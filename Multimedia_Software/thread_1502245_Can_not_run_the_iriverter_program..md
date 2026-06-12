---
title: "Can not run the iriverter program."
date: 2010-06-05
forum: Multimedia Software
---

### Post by irv on 2010-06-05
I installed "iriverter" and would like to use it to convert some video files. I like it because it uses mencoder.
The problem is, after it installs it will not open. Here is the output running it from a terminal:
```
iriverter
Exception in thread "main" java.lang.NoClassDefFoundError: org/eclipse/swt/events/SelectionListener
	at java.lang.ClassLoader.defineClass1(Native Method)
	at java.lang.ClassLoader.defineClass(ClassLoader.java:634)
	at java.security.SecureClassLoader.defineClass(SecureClassLoader.java:142)
	at java.net.URLClassLoader.defineClass(URLClassLoader.java:277)
	at java.net.URLClassLoader.access$000(URLClassLoader.java:73)
	at java.net.URLClassLoader$1.run(URLClassLoader.java:212)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.events.SelectionListener
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
	... 12 more
Could not find the main class: org.thestaticvoid.iriverter.ConverterUI. Program will exit.

```

It appears to be a java issue. Is there something I need to install before it runs? or when this app was packaged did it omit something?
Thanks for the help ahead of time.

---

### Post by mh2ack on 2010-06-09
I had the same problem. I read and searched then tried going to their  website ([http://iriverter.thestaticvoid.com/](http://iriverter.thestaticvoid.com/)).  There is also a link to their website in the Ubuntu Software Center...   I uninstalled the version of Iriverter  from the Ubuntu Software Center and then clicked the link to install the  version 17.1 from their website and it works. Ubuntu needs to update  the version of Iriverter in the Software  center, or something. The problem probably has to do with that the  current version contains nonfree binary codecs. I suppose they would  need to do something similar to what they do for Adobe products.

Given what I was trying to do and following the lead of another thread I  installed Avidemux. So now I will see which I like better.

---

### Post by Jinger on 2010-06-09
It's a bug. It has been already signalised. Take a look at this page:[https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/535193]("https://bugs.launchpad.net/ubuntu/+source/iriverter/+bug/535193")

In order to solve this problem try downloading the .deb of this through GetDeb, that is presently down.

---

### Post by themegolith on 2013-03-11
The problem and solution are simple.

The issue is in the /usr/bin/iriverter script. It refers to
/usr/lib/java/swt-gtk-3.5.jar but the distro contains -3.5.1.jar

You can confirm part this information by opening /usr/lib/java in your file manager. 

Now we need to open /usr/bin/iriverter for editing. 

Since it’s a system file you need to open it with root access. I have kde-service-menu-rootactions from Sam Rog’s PPA installed on my system so I can simply right-click the file and select Root Actions > Open as Text from the context menu but you can also open it with gksudo kate /usr/bin/iriverter (substitute your preferred text editor for kate). 

$CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt-gtk-3.5.jar org.thestaticvoid.iriverter.ConverterUI $*

to

$CLASSPATH:${prefix}/share/java/iriverter.jar:/usr/lib/java/swt-gtk-3.5.1.jar org.thestaticvoid.iriverter.ConverterUI $*

Note: If you have a different version of java in /usr/bin/java/ the then one shown, then use the name of that version of java instead.

One you’ve made the edit save the file. Now you should be able to launch iriverter without problem

---

### Post by QIII on 2013-03-11
Thank you for sharing.

If a post is older than a year or so and hasn't had a new reply in that  time, instead of replying to it, create a new thread. In the software  world, a lot can change in a very short time, and doing things this way  makes it more likely that you will find the best information. You may  link to the original discussion in the new thread if you think it may be  helpful.

*Thread **closed.***

---

