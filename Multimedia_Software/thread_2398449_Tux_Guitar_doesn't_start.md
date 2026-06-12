---
title: "Tux Guitar doesn't start"
date: 2018-08-12
forum: Multimedia Software
---

### Post by dkennyk on 2018-08-12
Hello,

I tried to install TuxGuitar both within the terminal and at Budgie Software. The program shows up in the start menu, but when I try to run it, it doesn't start. The TuxGuitar icon appears at the left dock, but that's all. What can I do?

---

### Post by Yellow Pasque on 2018-08-12
Try to start it from the terminal and see if you can get a clue from error messages.

---

### Post by dkennyk on 2018-08-13
Sorry, I'm a noob at linux.

This comes up in the terminal:

Exception in thread "main" java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:256)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:236)
    at org.eclipse.swt.internal.C.<clinit>(C.java:16)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:139)
    at org.herac.tuxguitar.gui.TuxGuitar.displayGUI(Unknown Source)
    at org.herac.tuxguitar.gui.TGMain.main(Unknown Source)

---

### Post by mariroma on 2018-08-16
[COLOR=#000000][FONT=Verdana]I just installed it on one of my systems, works fine here. I saw there is a 32 bit version, and a 64 bit source version. Are you sure you installed the version that matches your system?[/FONT][/COLOR]

---

