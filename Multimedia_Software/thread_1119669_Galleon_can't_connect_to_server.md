---
title: "Galleon can't connect to server"
date: 2009-04-08
forum: Multimedia Software
---

### Post by ktmom on 2009-04-08
I realize there are several posts on this subject.  After three days of trying to resolve my problems, and searching and reading through posts on multiple related forums, I have gotten nowhere. Any help I can get would be appreciated.  I am a newb, and know only enough to be very dangerous ;)

I am running Ubuntu 8.10.  I have a TiVo Humax series 2.  Both are networked.  I am assuming that the Galleon GUI is griping that it can not connect to the Galleon server.  

FWIW:I am running a web development setup with Apache2, php and MySQL on this system but I don't see how that could affect this problem.

I have:
[LIST=1]
[*]updated the etc/hosts file with a line including my home network IP address and computer name.
[*]tried Java 1.6 (install for another app)
[*]pointed Java to use 1.5 and restarted, then uninstalled and reinstalled Galleon
[*]I have not turned off IPv 6, because for the life of me I can not figure out how to.
[/LIST]

The following is what prints in the terminal when I enter java at the cli;
```
Usage: java [-options] class [args...]
           (to execute a class)
   or  java [-options] -jar jarfile [args...]
           (to execute a jar file)

where options include:
    -d32          use a 32-bit data model if available

    -d64          use a 64-bit data model if available
    -client	  to select the "client" VM
    -server	  to select the "server" VM
    -hotspot	  is a synonym for the "client" VM  [deprecated]
                  The default VM is client.
                  
    -cp <class search path of directories and zip/jar files>
    -classpath <class search path of directories and zip/jar files>
                  A : separated list of directories, JAR archives,
                  and ZIP archives to search for class files.
    -D<name>=<value>
                  set a system property
    -verbose[:class|gc|jni]
                  enable verbose output
    -version      print product version and exit
    -version:<value>
                  require the specified version to run
    -showversion  print product version and continue
    -jre-restrict-search | -jre-no-restrict-search
                  include/exclude user private JREs in the version search
    -? -help      print this help message
    -X            print help on non-standard options
    -ea[:<packagename>...|:<classname>]
    -enableassertions[:<packagename>...|:<classname>]
                  enable assertions
    -da[:<packagename>...|:<classname>]
    -disableassertions[:<packagename>...|:<classname>]
                  disable assertions
    -esa | -enablesystemassertions
                  enable system assertions
    -dsa | -disablesystemassertions
                  disable system assertions
    -agentlib:<libname>[=<options>]
                  load native agent library <libname>, e.g. -agentlib:hprof
                    see also, -agentlib:jdwp=help and -agentlib:hprof=help
    -agentpath:<pathname>[=<options>]
                  load native agent library by full pathname
    -javaagent:<jarpath>[=<options>]
                  load Java programming language agent, see java.lang.instrument

```

when I type: java - version, right now this is what I get;
```
java version "1.5.0_16"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_16-b02)
Java HotSpot(TM) Client VM (build 1.5.0_16-b02, mixed mode, sharing)

```

This is what prints in the terminal when I launch Galleon gui, I have tried as sudo and not.  
```
elizabeth@Dell8400:/usr/share/galleon/bin$ sudo ./galleon start
Starting Galleon TiVo Application Server...
elizabeth@Dell8400:/usr/share/galleon/bin$ sudo ./gui.sh
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb15ce7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb15ce891]
#2 /usr/lib/libX11.so.6(_XReply+0x254) [0xb1616494]
#3 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0xb1710dce]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0xb16fad77]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0xb16faef3]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb16fb136]
#7 [0xb26c9c1b]
#8 [0xb26c3b3b]
#9 [0xb26c3b3b]
#10 [0xb26c1219]
#11 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so [0xb786a2ec]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so [0xb797ef08]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so [0xb786a11f]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb78c7bcd]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb766030d]
#16 [0xb26c94bb]
#17 [0xb26c3a64]
#18 [0xb26c1219]
#19 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so [0xb786a2ec]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb15ce7c7]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb15ce96e]
#2 /usr/lib/libX11.so.6 [0xb1615619]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb160b666]
#4 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0xb16fa0b9]
#5 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0xb16fa303]
#6 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so [0xb16fafa1]
#7 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x26) [0xb16fb136]
#8 [0xb26c9c1b]
#9 [0xb26c3b3b]
#10 [0xb26c3b3b]
#11 [0xb26c1219]
#12 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so [0xb786a2ec]
#13 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so [0xb797ef08]
#14 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so [0xb786a11f]
#15 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x32d) [0xb78c7bcd]
#16 /usr/lib/jvm/java-1.5.0-sun-1.5.0.16/jre/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb766030d]
#17 [0xb26c94bb]
#18 [0xb26c3a64]
#19 [0xb26c1219]
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at org.lnicholls.galleon.gui.MainFrame$ServerDialog.<init>(MainFrame.java:774)
	at org.lnicholls.galleon.gui.MainFrame$ServerDialog.<init>(MainFrame.java:754)
	at org.lnicholls.galleon.gui.MainFrame$2.actionPerformed(MainFrame.java:133)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1849)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2169)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:420)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:258)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:302)
	at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1051)
	at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1092)
	at java.awt.AWTEventMulticaster.mouseReleased(AWTEventMulticaster.java:231)
	at java.awt.Component.processMouseEvent(Component.java:5517)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3135)
	at java.awt.Component.processEvent(Component.java:5282)
	at java.awt.Container.processEvent(Container.java:1966)
	at java.awt.Component.dispatchEventImpl(Component.java:3984)
	at java.awt.Container.dispatchEventImpl(Container.java:2024)
	at java.awt.Component.dispatchEvent(Component.java:3819)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4212)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3892)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3822)
	at java.awt.Container.dispatchEventImpl(Container.java:2010)
	at java.awt.Window.dispatchEventImpl(Window.java:1791)
	at java.awt.Component.dispatchEvent(Component.java:3819)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:463)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:242)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:163)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:157)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:149)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:110)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at org.lnicholls.galleon.gui.MainFrame$AddAppDialog.<init>(MainFrame.java:568)
	at org.lnicholls.galleon.gui.MainFrame$AddAppDialog.<init>(MainFrame.java:503)
	at org.lnicholls.galleon.gui.MainFrame$1.actionPerformed(MainFrame.java:125)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1849)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2169)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:420)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:258)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:302)
	at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1051)
	at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1092)
	at java.awt.AWTEventMulticaster.mouseReleased(AWTEventMulticaster.java:231)
	at java.awt.Component.processMouseEvent(Component.java:5517)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3135)
	at java.awt.Component.processEvent(Component.java:5282)
	at java.awt.Container.processEvent(Container.java:1966)
	at java.awt.Component.dispatchEventImpl(Component.java:3984)
	at java.awt.Container.dispatchEventImpl(Container.java:2024)
	at java.awt.Component.dispatchEvent(Component.java:3819)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4212)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3892)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3822)
	at java.awt.Container.dispatchEventImpl(Container.java:2010)
	at java.awt.Window.dispatchEventImpl(Window.java:1791)
	at java.awt.Component.dispatchEvent(Component.java:3819)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:463)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:242)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:163)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:157)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:149)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:110)
Exception in thread "AWT-EventQueue-0" java.lang.NullPointerException
	at org.lnicholls.galleon.gui.RulesPanel.<init>(RulesPanel.java:160)
	at org.lnicholls.galleon.gui.ToGoDialog.<init>(ToGoDialog.java:76)
	at org.lnicholls.galleon.gui.MainFrame$6.actionPerformed(MainFrame.java:170)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1849)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2169)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:420)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:258)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:302)
	at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1051)
	at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1092)
	at java.awt.AWTEventMulticaster.mouseReleased(AWTEventMulticaster.java:231)
	at java.awt.Component.processMouseEvent(Component.java:5517)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3135)
	at java.awt.Component.processEvent(Component.java:5282)
	at java.awt.Container.processEvent(Container.java:1966)
	at java.awt.Component.dispatchEventImpl(Component.java:3984)
	at java.awt.Container.dispatchEventImpl(Container.java:2024)
	at java.awt.Component.dispatchEvent(Component.java:3819)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4212)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3892)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3822)
	at java.awt.Container.dispatchEventImpl(Container.java:2010)
	at java.awt.Window.dispatchEventImpl(Window.java:1791)
	at java.awt.Component.dispatchEvent(Component.java:3819)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:463)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:242)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:163)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:157)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:149)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:110)

```

---

