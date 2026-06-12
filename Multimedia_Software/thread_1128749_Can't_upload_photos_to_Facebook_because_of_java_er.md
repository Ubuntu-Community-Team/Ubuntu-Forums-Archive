---
title: "Can't upload photos to Facebook because of java error"
date: 2009-04-17
forum: Multimedia Software
---

### Post by VotaVader on 2009-04-17
Hi! I'm trying to upload photos into a Facebook album, and in the screen where the Java applet is supposed to appear to let me upload them in bulk (there's too many of them to upload one by one), there appears an error: "Error: Click for details"
I did, and I get the Java Console, which reads like this:
```
Java Plug-in 1.6.0_10
Using JRE version 1.6.0_10 Java HotSpot(TM) Client VM
User home directory = /home/pedro




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

Facebook Photo Uploader 5 version: 5.5.8.0
Current document URL: http://www.facebook.com/profile.php?id=701457489&ref=profile
java.lang.ExceptionInInitializerError
	at com.aurigma.imageuploader.ImageUploader.init(Unknown Source)
	at sun.applet.AppletPanel.run(AppletPanel.java:424)
	at java.lang.Thread.run(Thread.java:619)
Caused by: java.security.AccessControlException: access denied (java.util.PropertyPermission java.io.tmpdir read)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:323)
	at java.security.AccessController.checkPermission(AccessController.java:546)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:532)
	at java.lang.SecurityManager.checkPropertyAccess(SecurityManager.java:1285)
	at java.lang.System.getProperty(System.java:652)
	at com.aurigma.imageuploader.tools.x.<clinit>(Unknown Source)
	... 3 more
Exception in thread "AWT-EventQueue-2" java.lang.IllegalThreadStateException: forbid thread creation in disposed TG
	at sun.plugin.security.ActivatorSecurityManager.checkAccess(ActivatorSecurityManager.java:155)
	at java.lang.ThreadGroup.checkAccess(ThreadGroup.java:288)
	at java.lang.Thread.init(Thread.java:332)
	at java.lang.Thread.<init>(Thread.java:433)
	at java.awt.EventDispatchThread.<init>(EventDispatchThread.java:58)
	at java.awt.EventQueue$1.run(EventQueue.java:822)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.EventQueue.initDispatchThread(EventQueue.java:819)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:153)
Facebook Photo Uploader 5 version: 5.5.8.0
Current document URL: http://www.facebook.com/editalbum.php?aid=73131&add=1
java.lang.NoClassDefFoundError: Could not initialize class com.aurigma.imageuploader.tools.x
	at com.aurigma.imageuploader.ImageUploader.init(Unknown Source)
	at sun.applet.AppletPanel.run(AppletPanel.java:424)
	at java.lang.Thread.run(Thread.java:619)
Exception in thread "AWT-EventQueue-3" java.lang.IllegalThreadStateException: forbid thread creation in disposed TG
	at sun.plugin.security.ActivatorSecurityManager.checkAccess(ActivatorSecurityManager.java:155)
	at java.lang.ThreadGroup.checkAccess(ThreadGroup.java:288)
	at java.lang.Thread.init(Thread.java:332)
	at java.lang.Thread.<init>(Thread.java:433)
	at java.awt.EventDispatchThread.<init>(EventDispatchThread.java:58)
	at java.awt.EventQueue$1.run(EventQueue.java:822)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.awt.EventQueue.initDispatchThread(EventQueue.java:819)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:153)
Facebook Photo Uploader 5 version: 5.5.8.0
Current document URL: http://www.facebook.com/editalbum.php?aid=73131&add=1
java.lang.NoClassDefFoundError: Could not initialize class com.aurigma.imageuploader.tools.x
	at com.aurigma.imageuploader.ImageUploader.init(Unknown Source)
	at sun.applet.AppletPanel.run(AppletPanel.java:424)
	at java.lang.Thread.run(Thread.java:619)
Facebook Photo Uploader 5 version: 5.5.8.0
Current document URL: http://www.facebook.com/editalbum.php?aid=73131&add=1
java.lang.NoClassDefFoundError: Could not initialize class com.aurigma.imageuploader.tools.x
	at com.aurigma.imageuploader.ImageUploader.init(Unknown Source)
	at sun.applet.AppletPanel.run(AppletPanel.java:424)
	at java.lang.Thread.run(Thread.java:619)
```

Now, I waited a couple of days just in case it was a problem with the server, but I still have the problem... I'm guessing it has something to do with the Java plugins in my computer (they might have screwed up when I was trying to fix the Flash plugin), or maybe ActiveX. Has anyone had this problem, or can better interpret these console results and tell me what to do about it?
It'd be much appreciated, thanks.

---

### Post by VotaVader on 2009-04-21
Bump! Please help me with this one... At least what java plugins do I have to reinstall that have to do with firefox?

---

### Post by dmm1983 on 2009-04-21
theres an option at the bottom use the simple upload tool works i use it. a lot even when i use a windoze box.

---

### Post by zsugiart on 2009-06-02
hey, bump into this problem too. 

@dmm1983: that doesn't help at all, he just say that there's too much photos to upload, the simpler uploader is plain slow and there's no reason as to why applet shouldn't work in Firefox/Ubuntu. 

btw, I tried loading a normal applet
[http://merganser.math.gvsu.edu/david/reed03/java/schottky/zoom.html](http://merganser.math.gvsu.edu/david/reed03/java/schottky/zoom.html)

seems to work fine. Yet my windows friends can load the facebook photoloader applet fine. Anyone?

---

### Post by VotaVader on 2009-06-02
I managed to fix the problem a while ago by reverting to the Java 5.0 plugin. There seemed to be a problem with my Java 6 plugin I guess. I still have both control panels for some reason (even though I completely removed version 6), but now it works. Also, the applications that need Java 6 also still work. It's very strange, but it seems when I installed the Java 5 plugin, whatever files were giving trouble were either fixed, changed, or removed.
I know this isn't a very professional solution, but I hope it helps. Before doing this, I tried various other browsers and KDE, but to no avail, so I'm pretty sure it was a problem with the plugin, and reinstalling it didn't fix it.

---

### Post by Arup on 2009-06-02
Sun Java 1.6_13 works fine with Opera 9.64 under Jaunty x64. I have uploaded huge amount of pics with no issues.

---

### Post by VotaVader on 2009-06-03
> **Arup said:**
> Sun Java 1.6_13 works fine with Opera 9.64 under Jaunty x64. I have uploaded huge amount of pics with no issues.

Yes, I'm not saying that there's something wrong with the OS or that there is an incompatibility with that Java plugin, it was just that I had that particular problem for some unknown reason. If it was a big incompatibility problem, the forum would be full of threads about it.

---

