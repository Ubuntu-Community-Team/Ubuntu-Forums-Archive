---
title: "Eclipse still broken (in dependency hell)"
date: 2010-08-16
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Jimbob0i0 on 2010-08-16
Bug [lpbug]600626[/lpbug] is for testng missing in release (main). There was allegedly a "fix committed" on 15th July but testng still resides in Universe rather than Main.

This unfortunately breaks the build process for libhamcrest-java as can be seen in the build logs [here](https://launchpad.net/ubuntu/+source/libhamcrest-java/1.1-8/+build/1814732).

Eclipse depends on libhamcrest-java and has a bug [lpbug]603656[/lpbug] that this refers to. This is also listed as 'fix comitted' and yet no fix is yet forthcoming.

As things stand eclipse will not be possible to install on Maverick and there has been no change for a month in this situation....

Any ideas how to progress this from here?

---

### Post by Jimbob0i0 on 2010-08-17
Looks like these bugs break Android Developer Tools installation on Maverick anyway and have only been fixed in most recent 3.6 .... which is not compatible with Android Developer Tools.... nice ;)

Gave up on eclipse in Ubuntu for now and directly installed to /opt from the site (classic version) with the user having write permissions to the install to get it working...

Just to save others the frustration in trying to install ADT on the repo included eclipse....

Bugs from Eclipse:
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=297329](https://bugs.eclipse.org/bugs/show_bug.cgi?id=297329)
[https://bugs.eclipse.org/bugs/show_bug.cgi?id=287246](https://bugs.eclipse.org/bugs/show_bug.cgi?id=287246)

---

### Post by JCoster on 2010-08-17
You can download the tar from the Eclipse website for 3.6 Helius and extract that?  Having upgraded from Lucid, I already had an Eclipse install and once updated to Maverick, I noticed last night it was unusable.

So I downloaded 3.6 and extracted it over the files in /usr/lib64/eclipse/ and I'm away.

---

### Post by Jimbob0i0 on 2010-08-17
I generally wouldn't advise installing over files that have been put in place by your package manager....

Things like checksums will be wrong and if/when an updated package appears in the repositories what you have put in place will be at best clobbered and at worst turned into an unholy mess of various files...

If you are going to extract an app to use direct from a website it is best to extract into either /usr/local or /opt to prevent such clobbering - or roll your own deb that conflicts (and overrides) the one(s) from the repository...

3.6 currently has issues with Android Developer Toosl which is why I was trying to get 3.5 working and ended up using 3.5 classic from the eclipse site extracted to /opt with my user having write permissions to that location.

---

### Post by PrathameshD on 2010-08-19
is what I get the same thing as you all are talking about?
I installed Eclipse 3.5.2-5 platform using the Software Center...
and whenever I run Eclipse it doen't open and directs me to the log file..
This is the log file
```

!ENTRY org.eclipse.osgi 4 0 2010-08-19 17:07:39.624
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

---

### Post by Jimbob0i0 on 2010-08-19
Software centre doesn't install the eclipse (meta) package but rather just eclipse-platform...

The dependency is now fixed so in the next few days we shoudl have installable packages again...

Of course you might hit the upstream eclipse bug(s) I linked still so a non-shared install might still be beneficial ;)

---

