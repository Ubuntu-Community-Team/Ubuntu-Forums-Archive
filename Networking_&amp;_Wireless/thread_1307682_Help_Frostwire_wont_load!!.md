---
title: "Help Frostwire wont load!!"
date: 2009-10-31
forum: Networking &amp; Wireless
---

### Post by xenosaga456 on 2009-10-31
ya i need help with frostwire every time i load it up it gives me this

```
FrostWire version 4.18.3
Java version 1.6.0_0 from Sun Microsystems Inc.
Linux v. 2.6.28-16-generic on i386
Free/total memory: 45778088/78970880

FATAL ERROR!

java.lang.NoClassDefFoundError: com/ibm/icu/text/Normalizer
at org.limewire.util.I18NConvertICU.convert(Unknown Source)
at org.limewire.util.I18NConvertICU.getNorm(Unknown Source)
at org.limewire.util.I18NConvert.<init>(Unknown Source)
at org.limewire.util.I18NConvert.<clinit>(Unknown Source)
at com.limegroup.gnutella.gui.Initializer.loadLateTas ksForUI(Unknown Source)
at com.limegroup.gnutella.gui.Initializer.initialize( Unknown Source)
at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ e Method)
at sun.reflect.NativeMethodAccessorImpl.invoke(Native MethodAccessorImpl.java:57)
at sun.reflect.DelegatingMethodAccessorImpl.invoke(De legatingMethodAccessorImpl.java:43)
at java.lang.reflect.Method.invoke(Method.java:616)
at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: com.ibm.icu.text.Normalizer
at java.net.URLClassLoader$1.run(URLClassLoader.java: 217)
at java.security.AccessController.doPrivileged(Native Method)
at java.net.URLClassLoader.findClass(URLClassLoader.j ava:205)
at java.lang.ClassLoader.loadClass(ClassLoader.java:3 23)
at sun.misc.Launcher$AppClassLoader.loadClass(Launche r.java:294)
at java.lang.ClassLoader.loadClass(ClassLoader.java:2 6
at java.lang.ClassLoader.loadClassInternal(ClassLoade r.java:336)
... 12 more


-- listing session information --
Current thread: main
Active Threads: 16
Peak Number of Thread: 22
System Load Avg: 1.98
Objects Pending GC: 0
Free Space In Settings: 39583592448
Free Space In Incomplete: 39583592448
Free Space In Downloads: 39583592448
Heap Memory Usage: init = 49551744(48390K) used = 33354440(32572K) committed = 78970880(77120K) max = 765394944(747456K)
Non-Heap Memory Usage: init = 19136512(18688K) used = 29977744(29275K) committed = 30932992(30208K) max = 184549376(180224K)

-- listing threads --
Timer-0: 1
CreationTimeCacheDeserializer: 1
AWT-Shutdown: 1
Timer-1: 1
HostileUpdater Worker: 1
Deadlock Detection Thread: 1
AWT-XAWT: 1
User event dispatch thread: 1
DelayedGUI: 1
main: 1
Thread-5: 1
Thread-3: 1
AWT-EventQueue-0: 1
NIODispatcher: 1
Image Fetcher 2: 1
Image Fetcher 3: 1


-- listing properties --
EXTENSIONS_MIGRATE=false
LAST_EXPIRE_TIME=1256076297396
INTRO_NETWORK_LINK=http://bit.ly/1gkmbo
COUNTRY=
INTRO_URL=file:///home/user/.frostwire4.18/ove...
INTRO_TORRENT_LINK=http://www.frostclick.com/torrents/au...
INTRO_LOCAL_LINK=http://bit.ly/1gkmbo
CLIENT_ID=DD20BCC464094A883E039BAF7184FD00
CHAT_IRC_NICK=
AFTER_SEARCH_URL=file:///home/user/.frostwire4.18/ove...
AFTER_SEARCH_LOCAL_LINK=http://www.frostwire.com/downloads
PORT=38964
EXTENSIONS_TO_SEARCH_FOR=
INSTALLED=true
MAX_SIM_DOWNLOAD=12
AFTER_SEARCH_NETWORK_LINK=http://www.frostwire.com/downloads
EXTENSIONS_LIST_UNSHARED=m4a;mpg;tif;mpe;rmvp;ogm; cue;swf;shn;...
WINDOW_Y=150
CONNECTION_SPEED=1000
WINDOW_X=208


**************** Comments from the user ****************
null

```


if you can help me i would love u forever

---

### Post by DimitrisC on 2009-11-01
I get the exact same thing on Ubuntu 9.10 64-bit. Hope someone can help. Thanks.

---

### Post by xenosaga456 on 2009-11-02
well if u find out anything can u let me know:D

---

### Post by DimitrisC on 2009-11-02
Well someone found a workaround to this problem. I just tried it and it works! 
Go to [www.frostwire.com](www.frostwire.com) and download the tarball file (not the .deb package). Then completely remove any previous frostwire installations and delete the /usr/lib/frostwire directory if any. Extract the tarball somewhere and rename the extracted directory to frostwire. Then move that directory to /usr/lib/. In order to  start frostwire just create an entry to gnome menu and point it to "/usr/lib/frostwire/./runFrostwire.sh" (without quotes). Hope this helps :-). Let me know if it worked for you.

---

### Post by xenosaga456 on 2009-11-03
hey i fixed it

i went to synaptic package manager and set frostwire for compleat removal


then i restarted my computer and went in to the recovery mode


then i fixed broken packages and continued with the boot 


i reinstalled it and yayayayaya it worked

---

### Post by DimitrisC on 2009-11-04
Cool :-) It seems there is more than 1 way to fixing this! :-) Good to know.

Edit: You should mark this thread as solved so anyone else experiencing this problem can see here for the solution.

---

### Post by barrieluv on 2009-11-06
Good stuff!  Many thanks! :)

---

### Post by xenosaga456 on 2009-11-11
ya this may sound stupid but i cant figure out how to set this thread as SOLVED?

---

