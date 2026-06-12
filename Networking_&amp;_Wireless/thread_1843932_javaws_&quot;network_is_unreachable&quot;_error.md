---
title: "javaws &quot;network is unreachable&quot; error"
date: 2011-09-14
forum: Networking &amp; Wireless
---

### Post by opabecker on 2011-09-14
I am having trouble launching an application called UC4 Applications Manager.  This application is launched using Java Web Start.  I am currently using Sun JDK 1.6.0_26 on Natty.  The application worked without error on Maverick, and works without error on a Windows 7 guest vm, but gave the same error when I had tried to run it on Hardy in the past.  I had not needed to make any configuration changes on Maverick to make the app work - it worked out of the box.

The error message I am currently getting is:

java.net.SocketException: Das Netzwerk ist nicht erreichbar
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
	at com.appworx.client.screen.util.Loader.setMaster(Loader.java:941)
	at com.appworx.client.screen.logon.C.Þ(Logon.java:228)
	at com.appworx.client.screen.main.AxMain.A(AxMain.java:2209)
	at com.appworx.client.screen.main.AxMain.main(AxMain.java:2849)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.sun.javaws.Launcher.executeApplication(Launcher.java:1809)
	at com.sun.javaws.Launcher.executeMainClass(Launcher.java:1750)
	at com.sun.javaws.Launcher.doLaunchApp(Launcher.java:1512)
	at com.sun.javaws.Launcher.run(Launcher.java:130)
	at java.lang.Thread.run(Thread.java:662)

English translation of error message: "The network is unreachable."

I've already tried suggestions to use sysctl to disable IPv6 networking, and to set deployment.javaws.jre.0.args=-Djava.net.preferIPv4Stack\=true in my deployment.properties file, to no avail.

I've tried the demos at [http://java.sun.com/javase/technologies/desktop/javawebstart/demos.html](http://java.sun.com/javase/technologies/desktop/javawebstart/demos.html), and they all work for me - no problems.

I don't know what could have changed between Maverick and Natty that this application would break, nor what could have changed between Hardy and Maverick that the application would have started working.

I'd appreciate any assistance.

Thanks!
Anthony M. Becker - Database Administrator
Oakland University - Rochester, MI - 248.370.2117
---------------------------------------------------
"All my life, I always wanted to be somebody.
Now I see that I should have been more specific."
   *-Jane Wagner
---------------------------------------------------

---

### Post by opabecker on 2011-09-14
I should also mention that the UC4 app did not work on Lucid.  In short, something about Maverick fixed the problem, and something about Natty broke it again.

Thanks!
Anthony M. Becker - Database Adminstrator
Oakland University - Rochester, MI - phone 248.370.2117
---------------------------------------------------------
"Ein Anfang ist immer schrecklich! Madame Plissee sprach
schon von 'Anfang terrible'."
     -Heinz Erhardt
---------------------------------------------------------

---

### Post by opabecker on 2011-09-21
BUMP.

I am currently working around this in two different but effective ways:

1) I can run the application in a Windows virtual machine.
2) I copied a Windows JDK into my Wine installation (since I couldn't install it) and saved the jnlp files from the UC4 application in my Wine installation as well.  I set up a menu selection to use the Windows javaws to open the jnlp files, and this successfully runs the application without me needing the virtual machine.

All the same, I would much rather be able to simply click on the link on my web page and have it work using Linux's own javaws.

---

