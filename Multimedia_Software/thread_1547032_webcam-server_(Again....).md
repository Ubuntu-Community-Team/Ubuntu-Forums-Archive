---
title: "webcam-server (Again....)"
date: 2010-08-06
forum: Multimedia Software
---

### Post by hanslammerts on 2010-08-06
Hi,

Just downloaded and installed the Ubuntu package webcam-server.
The problem is that I can´t get it to work. All I get is a black rectangle with the text: Connecting, please wait, and a red dot just below that text.
(This is when trying to reach the webcam page over the internet, local is not possible since it is a server, not a desktop installation)

Of course I´ve been Googling around a bit and found several posts, but none of them had the solution.

I´m running Ubuntu 10.04 server (so no GUI stuff available), the webcam is an old Philips PCVC740K.
If I use streamer to capture an image then I get a perfect picture, so my camera is working.

Webcam-server is running on port 8888 (and yes, I have opened this port in my router to the outside world, although I´m not really sure this is necessary).
There is no firewall running on the server (for now, during testphase).

I have tried entering the localIP of the server in the webcam.html page. No luck.
I have tried entering my FQDN in the webcam.htmlpage. No luck either.
When I open the page, the webcam-server logfile does not show any connection from remote.
There´s also different behaviour in different browsers.
Opening the webcam page with FF, I get a rectangle with a red cross, and in the statusbar the text Loading Java Applet failed.
The java console in FF says:

Java(TM) Plug-in 1.5.0
Using JRE version 1.5.0 IBM J9 VM
User home directory = C:\Documents and Settings\Administrator
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
p:   reload proxy configuration
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------
load: class WebCamApplet.class not found.
java.lang.ClassNotFoundException: WebCamApplet.class
    at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:200)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:602)
    at sun.applet.AppletClassLoader.loadClass(AppletClassLoader.java:151)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:568)
    at sun.applet.AppletClassLoader.loadCode(AppletClassLoader.java:618)
    at sun.applet.AppletPanel.createApplet(AppletPanel.java:776)
    at sun.plugin.AppletViewer.createApplet(AppletViewer.java:1765)
    at sun.applet.AppletPanel.runLoader(AppletPanel.java:705)
    at sun.applet.AppletPanel.run(AppletPanel.java:368)
    at java.lang.Thread.run(Thread.java:803)
Caused by: java.io.IOException: open HTTP connection failed.
    at sun.applet.AppletClassLoader.getBytes(AppletClassLoader.java:303)
    at sun.applet.AppletClassLoader.access$100(AppletClassLoader.java:76)
    at sun.applet.AppletClassLoader$1.run(AppletClassLoader.java:190)
    at java.security.AccessController.doPrivileged(AccessController.java:275)
    at sun.applet.AppletClassLoader.findClass(AppletClassLoader.java:187)
    ... 9 more


When opening the same page with IE8, I get the beforementioned black rectangle, and the Java console shows something I cannot explain either:

Java Plug-in 1.6.0_13
Using JRE version 1.6.0_13 Java HotSpot(TM) Client VM
User home directory = C:\Documents and Settings\Administrator
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


Loaded image: [https://hanslammerts.mine.nu/init.jpg](https://hanslammerts.mine.nu/init.jpg)
Exception in thread "Thread-11" java.security.AccessControlException: access denied (java.net.SocketPermission 192.168.2.99:8888 connect,resolve)
    at java.security.AccessControlContext.checkPermission(Unknown Source)
    at java.security.AccessController.checkPermission(Unknown Source)
    at java.lang.SecurityManager.checkPermission(Unknown Source)
    at java.lang.SecurityManager.checkConnect(Unknown Source)
    at sun.plugin2.applet.Applet2SecurityManager.checkConnect(Unknown Source)
    at java.net.Socket.connect(Unknown Source)
    at java.net.Socket.connect(Unknown Source)
    at java.net.Socket.<init>(Unknown Source)
    at java.net.Socket.<init>(Unknown Source)
    at ImageDownloader.connect(ImageDownloader.java:54)
    at ImageDownloader.run(ImageDownloader.java:71)

It looks like there is a security problem somewhere, but I cannot put my finger on the exact problem.

Any suggestions would be most welcome.
If anyone knows of any other webcam streaming software (apart fromt he obvious Zoneminder and Motion) that can run on a server without X, I´l be most interested as well.

Thanks,

Hans

P.S. 
One more potential important piece of information:
I have rigged my apache2 config in such away that connections over HTTP are automatically redirected to HTTPS.

---

### Post by hanslammerts on 2010-08-07
Bump ?

---

### Post by hanslammerts on 2010-08-09
Really, no-one ?

---

### Post by enmacc on 2011-09-12
i have the same problem, with ubuntu server Ubuntu 10.04.3 LTS.... for consolation..

---

