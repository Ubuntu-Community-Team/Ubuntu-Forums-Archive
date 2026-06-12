---
title: "tnv on ubuntu 8.10"
date: 2009-02-27
forum: Networking &amp; Wireless
---

### Post by ntimperio on 2009-02-27
Anyone using tnv on ubuntu 8.10?  I downloaded, extracted, have sun java 1.6 and still can't get the application to work.  It launches, but when I try to load a pcap file I get this error and the app acts like nothing happened.

me@ubuntu-lt01:~/Desktop/tnv-0.3.8$ ./tnv_startup.sh 
Starting tnv on Linux using JRE java...
PacketCapture: loading native library jpcap.. Exception in thread "AWT-EventQueue-0" java.lang.UnsatisfiedLinkError: /home/nicholas/Desktop/tnv-0.3.8/lib/Linux/libjpcap.so: libstdc++-libc6.2-2.so.3: cannot open shared object file: No such file or directory
	at java.lang.ClassLoader$NativeLibrary.load(Native Method)
	at java.lang.ClassLoader.loadLibrary0(ClassLoader.java:1778)
	at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1703)
	at java.lang.Runtime.loadLibrary0(Runtime.java:823)
	at java.lang.System.loadLibrary(System.java:1030)
	at net.sourceforge.jpcap.capture.PacketCapture.<clinit>(PacketCapture.java:174)
	at net.sourceforge.tnv.TNV.importTcpdumpFile(TNV.java:744)
	at net.sourceforge.tnv.TNV.access$12(TNV.java:734)
	at net.sourceforge.tnv.TNV$8.actionPerformed(TNV.java:334)
	at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
	at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318)
	at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
	at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
	at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
	at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1225)
	at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1266)
	at java.awt.Component.processMouseEvent(Component.java:6134)
	at javax.swing.JComponent.processMouseEvent(JComponent.java:3265)
	at java.awt.Component.processEvent(Component.java:5899)
	at java.awt.Container.processEvent(Container.java:2023)
	at java.awt.Component.dispatchEventImpl(Component.java:4501)
	at java.awt.Container.dispatchEventImpl(Container.java:2081)
	at java.awt.Component.dispatchEvent(Component.java:4331)
	at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4301)
	at java.awt.LightweightDispatcher.processMouseEvent(Container.java:3965)
	at java.awt.LightweightDispatcher.dispatchEvent(Container.java:3895)
	at java.awt.Container.dispatchEventImpl(Container.java:2067)
	at java.awt.Window.dispatchEventImpl(Window.java:2458)
	at java.awt.Component.dispatchEvent(Component.java:4331)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
	at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)

---

