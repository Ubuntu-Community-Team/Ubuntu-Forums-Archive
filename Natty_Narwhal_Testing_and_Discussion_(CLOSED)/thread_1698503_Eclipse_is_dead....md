---
title: "Eclipse is dead..."
date: 2011-03-02
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Ancanus on 2011-03-02
...after the latest xulrunner update I guess.

Crashes on start up and dumps this on the log:

```

!ENTRY org.eclipse.osgi 4 0 2011-03-02 11:05:49.773
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: no swt-gtk-3557 or swt-gtk in swt.library.path, java.library.path or the jar file
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:254)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:159)
        at org.eclipse.swt.internal.C.<clinit>(C.java:21)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:131)
        at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:516)
        at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
        at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:143)
        at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:88)
        at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
        at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
        at org.eclipse.equinox.launcher.Main.run(Main.java:1311)

```

Pity, since I've got a project due in a few hours (teaches you to stick to stable!)

Anyone knows of a workaround until the Eclipse package gets updated?

---

### Post by dino99 on 2011-03-02
continue with maverick, or downgrade the faulty package, but which one ? Or continue with Natty livecd.

---

### Post by The_Eggert on 2011-03-02
/Off topic
Jesus - I thought the project had been discontinued.. :P

---

### Post by SevenMachines on 2011-03-02
> **Ancanus said:**
> ...after the latest xulrunner update I guess.

Crashes on start up and dumps this on the log:

```
...
```Pity, since I've got a project due in a few hours (teaches you to stick to stable!)

Anyone knows of a workaround until the Eclipse package gets updated?
Just download the tarball 
[http://www.eclipse.org/downloads/](http://www.eclipse.org/downloads/)
unzip and run. i tend to have both the repository and the more up to date local downloaded version at any one time myself

---

### Post by ubuntu27 on 2011-03-03
> **The_Eggert said:**
> /Off topic
Jesus - I thought the project had been discontinued.. :P

I had the same thought when I read the title.:lolflag:

---

### Post by nasp on 2011-03-04
Same issue with natty alpha 3 64 bit.

[This bug was revived]("https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/620516").
Not sure if we should create a new one.

---

