// ShareNet Flutter App - Minimal Functional Code

import 'package:flutter/material.dart'; import 'package:shared_preferences/shared_preferences.dart'; import 'package:local_auth/local_auth.dart';

void main() => runApp(ShareNetApp());

class ShareNetApp extends StatelessWidget { @override Widget build(BuildContext context) { return MaterialApp( title: 'ShareNet', theme: ThemeData(primarySwatch: Colors.blue), home: LockScreen(), debugShowCheckedModeBanner: false, ); } }

class LockScreen extends StatefulWidget { @override _LockScreenState createState() => _LockScreenState(); }

class _LockScreenState extends State<LockScreen> { final _localAuth = LocalAuthentication(); final _pinController = TextEditingController();

@override void initState() { super.initState(); _checkForBiometrics(); }

void _checkForBiometrics() async { bool canCheck = await _localAuth.canCheckBiometrics; if (canCheck) { bool authenticated = await _localAuth.authenticate( localizedReason: 'Please authenticate to access ShareNet', options: AuthenticationOptions(biometricOnly: true), ); if (authenticated) _navigate


