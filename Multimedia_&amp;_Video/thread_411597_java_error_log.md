---
title: "java error log"
date: 2007-04-17
forum: Multimedia &amp; Video
---

### Post by matoxxx on 2007-04-17
Hi,
i came across some java errors, while trying [http://www.travian.cz/chat.php](http://www.travian.cz/chat.php) java was resulting in firefox crash.


```
# An unexpected error has been detected by HotSpot Virtual Machine:
#
#  SIGSEGV (0xb) at pc=0xb1b31cfd, pid=31370, tid=2973367216
#
# Java VM: Java HotSpot(TM) Client VM (1.5.0_06-b05 mixed mode, sharing)
# Problematic frame:
# C  [libfontmanager.so+0x2ecfd]
#

---------------  T H R E A D  ---------------

Current thread (0x08091020):  JavaThread "AWT-EventQueue-2" [_thread_in_native, id=31413]

siginfo:si_signo=11, si_errno=0, si_code=1, si_addr=0x4d224e0c

Registers:
EAX=0x0814732c, EBX=0xb1b7f5a8, ECX=0x08146244, EDX=0x450ddae0
ESP=0xb139e554, EBP=0xb139e57c, ESI=0x0814732c, EDI=0x914376b8
EIP=0xb1b31cfd, CR2=0x4d224e0c, EFLAGS=0x00010212

Top of Stack: (sp=0xb139e554)
0xb139e554:   b139e5c4 b139e794 b139e5fc b7862028
0xb139e564:   450ddae0 914376b8 00000004 b1b7f5a8
0xb139e574:   08140e98 08140ecc b139e59c b1b37ec6
0xb139e584:   b139e5c4 00000000 0000000a b2436690
0xb139e594:   b1b83ac0 b7a6838c b139e6fc b1b3824e
0xb139e5a4:   b139e5c4 08142730 08142778 083c7a84
0xb139e5b4:   08091020 083db6b8 913d9420 b139e5c4
0xb139e5c4:   08146244 08146244 08146244 00004000 

Instructions: (pc=0xb1b31cfd)
0xb1b31ced:   8b 4a 08 8b 45 ec 8d 14 85 00 00 00 00 8b 41 04
0xb1b31cfd:   8b 14 10 8b 4d e8 8b 04 0e 29 d0 89 44 24 04 8b 

Stack: [0xb131f000,0xb13a0000),  sp=0xb139e554,  free space=509k
Native frames: (J=compiled Java code, j=interpreted, Vv=VM code, C=native code)
C  [libfontmanager.so+0x2ecfd]
C  [libfontmanager.so+0x34ec6]
C  [libfontmanager.so+0x3524e]
C  [libfontmanager.so+0x3768a]
C  [libfontmanager.so+0x35a92]
C  [libfontmanager.so+0x35faa]
C  [libfontmanager.so+0x225c6]
C  [libfontmanager.so+0x24326]
C  [libfontmanager.so+0x463c6]  Java_sun_font_FileFont_getGlyphImage+0x120
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtr(I)J+62
j  sun.font.FileFontStrike.getGlyphAdvance(I)F+59
j  sun.font.FileFontStrike.getCodePointAdvance(I)F+9
J  sun.font.FontDesignMetrics.getLatinCharWidth(C)F
j  sun.font.FontDesignMetrics.stringWidth(Ljava/lang/String;)I+36
j  irc.gui.pixx.PixxMenuBar.drawItem(Ljava/awt/Graphics;IIZLjava/lang/String;)V+133
j  irc.gui.pixx.PixxMenuBar.drawDisconnectItem(Ljava/awt/Graphics;IIZ)V+12
j  irc.gui.pixx.PixxMenuBar.update(Ljava/awt/Graphics;)V+210
j  irc.gui.pixx.PixxMenuBar.paint(Ljava/awt/Graphics;)V+2
j  sun.awt.RepaintArea.paintComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+6
j  sun.awt.X11.XRepaintArea.paintComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+23
j  sun.awt.RepaintArea.paint(Ljava/lang/Object;Z)V+326
j  sun.awt.X11.XComponentPeer.handleEvent(Ljava/awt/AWTEvent;)V+188
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEvent;)V+765
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEvent;)V+42
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEvent;)V+2
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V+46
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub
V  [libjvm.so+0x174fec]
V  [libjvm.so+0x2821f8]
V  [libjvm.so+0x174845]
V  [libjvm.so+0x1748de]
V  [libjvm.so+0x1ebee5]
V  [libjvm.so+0x2ea563]
V  [libjvm.so+0x282d08]
C  [libpthread.so.0+0x5341]

Java frames: (J=compiled Java code, j=interpreted, Vv=VM code)
j  sun.font.FileFont.getGlyphImage(JI)J+0
j  sun.font.FileFontStrike.getGlyphImagePtr(I)J+62
j  sun.font.FileFontStrike.getGlyphAdvance(I)F+59
j  sun.font.FileFontStrike.getCodePointAdvance(I)F+9
J  sun.font.FontDesignMetrics.getLatinCharWidth(C)F
j  sun.font.FontDesignMetrics.stringWidth(Ljava/lang/String;)I+36
j  irc.gui.pixx.PixxMenuBar.drawItem(Ljava/awt/Graphics;IIZLjava/lang/String;)V+133
j  irc.gui.pixx.PixxMenuBar.drawDisconnectItem(Ljava/awt/Graphics;IIZ)V+12
j  irc.gui.pixx.PixxMenuBar.update(Ljava/awt/Graphics;)V+210
j  irc.gui.pixx.PixxMenuBar.paint(Ljava/awt/Graphics;)V+2
j  sun.awt.RepaintArea.paintComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+6
j  sun.awt.X11.XRepaintArea.paintComponent(Ljava/awt/Component;Ljava/awt/Graphics;)V+23
j  sun.awt.RepaintArea.paint(Ljava/lang/Object;Z)V+326
j  sun.awt.X11.XComponentPeer.handleEvent(Ljava/awt/AWTEvent;)V+188
j  java.awt.Component.dispatchEventImpl(Ljava/awt/AWTEvent;)V+765
j  java.awt.Container.dispatchEventImpl(Ljava/awt/AWTEvent;)V+42
j  java.awt.Component.dispatchEvent(Ljava/awt/AWTEvent;)V+2
j  java.awt.EventQueue.dispatchEvent(Ljava/awt/AWTEvent;)V+46
j  java.awt.EventDispatchThread.pumpOneEventForHierarchy(ILjava/awt/Component;)Z+233
j  java.awt.EventDispatchThread.pumpEventsForHierarchy(ILjava/awt/Conditional;Ljava/awt/Component;)V+26
j  java.awt.EventDispatchThread.pumpEvents(ILjava/awt/Conditional;)V+4
j  java.awt.EventDispatchThread.pumpEvents(Ljava/awt/Conditional;)V+3
j  java.awt.EventDispatchThread.run()V+9
v  ~StubRoutines::call_stub

---------------  P R O C E S S  ---------------

Java Threads: ( => current thread )
  0x081a15b0 JavaThread "TimerQueue" daemon [_thread_blocked, id=31419]
  0x0836adb8 JavaThread "Read thread" [_thread_in_native, id=31414]
=>0x08091020 JavaThread "AWT-EventQueue-2" [_thread_in_native, id=31413]
  0x083c6960 JavaThread "Event dispatch thread" daemon [_thread_blocked, id=31409]
  0x0846a238 JavaThread "AWT-EventQueue-1" [_thread_blocked, id=31403]
  0x083c8790 JavaThread "thread applet-IRCApplet.class" [_thread_blocked, id=31390]
  0x083c5568 JavaThread "AWT-EventQueue-0" [_thread_blocked, id=31387]
  0x083c4188 JavaThread "AWT-Shutdown" [_thread_blocked, id=31386]
  0x083b93c0 JavaThread "Thread-2" [_thread_in_native, id=31385]
  0x0839c718 JavaThread "Thread-1" [_thread_blocked, id=31382]
  0x08396180 JavaThread "traceMsgQueueThread" daemon [_thread_blocked, id=31380]
  0x08381618 JavaThread "AWT-XAWT" daemon [_thread_blocked, id=31379]
  0x082f7d78 JavaThread "Java2D Disposer" daemon [_thread_blocked, id=31378]
  0x080b4eb8 JavaThread "Low Memory Detector" daemon [_thread_blocked, id=31376]
  0x080b3958 JavaThread "CompilerThread0" daemon [_thread_blocked, id=31375]
  0x080b2a38 JavaThread "Signal Dispatcher" daemon [_thread_blocked, id=31374]
  0x08096e50 JavaThread "Finalizer" daemon [_thread_blocked, id=31373]
  0x08096150 JavaThread "Reference Handler" daemon [_thread_blocked, id=31372]
  0x08051c80 JavaThread "main" [_thread_in_native, id=31370]

Other Threads:
  0x080935f0 VMThread [id=31371]
  0x080b6358 WatcherThread [id=31377]

VM state:at safepoint (normal execution)

VM Mutex/Monitor currently owned by a thread:  ([mutex/lock_event])
[0x080510d0/0x080510f8] Threads_lock - owner thread: 0x080935f0
[0x08051520/0x08051538] Heap_lock - owner thread: 0x083c6960

Heap
 def new generation   total 576K, used 64K [0x88a90000, 0x88b30000, 0x88f70000)
  eden space 512K,   0% used [0x88a90000, 0x88a90000, 0x88b10000)
  from space 64K, 100% used [0x88b20000, 0x88b30000, 0x88b30000)
  to   space 64K,   0% used [0x88b10000, 0x88b10000, 0x88b20000)
 tenured generation   total 3580K, used 3574K [0x88f70000, 0x892ef000, 0x8ca90000)
   the space 3580K,  99% used [0x88f70000, 0x892eda10, 0x892edc00, 0x892ef000)
 compacting perm gen  total 8192K, used 3557K [0x8ca90000, 0x8d290000, 0x90a90000)
   the space 8192K,  43% used [0x8ca90000, 0x8ce09640, 0x8ce09800, 0x8d290000)
    ro space 8192K,  68% used [0x90a90000, 0x9100c408, 0x9100c600, 0x91290000)
    rw space 12288K,  48% used [0x91290000, 0x91853a30, 0x91853c00, 0x91e90000)

Dynamic libraries:
08048000-0804c000 r-xp 00000000 08:07 311516     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java_vm
0804c000-0804d000 rwxp 00003000 08:07 311516     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/bin/java_vm
0804d000-084f9000 rwxp 0804d000 00:00 0          [heap]
88a90000-88b30000 rwxp 88a90000 00:00 0 
88b30000-88f70000 rwxp 88b30000 00:00 0 
88f70000-892ef000 rwxp 88f70000 00:00 0 
892ef000-8ca90000 rwxp 892ef000 00:00 0 
8ca90000-8d290000 rwxp 8ca90000 00:00 0 
8d290000-90a90000 rwxp 8d290000 00:00 0 
90a90000-9100d000 r-xs 00001000 08:07 312214     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
9100d000-91290000 rwxp 9100d000 00:00 0 
91290000-91854000 rwxp 0057e000 08:07 312214     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
91854000-91e90000 rwxp 91854000 00:00 0 
91e90000-91f5f000 rwxp 00b42000 08:07 312214     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
91f5f000-92290000 rwxp 91f5f000 00:00 0 
92290000-92294000 r-xs 00c11000 08:07 312214     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/classes.jsa
92294000-92690000 rwxp 92294000 00:00 0 
b0d00000-b0d29000 rwxp b0d00000 00:00 0 
b0d29000-b0e00000 ---p b0d29000 00:00 0 
b0eea000-b0ef8000 r-xs 00000000 08:07 412192     /usr/share/X11/fonts/Type1/cursor.pfa
b0ef8000-b0f01000 r-xs 00000000 08:07 412191     /usr/share/X11/fonts/Type1/c0649bt_.pfb
b0f01000-b0f0a000 r-xs 00000000 08:07 412189     /usr/share/X11/fonts/Type1/c0648bt_.pfb
b0f0a000-b0f13000 r-xs 00000000 08:07 412187     /usr/share/X11/fonts/Type1/c0633bt_.pfb
b0f1e000-b0f27000 r-xs 00000000 08:07 412185     /usr/share/X11/fonts/Type1/c0632bt_.pfb
b0f27000-b0f34000 rwxs 00000000 00:07 13959197   /SYSV00000000 (deleted)
b0f34000-b0f57000 r-xs 00000000 08:05 117484519  /home/matoxxx/.java/deployment/cache/javapi/v1.0/jar/pixx.jar-20c4f77-6e1c33e7.zip
b0f57000-b1020000 rwxs 00000000 00:07 13795352   /SYSV00000000 (deleted)
b1020000-b1023000 ---p b1020000 00:00 0 
b1023000-b10a1000 rwxp b1023000 00:00 0 
b10a1000-b10a4000 ---p b10a1000 00:00 0 
b10a4000-b1122000 rwxp b10a4000 00:00 0 
b1122000-b1125000 rwxp b1122000 00:00 0 
b1125000-b11a3000 rwxp b1125000 00:00 0 
b11a3000-b11a9000 r-xp 00000000 08:07 311538     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnio.so
b11a9000-b11aa000 rwxp 00005000 08:07 311538     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnio.so
b11aa000-b12f4000 rwxs 00000000 00:07 13598743   /SYSV00000000 (deleted)
b12f4000-b130c000 r-xp 00000000 08:07 311543     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdcpr.so
b130c000-b131f000 rwxp 00018000 08:07 311543     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdcpr.so
b131f000-b1322000 ---p b131f000 00:00 0 
b1322000-b13a0000 rwxp b1322000 00:00 0 
b13a0000-b14ea000 rwxs 00000000 00:07 13565974   /SYSV00000000 (deleted)
b14ea000-b152e000 r-xs 00000000 08:05 117484517  /home/matoxxx/.java/deployment/cache/javapi/v1.0/jar/irc.jar-6cecc188-7a18fa89.zip
b152e000-b153e000 r-xp 00000000 08:07 376944     /lib/tls/i686/cmov/libresolv-2.3.6.so
b153e000-b153f000 rwxp 00010000 08:07 376944     /lib/tls/i686/cmov/libresolv-2.3.6.so
b153f000-b1541000 rwxp b153f000 00:00 0 
b1544000-b154e000 r-xs 00000000 08:07 412183     /usr/share/X11/fonts/Type1/c0611bt_.pfb
b154e000-b1562000 r-xp 00000000 08:07 311537     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnet.so
b1562000-b1563000 rwxp 00013000 08:07 311537     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libnet.so
b1563000-b1566000 rwxp b1563000 00:00 0 
b1566000-b15e4000 rwxp b1566000 00:00 0 
b15e4000-b15e7000 ---p b15e4000 00:00 0 
b15e7000-b1665000 rwxp b15e7000 00:00 0 
b1665000-b1668000 ---p b1665000 00:00 0 
b1668000-b16e6000 rwxp b1668000 00:00 0 
b16e6000-b16e9000 ---p b16e6000 00:00 0 
b16e9000-b1767000 rwxp b16e9000 00:00 0 
b1767000-b176a000 ---p b1767000 00:00 0 
b176a000-b17e8000 rwxp b176a000 00:00 0 
b17e8000-b17eb000 ---p b17e8000 00:00 0 
b17eb000-b1869000 rwxp b17eb000 00:00 0 
b1869000-b186c000 ---p b1869000 00:00 0 
b186c000-b18ea000 rwxp b186c000 00:00 0 
b18ea000-b18ed000 ---p b18ea000 00:00 0 
b18ed000-b196b000 rwxp b18ed000 00:00 0 
b196b000-b196e000 ---p b196b000 00:00 0 
b196e000-b19ec000 rwxp b196e000 00:00 0 
b19ec000-b19ef000 ---p b19ec000 00:00 0 
b19ef000-b1a6d000 rwxp b19ef000 00:00 0 
b1a6d000-b1a70000 r-xp 00000000 08:07 263598     /usr/lib/libXfixes.so.3.0.0
b1a70000-b1a71000 rwxp 00003000 08:07 263598     /usr/lib/libXfixes.so.3.0.0
b1a71000-b1a78000 r-xp 00000000 08:07 263618     /usr/lib/libXrender.so.1.3.0
b1a78000-b1a79000 rwxp 00006000 08:07 263618     /usr/lib/libXrender.so.1.3.0
b1a79000-b1a81000 r-xp 00000000 08:07 263590     /usr/lib/libXcursor.so.1.0.2
b1a81000-b1a82000 rwxp 00007000 08:07 263590     /usr/lib/libXcursor.so.1.0.2
b1a82000-b1a85000 ---p b1a82000 00:00 0 
b1a85000-b1b03000 rwxp b1a85000 00:00 0 
b1b03000-b1b76000 r-xp 00000000 08:07 311554     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libfontmanager.so
b1b76000-b1b80000 rwxp 00073000 08:07 311554     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libfontmanager.so
b1b80000-b1b84000 rwxp b1b80000 00:00 0 
b1b84000-b1b97000 r-xp 00000000 08:07 311566     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so
b1b97000-b1b98000 rwxp 00012000 08:07 311566     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so
b1b98000-b1bac000 rwxp b1b98000 00:00 0 
b1bac000-b1bae000 r-xp 00000000 08:07 263585     /usr/lib/libXau.so.6.0.0
b1bae000-b1baf000 rwxp 00001000 08:07 263585     /usr/lib/libXau.so.6.0.0
b1baf000-b1c90000 r-xp 00000000 08:07 263579     /usr/lib/libX11.so.6.2.0
b1c90000-b1c94000 rwxp 000e1000 08:07 263579     /usr/lib/libX11.so.6.2.0
b1c94000-b1c95000 rwxp b1c94000 00:00 0 
b1c95000-b1ca1000 r-xp 00000000 08:07 263596     /usr/lib/libXext.so.6.4.0
b1ca1000-b1ca2000 rwxp 0000c000 08:07 263596     /usr/lib/libXext.so.6.4.0
b1ca6000-b1caa000 r-xp 00000000 08:07 376918     /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b1caa000-b1cab000 rwxp 00003000 08:07 376918     /lib/tls/i686/cmov/libnss_dns-2.3.6.so
b1cab000-b1cae000 r-xp 00000000 08:07 311569     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdeploy.so
b1cae000-b1caf000 rwxp 00002000 08:07 311569     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libdeploy.so
b1caf000-b1ce5000 r-xp 00000000 08:07 311549     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/xawt/libmawt.so
b1ce5000-b1ce8000 rwxp 00035000 08:07 311549     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/xawt/libmawt.so
b1ce8000-b1ce9000 rwxp b1ce8000 00:00 0 
b1ce9000-b1daf000 r-xp 00000000 08:07 311544     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libmlib_image.so
b1daf000-b1db0000 rwxp 000c5000 08:07 311544     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libmlib_image.so
b1db0000-b1e25000 r-xp 00000000 08:07 361346     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libawt.so
b1e25000-b1e2b000 rwxp 00074000 08:07 361346     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libawt.so
b1e2b000-b1e4f000 rwxp b1e2b000 00:00 0 
b1e4f000-b1f13000 r-xs 00000000 08:07 312203     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/localedata.jar
b1f13000-b1f3e000 r-xs 00000000 08:07 311571     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/sunpkcs11.jar
b1f3e000-b1f64000 r-xs 00000000 08:07 361481     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/sunjce_provider.jar
b1f64000-b1f65000 ---p b1f64000 00:00 0 
b1f65000-b1fe5000 rwxp b1f65000 00:00 0 
b1fe5000-b1fe8000 ---p b1fe5000 00:00 0 
b1fe8000-b2066000 rwxp b1fe8000 00:00 0 
b2066000-b2069000 ---p b2066000 00:00 0 
b2069000-b20e7000 rwxp b2069000 00:00 0 
b20e7000-b20ea000 ---p b20e7000 00:00 0 
b20ea000-b2168000 rwxp b20ea000 00:00 0 
b2168000-b219b000 r-xp 00000000 08:07 267008     /usr/lib/locale/sk_SK.utf8/LC_CTYPE
b219b000-b219e000 ---p b219b000 00:00 0 
b219e000-b221c000 rwxp b219e000 00:00 0 
b221c000-b221f000 ---p b221c000 00:00 0 
b221f000-b229d000 rwxp b221f000 00:00 0 
b229d000-b229e000 ---p b229d000 00:00 0 
b229e000-b232a000 rwxp b229e000 00:00 0 
b232a000-b2346000 rwxp b232a000 00:00 0 
b2346000-b2348000 rwxp b2346000 00:00 0 
b2348000-b2364000 rwxp b2348000 00:00 0 
b2364000-b2365000 rwxp b2364000 00:00 0 
b2365000-b2366000 rwxp b2365000 00:00 0 
b2366000-b2369000 rwxp b2366000 00:00 0 
b2369000-b2384000 rwxp b2369000 00:00 0 
b2384000-b2388000 rwxp b2384000 00:00 0 
b2388000-b23a4000 rwxp b2388000 00:00 0 
b23a4000-b23b6000 rwxp b23a4000 00:00 0 
b23b6000-b242f000 rwxp b23b6000 00:00 0 
b242f000-b25c7000 rwxp b242f000 00:00 0 
b25c7000-b442f000 rwxp b25c7000 00:00 0 
b442f000-b462c000 r-xs 00000000 08:07 311647     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/deploy.jar
b462c000-b4724000 r-xs 00000000 08:07 311662     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/plugin.jar
b4724000-b4f5f000 r-xs 00000000 08:07 312209     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/charsets.jar
b4f5f000-b4f73000 r-xs 00000000 08:07 312204     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/jce.jar
b4f73000-b4ff8000 r-xs 00000000 08:07 312200     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/jsse.jar
b4ff8000-b5061000 rwxp b4ff8000 00:00 0 
b5061000-b7649000 r-xs 00000000 08:07 311600     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/rt.jar
b7649000-b765c000 r-xp 00000000 08:07 311534     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libzip.so
b765c000-b765e000 rwxp 00012000 08:07 311534     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libzip.so
b765e000-b767f000 r-xp 00000000 08:07 311533     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjava.so
b767f000-b7681000 rwxp 00020000 08:07 311533     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjava.so
b7681000-b768c000 r-xp 00000000 08:07 311532     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libverify.so
b768c000-b768d000 rwxp 0000b000 08:07 311532     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libverify.so
b768d000-b7696000 r-xp 00000000 08:07 376920     /lib/tls/i686/cmov/libnss_files-2.3.6.so
b7696000-b7697000 rwxp 00008000 08:07 376920     /lib/tls/i686/cmov/libnss_files-2.3.6.so
b7697000-b769f000 r-xp 00000000 08:07 376924     /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b769f000-b76a0000 rwxp 00007000 08:07 376924     /lib/tls/i686/cmov/libnss_nis-2.3.6.so
b76a0000-b76a8000 r-xp 00000000 08:07 376916     /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b76a8000-b76a9000 rwxp 00007000 08:07 376916     /lib/tls/i686/cmov/libnss_compat-2.3.6.so
b76a9000-b76bb000 r-xp 00000000 08:07 376914     /lib/tls/i686/cmov/libnsl-2.3.6.so
b76bb000-b76bc000 rwxp 00012000 08:07 376914     /lib/tls/i686/cmov/libnsl-2.3.6.so
b76bc000-b76c3000 rwxp b76bc000 00:00 0 
b76c3000-b76cb000 rwxs 00000000 08:07 100789     /tmp/hsperfdata_matoxxx/31370
b76cb000-b76ec000 r-xp 00000000 08:07 376907     /lib/tls/i686/cmov/libm-2.3.6.so
b76ec000-b76ed000 rwxp 00020000 08:07 376907     /lib/tls/i686/cmov/libm-2.3.6.so
b76ed000-b7a4d000 r-xp 00000000 08:07 311527     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/libjvm.so
b7a4d000-b7a6b000 rwxp 0035f000 08:07 311527     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client/libjvm.so
b7a6b000-b7e82000 rwxp b7a6b000 00:00 0 
b7e82000-b7fa7000 r-xp 00000000 08:07 376874     /lib/tls/i686/cmov/libc-2.3.6.so
b7fa7000-b7fae000 rwxp 00125000 08:07 376874     /lib/tls/i686/cmov/libc-2.3.6.so
b7fae000-b7fb1000 rwxp b7fae000 00:00 0 
b7fb1000-b7fb3000 r-xp 00000000 08:07 376893     /lib/tls/i686/cmov/libdl-2.3.6.so
b7fb3000-b7fb4000 rwxp 00001000 08:07 376893     /lib/tls/i686/cmov/libdl-2.3.6.so
b7fb4000-b7fb5000 rwxp b7fb4000 00:00 0 
b7fb5000-b7fc4000 r-xp 00000000 08:07 376940     /lib/tls/i686/cmov/libpthread-2.3.6.so
b7fc4000-b7fc5000 rwxp 0000e000 08:07 376940     /lib/tls/i686/cmov/libpthread-2.3.6.so
b7fc5000-b7fc7000 rwxp b7fc5000 00:00 0 
b7fc9000-b7fcb000 r-xs 00000000 08:07 312202     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/ext/dnsns.jar
b7fcb000-b7fd1000 r-xp 00000000 08:07 311522     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/native_threads/libhpi.so
b7fd1000-b7fd2000 rwxp 00006000 08:07 311522     /usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/native_threads/libhpi.so
b7fd2000-b7fd3000 rwxp b7fd2000 00:00 0 
b7fd3000-b7fd4000 ---p b7fd3000 00:00 0 
b7fd4000-b7fd7000 rwxp b7fd4000 00:00 0 
b7fd7000-b7fec000 r-xp 00000000 08:07 379608     /lib/ld-2.3.6.so
b7fec000-b7fed000 rwxp 00014000 08:07 379608     /lib/ld-2.3.6.so
bf7ec000-bf7ef000 ---p bf7ec000 00:00 0 
bf7ef000-bf9ec000 rwxp bf7ef000 00:00 0          [stack]
ffffe000-fffff000 ---p 00000000 00:00 0          [vdso]

VM Arguments:
jvm_args: -DtrustProxy=true -Xverify:remote -Djava.protocol.handler.pkgs=sun.plugin.net.protocol -Xbootclasspath/a:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/plugin.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/deploy.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=150_06 -Djavaplugin.version=1.5.0_06 -Djavaplugin.vm.options=-DtrustProxy=true -Xverify:remote -Djava.class.path=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/classes -Djava.class.path=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/classes -Djava.protocol.handler.pkgs=sun.plugin.net.protocol -Xbootclasspath/a:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/plugin.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/deploy.jar:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/javaplugin_l10n.jar -Djavaplugin.lib=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/libjavaplugin_jni.so -Dmozilla.workaround=true -Djavaplugin.nodotversion=150_06 -Djavaplugin.version=1.5.0_06 
java_command: <unknown>
Launcher Type: generic

Environment Variables:
JAVA_HOME=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
USERNAME=matoxxx
LD_LIBRARY_PATH=/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386/client:/usr/lib/jvm/java-1.5.0-sun-1.5.0.06/jre/lib/i386:/usr/lib/firefox:/usr/lib/firefox/plugins:/usr/lib/mozilla-firefox/plugins
SHELL=/bin/bash
DISPLAY=:0.0

Signal Handlers:
SIGSEGV: [libjvm.so+0x31b990], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGBUS: [libjvm.so+0x31b990], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGFPE: [libjvm.so+0x281230], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGPIPE: [libjvm.so+0x281230], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGILL: [libjvm.so+0x281230], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGUSR1: SIG_DFL, sa_mask[0]=0x00000000, sa_flags=0x00000000
SIGUSR2: [libjvm.so+0x283580], sa_mask[0]=0x00000000, sa_flags=0x10000004
SIGHUP: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGINT: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGQUIT: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004
SIGTERM: [libjvm.so+0x282fb0], sa_mask[0]=0x7ffbfeff, sa_flags=0x10000004


---------------  S Y S T E M  ---------------

OS:testing/unstable

uname:Linux 2.6.15-28-386 #1 PREEMPT Thu Feb 1 15:51:56 UTC 2007 i686
libc:glibc 2.3.6 NPTL 2.3.6 
rlimit: STACK 8192k, CORE 0k, NPROC infinity, NOFILE 1024, AS infinity
load average:1.29 0.63 0.29

CPU:total 1 family 47, cmov, cx8, fxsr, mmx, sse, sse2

Memory: 4k page, physical 515816k(86236k free), swap 1052212k(904372k free)

vm_info: Java HotSpot(TM) Client VM (1.5.0_06-b05) for linux-x86, built on Dec 17 2005 01:54:22 by java_re with gcc 3.2.1-7a (J2SE release)



```

dont know where should i post it, give me hint please ..

---

### Post by kidders on 2007-04-19
Hi there,

> **matoxxx said:**
> SIGSEGV (0xb)

That little snippet is the important part, when it comes to finding a good place to post your problem. To me, this means "Signal 11" which (unless I'm mistaken) is a segfault. This means that the Ubuntu developers may want to know about it.

If you can reproduce this bug reliably, and provide step-by-step instructions for doing so, you should bring this issue to the attention of the development team. They will be able to tell you pretty quickly whether you have discovered a flaw in Ubuntu's implementation of Java. If you have, you will be doing a great service for the Linux community, and you'll be able to track the progress of any bugfix. :-)

Be aware however that if you are *not* using a JRE provided by Ubuntu, they will not be able to help you. You may have better luck with the company you downloaded it from (Sun, maybe?).

I hope that's of some help.

---

### Post by matoxxx on 2007-04-21
I can reproduce this bug, in firefox or in epiphany, its sun's java related bug.
I am using sun's java 1,5 from repozitories.

---

