---
title: "google earth woes"
date: 2008-10-03
forum: Multimedia Software
---

### Post by StPenguin on 2008-10-03
Greetings all, and welcome to the thread of my first 'alrightIgiveupletshittheforums' problem on ubuntu :D I installed Google Earth from the repositories, and it crashes while trying to start (while showing the splash screen). As you can see from the ouput, there seems to be a troubling line after the command about not being able to open the unichrome driver...however, this message also appears after opening glxgears (and it runs succesfully).
System info:
8.04 with openbox. I'm on an av3715-eh1 laptop, which is a 32bit cpu and a Via S3 Unichrome Pro IGP. I'm using the drivers from the via site (not the unichrome, openchrome, or other in the repositories). Glxgears seems to run fine, however, come to think of it, I think that's the only other 3d app I've run so far.

Output: xxx@xxx:~$ googleearth
/usr/lib/dri/via_unichrome_dri.so: cannot open shared object file: No such file or directory
Google Earth has caught signal 11.

Stacktrace from glibc:
  /usr/lib/googleearth/googleearth-bin [0x804f403]
  /usr/lib/googleearth/googleearth-bin [0x804f916]
  [0xb7f62420]
  /usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx15igVisualContext14resetToDefaultENS0_20IG_GFX_DEFAULT_STATEE+0x45d) [0xb3e9cbed]
  /usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext14resetToDefaultENS0_20IG_GFX_DEFAULT_STATEE+0x22) [0xb3e9cdc2]
  /usr/lib/googleearth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x43f) [0xb3ec22cf]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext11openContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0xff) [0xb3a8f9bf]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x1fb) [0xb3a9128b]
  /usr/lib/googleearth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x8f) [0xb3c51caf]
  /usr/lib/googleearth/librender.so(_ZN12RenderWidget6setApiEPN5earth4evll3APIE+0x4f) [0xb67ee12f]
  /usr/lib/googleearth/librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0xb2) [0xb67f8e92]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x90) [0xb73362d0]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0xa86) [0xb77d30d2]
  /usr/lib/googleearth/libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0x1d3) [0xb779744b]
  /usr/lib/googleearth/libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x132) [0xb779e03e]
  /usr/lib/googleearth/libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x62) [0xb7d90eda]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0xf9) [0xb77d57a9]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83) [0xb77d5507]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb77d56a4]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb77d5710]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb77d7d6b]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb77d568e]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb77d5710]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x83) [0xb77d5507]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb77d56a4]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb77d5710]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb77d7d6b]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb77d568e]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb77d5710]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb77d7d6b]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb77d568e]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb77d5710]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb77d7d6b]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb77d568e]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb77d5710]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb77d7d6b]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb77d568e]
  /usr/lib/googleearth/libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x60) [0xb77d5710]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb77d7d6b]
  /usr/lib/googleearth/libQtGui.so.4(_ZN7QWidget10showNormalEv+0x68) [0xb77ce0f0]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN10MainWindow18readScreensizeInfoEv+0xc0f) [0xb7316e4f]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application12setupMainWinERK7QStringb+0x2ab) [0xb72c69ab]
  /usr/lib/googleearth/libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x2f1) [0xb72ca451]
  /usr/lib/googleearth/googleearth-bin(main+0x2ba) [0x8050bea]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe0) [0xb70f7450]
  /usr/lib/googleearth/googleearth-bin [0x804f231]

If this is a known problem, I apologize for wasting your time, please point me to the right thread, I searched as best as I could. Thanks!!

---

### Post by StPenguin on 2008-10-04
anyone? would really love to have this fixed by next weekend, going on a trip and would like to have google earth handy to keep track of the geocache sites.

---

### Post by Jim Lennington on 2008-10-23
StPenguin:
Don't want you to feel like you're alone. I have a similar problem with GE crashing at the opening screen and restarting Xoffice with it. I don't have a solution and am a total NEWB. I am looking for help also.

---

### Post by Spitphire on 2008-11-02
can i see your /etc/X11/xorg.conf

also output of uname -a

---

### Post by openprivacy on 2008-11-06
I have the same stacktrace.  Perhaps it's because I'm running 64-bit?
```
> uname -a
Linux imagine 2.6.27-7-generic #1 SMP Tue Nov 4 19:33:06 UTC 2008 x86_64 GNU/Linux

```
My xorg.conf is totally stock:
```

Section "Device"
        Identifier      "Configured Video Device"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
EndSection
```

---

