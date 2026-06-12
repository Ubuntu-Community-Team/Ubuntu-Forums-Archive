---
title: "Iriverter is giving me an error when i run it in terminal..."
date: 2007-07-30
forum: Multimedia &amp; Video
---

### Post by sent17inel on 2007-07-30
```
daniel@daniel-desktop:~$ iriverter
!!! An unhandled exception occured: class java.lang.UnsatisfiedLinkError
--- iriverter 0.16
--- 
--- Settings:
--- 
--- 
!!! no swt-pi-gtk-3236 in java.library.path
!!! 
!!! java.lang.ClassLoader.loadLibrary(ClassLoader.java:1682)
!!! java.lang.Runtime.loadLibrary0(Runtime.java:823)
!!! java.lang.System.loadLibrary(System.java:1030)
!!! org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
!!! org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:22)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
!!! org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
!!! org.eclipse.swt.widgets.Display.<clinit>(Display.java:126)
!!! org.thestaticvoid.iriverter.ConverterUI.<init>(ConverterUI.java:28)
!!! org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:666)
!!! 
Exception in thread "main" java.lang.NoClassDefFoundError: Could not initialize class org.eclipse.swt.widgets.Display
        at org.thestaticvoid.iriverter.ConverterUI.main(ConverterUI.java:675)
daniel@daniel-desktop:~$ 

```

any idea whats wrong? Do i need some sort of java file?

---

### Post by zoryn on 2007-07-31
I'm getting the same error. Any help would be greatly appreciated...

---

### Post by CupofDice on 2007-07-31
I just had the same problem and [this]("http://ubuntuforums.org/showthread.php?t=425860&highlight=iriverter") helped me.

---

