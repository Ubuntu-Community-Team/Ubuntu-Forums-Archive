---
title: "Java Web Start (Sun Java 6) problems"
date: 2008-10-24
forum: Multimedia Software
---

### Post by JFDR on 2008-10-24
Hi !

I had previously installed
[http://www.gokgs.com/download.xhtml](http://www.gokgs.com/download.xhtml)
(an applet for playing the board game GO online)

using Java Web Start

and it was working fine for a while

I just went to play, and got a java error message.

Using Synaptic package manager, I reinstalled everything that came up under a search for Sun Java.

But I kept getting the same error

java.lang.IllegalStateException: DynamicProxyManager: Invalid Proxy Type


Here is the full error msg. I get when trying to reinstall the program using Java Web Start
:

java.lang.IllegalStateException: DynamicProxyManager: Invalid Proxy Type
	at com.sun.deploy.net.proxy.DynamicProxyManager.reset(DynamicProxyManager.java:318)
	at com.sun.deploy.net.proxy.DeployProxySelector.reset(DeployProxySelector.java:62)
	at com.sun.javaws.Main.initializeExecutionEnvironment(Main.java:984)
	at com.sun.javaws.Main.continueInSecureThread(Main.java:170)
	at com.sun.javaws.Main$1.run(Main.java:107)
	at java.lang.Thread.run(Thread.java:619)


Any ideas?

Thanks

---

### Post by JFDR on 2008-10-25
posted at General Help
as that may be better

[http://ubuntuforums.org/showthread.php?p=6033971#post6033971](http://ubuntuforums.org/showthread.php?p=6033971#post6033971)

---

