---
title: "Errors with RMI in java?"
date: 2011-06-03
forum: Networking &amp; Wireless
---

### Post by LordDelta on 2011-06-03
Recently, I've been tasked with a bit of db stuff that uses a vpn and java client (I don't think I can talk too much about it). The java client runs fine over the ciscovpn connection on an xp machine, however my problem is running it on Linux: the application successfully connects to the server over vpn to download the application, however it then throws an error about RMI being unable to connect later, and to check if the RmiServer is running...

I don't know too much about the application, other than its made by UC4 (Intelligent Service Automation), however if the following stack trace is helpfull:

```
java.net.SocketException: Network is unreachable
	at java.net.PlainSocketImpl.socketConnect(Native Method)
	at java.net.PlainSocketImpl.doConnect(PlainSocketImpl.java:351)
	at java.net.PlainSocketImpl.connectToAddress(PlainSocketImpl.java:213)
	at java.net.PlainSocketImpl.connect(PlainSocketImpl.java:200)
	at java.net.SocksSocketImpl.connect(SocksSocketImpl.java:366)
	at java.net.Socket.connect(Socket.java:529)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.connect(SSLSocketImpl.java:559)
	at com.sun.net.ssl.internal.ssl.SSLSocketImpl.<init>(SSLSocketImpl.java:401)
	at com.sun.net.ssl.internal.ssl.SSLSocketFactoryImpl.createSocket(SSLSocketFactoryImpl.java:123)
	at com.appworx.client.screen.util.ClientSocketManager.A(ClientSocketManager.java:241)
	at com.appworx.client.screen.util.ClientSocketManager.connect(ClientSocketManager.java:307)
	at com.appworx.client.screen.util.Loader.setMaster(Loader.java:961)
	at com.appworx.client.screen.logon.C.&#335;(Logon.java:235)
	at com.appworx.client.screen.main.AxMain.A(AxMain.java:2505)
	at com.appworx.client.screen.main.AxMain.main(AxMain.java:3166)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.sun.javaws.Launcher.executeApplication(Launcher.java:1804)
	at com.sun.javaws.Launcher.executeMainClass(Launcher.java:1750)
	at com.sun.javaws.Launcher.doLaunchApp(Launcher.java:1512)
	at com.sun.javaws.Launcher.run(Launcher.java:130)
	at java.lang.Thread.run(Thread.java:662)
```

This is obviously a Network problem then (or it looks that way to me), and I seem to have found some vague mention rmi and iptables? If anyone knows a solution, or could perhaps point me in the correct direction to look for some debuging/network monitoring tools to attempt to see what its trying to do and failing, I would appreciate it.

Since it works find on Windows, but fails on Linux, its probably a configuration setting I don't know too much about.

I'm using Sun's JRE: (output of java -version)

```
java version "1.6.0_24"
Java(TM) SE Runtime Environment (build 1.6.0_24-b07)
Java HotSpot(TM) 64-Bit Server VM (build 19.1-b02, mixed mode)

```

Thanks.

---

### Post by opabecker on 2011-09-16
Did you ever find a solution to this?  UC4 did not work for me on Lucid (same error), but DID work for me on Maverick (albeit with a few small display problems with easy workarounds).  Now that I've "upgraded" to Natty, it doesn't work again.  Please let me know if you've heard anything.

Thanks!
Anthony
|----------------------------------------------------
| Anthony M. Becker - Database Administrator
| Oakland University - Rochester, MI - 248.370.2117
|----------------------------------------------------
| "This technicality is so technical that we need
|  a few more technicians in order to find a
|  technical answer."
|                     - Alexander Bessmertnych

|----------------------------------------------------

---

### Post by opabecker on 2011-09-21
I still can't run UC4 natively on Natty; however, I have two workarounds:

1) Use a Windows virtual machine and run it there.

2) Install Wine, copy a Windows JDK into that installation, and use its javaws to open the Client.jnlp file.

I hope this helps you.  If you find any other solutions, please let me know.

Anthony

---

