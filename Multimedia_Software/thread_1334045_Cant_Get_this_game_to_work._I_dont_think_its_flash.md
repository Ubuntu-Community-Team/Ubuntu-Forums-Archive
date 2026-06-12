---
title: "Cant Get this game to work. I dont think its flash. Any ideas?"
date: 2009-11-22
forum: Multimedia Software
---

### Post by DeusExM1 on 2009-11-22
I am running opera 9.10 . i want to play a game here:

[http://www.nintendo8.com/game/678/spelunker/](http://www.nintendo8.com/game/678/spelunker/)

Youtube videos play fine. so then what is this? and why cant i play it ?

Edit: I can hear the sound and its crackling.

---

### Post by sanderj on 2009-11-22
Have you tried Firefox? Reason: on that page, my Firefox wants to install ... Java. So it's not flash-only.

---

### Post by Prodigal Son on 2009-11-22
It's Java.

```
sudo apt-get install sun-java6-jre sun-java6-plugin
```

---

### Post by DeusExM1 on 2009-11-22
firefox is one of the worst browsers out there imo. it opened pages slowly, and even youtube wouldnt work properly ! Which is why i got Opera.

I have installed the java plugin, but now i just see the game load to 100% but it doesnt start. Sometimes is blank like before. Any ideas>?

---

### Post by wojox on 2009-11-22
```

load: class AppletGui not found.
java.lang.ClassNotFoundException: AppletGui
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:152)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:252)
	at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:445)
	at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2880)
	at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1397)
	at java.lang.Thread.run(Thread.java:619)
Caused by: java.io.IOException: open HTTP connection failed:http://www.nintendo8.com/AppletGui.class
	at sun.plugin2.applet.Applet2ClassLoader.getBytes(Applet2ClassLoader.java:460)
	at sun.plugin2.applet.Applet2ClassLoader.access$000(Applet2ClassLoader.java:46)
	at sun.plugin2.applet.Applet2ClassLoader$1.run(Applet2ClassLoader.java:126)
	at java.security.AccessController.doPrivileged(Native Method)
	at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:123)
	... 6 more
Exception: java.lang.ClassNotFoundException: AppletGui


```

Definitely Java. I have Firefox-3.5.5 with Java(TM) Plug-in 1.6.0_15 in plugins and I can play it.

---

### Post by UNME on 2009-11-22
[@wojox] are you able to play flash + youtube with sound with firefox

---

### Post by wojox on 2009-11-22
Hell ya

---

### Post by UNME on 2009-11-22
[@wojox] I am not .. did some tweak?
I am able to play video but not sounds esp.for youtube.

---

### Post by sanderj on 2009-11-22
With Firefox on Ubuntu 9.10 i386 everything seems to work OK after accepting the offered java-plugin and restarting Firefox. See screenshot.


And yes, I've got sound ... and what an annoying sound that is: 25 years old 8-bit tunes ... a bit like the ZX Spectrum times ... ;-)

---

### Post by DeusExM1 on 2009-11-22
Ok i understand it is java now. When i had firefox it would load youtube videos with sound. But i couldnt move the slider on the bottom to skip some of the video. (it would work literally like 1/10 times to the point where i had to keep clicking like insane).

So any ideas how to make opera play nicely with java guys?

---

### Post by DeusExM1 on 2009-11-25
bump =]

---

