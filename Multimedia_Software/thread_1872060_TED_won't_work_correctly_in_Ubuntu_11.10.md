---
title: "TED won't work correctly in Ubuntu 11.10"
date: 2011-10-30
forum: Multimedia Software
---

### Post by Lrpbpb on 2011-10-30
TED (torrent episode downloader) has some issues with the Unity panel. Running it the first time I got the following error:

```

(java:5310): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:5310): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:5310): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",

(java:5310): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Exception in thread "main" java.lang.UnsatisfiedLinkError: no tray in java.library.path
    at java.lang.ClassLoader.loadLibrary(ClassLoader.java:1681)
    at java.lang.Runtime.loadLibrary0(Runtime.java:840)
    at java.lang.System.loadLibrary(System.java:1047)
    at org.jdesktop.jdic.tray.internal.impl.GnomeSystemTrayService.<clinit>(Unknown Source)
    at org.jdesktop.jdic.tray.internal.impl.ServiceManagerStub.getService(Unknown Source)
    at org.jdesktop.jdic.tray.internal.ServiceManager.getService(Unknown Source)
    at org.jdesktop.jdic.tray.SystemTray.<clinit>(Unknown Source)
    at ted.TedTrayIcon.<init>(TedTrayIcon.java:28)
    at ted.TedMainDialog.initGUI(TedMainDialog.java:309)
    at ted.TedMainDialog.<init>(TedMainDialog.java:125)
    at ted.TedMain.main(TedMain.java:50)

```I then discovered in the forums that by running: "java -jar ted.jar noTray" it would work, however it doesn't appear in the unity panel.  I tried white listing all apps but that gave me the same error.

Is there anyway to make ted appear in the unity panel in ubuntu 11.10?

---

### Post by bruno9779 on 2011-10-30
It is java based, you could give it a try with Oracle Java 7. It solved many of my java issues, alas, it isn't foss.

---

