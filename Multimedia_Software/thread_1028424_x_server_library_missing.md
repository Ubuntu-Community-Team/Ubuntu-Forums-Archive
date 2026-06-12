---
title: "x server library missing"
date: 2009-01-02
forum: Multimedia Software
---

### Post by bitdoger on 2009-01-02
help neebie needs a x library?... even though i have 8.04 running
this program needs...
root@david-desktop:/home/david/tos# ./thinkorswim_installer.sh
Starting Installer ...
Could not display the GUI. This application needs access to an X Server.
If you have access there is probably an X library missing.
*******************************************************************
You can also run this application in console mode without
access to an X server by passing the argument -c
*******************************************************************
An error occurred:
java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
Error log: /tmp/install4jError32984.log
root@david-desktop:/home/david/tos# ls
mytry  mytry~  thinkorswim  thinkorswim_installer.sh
root@david-desktop:/home/david/tos# cd /tmp
root@david-desktop:/tmp# dir
gconfd-david		 orbit-david	  Tracker-david.5658
hsperfdata_root		 pulse-david	  virtual-david.OwRebU
install4jError32984.log  seahorse-mPR5c2
keyring-FPSbhK		 tmp.XkApyO5252
Exception:

java.awt.HeadlessException: 
No X11 DISPLAY variable was set, but this program performed an operation which requires it.
	at java.awt.GraphicsEnvironment.checkHeadless(GraphicsEnvironment.java:159)
	at java.awt.Button.<init>(Button.java:135)
	at java.awt.Button.<init>(Button.java:122)
	at com.install4j.runtime.installer.frontend.WizardScreenExecutor$2.run(Unknown Source)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:199)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:273)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:183)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:173)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:168)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:160)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:121)

System properties:

java.runtime.name=Java(TM) SE Runtime Environment
exe4j.moduleName=/home/david/tos/thinkorswim_installer.sh
sun.boot.library.path=/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386
java.vm.version=10.0-b23
java.vm.vendor=Sun Microsystems Inc.
java.vendor.url=http://java.sun.com/
path.separator=:
java.vm.name=Java HotSpot(TM) Client VM
file.encoding.pkg=sun.io
sun.java.launcher=SUN_STANDARD
user.country=US
sun.os.patch.level=unknown
install4j.exeDir=/home/david/tos/
java.vm.specification.name=Java Virtual Machine Specification
user.dir=/home/david/tos/thinkorswim_installer.sh.5834.dir
java.runtime.version=1.6.0_07-b06
java.awt.graphicsenv=sun.awt.X11GraphicsEnvironment
java.endorsed.dirs=/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/endorsed
os.arch=i386
java.io.tmpdir=/tmp
line.separator=

java.vm.specification.vendor=Sun Microsystems Inc.
os.name=Linux
exe4j.totalDataLength=756744
sun.java2d.noddraw=true
sun.jnu.encoding=UTF-8
java.library.path=/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386/client:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/i386:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/../lib/i386:/usr/java/packages/lib/i386:/lib:/usr/lib
java.specification.name=Java Platform API Specification
java.class.version=50.0
sun.management.compiler=HotSpot Client Compiler
os.version=2.6.24-22-generic
user.home=/root
user.timezone=US/Eastern
java.awt.printerjob=sun.print.PSPrinterJob
install4j.jvmDir=/usr
file.encoding=UTF-8
java.specification.version=1.6
java.class.path=i4jruntime.jar:user.jar
user.name=root
java.vm.specification.version=1.0
java.home=/usr/lib/jvm/java-6-sun-1.6.0.07/jre
sun.arch.data.model=32
user.language=en
java.specification.vendor=Sun Microsystems Inc.
java.vm.info=mixed mode, sharing
java.version=1.6.0_07
java.ext.dirs=/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/ext:/usr/java/packages/lib/ext
sun.boot.class.path=/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/resources.jar:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/rt.jar:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/sunrsasign.jar:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/jsse.jar:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/jce.jar:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/lib/charsets.jar:/usr/lib/jvm/java-6-sun-1.6.0.07/jre/classes
install4j.appDir=/home/david/tos/
java.vendor=Sun Microsystems Inc.
file.separator=/
java.vendor.url.bug=http://java.sun.com/cgi-bin/bugreport.cgi
sun.io.unicode.encoding=UnicodeLittle
sun.cpu.endian=little
sun.cpu.isalist=

---

### Post by ChanServ on 2009-01-02
have you tried running ./thinkorswim_installer.sh -c  ?

---

### Post by bitdoger on 2009-01-02
i still need the x library to run the program after it install anyway

---

### Post by crunchfighter on 2009-02-12
Have you tried uninstalling java and then reinstalling it?

---

