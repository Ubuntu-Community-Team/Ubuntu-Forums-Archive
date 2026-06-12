---
title: "What's The Fix for Google Earth Signal 11?"
date: 2009-09-07
forum: Multimedia Software
---

### Post by Dipper on 2009-09-07
I am using:

Acer Aspire One netbook
Kubuntu 8.10
Latest intel driver

This is what I get when trying to launch Google Earth:

```
Google Earth has caught signal 11.

Stacktrace from glibc:
  ./googleearth-bin [0x806c343]
  ./googleearth-bin [0x806c8b6]
  [0xb80cd400]                 
  /usr/lib/libX11.so.6(XInitExtension+0x41) [0xb6590771]
  /usr/lib/libXext.so.6(XextAddDisplay+0x52) [0xb6668692]
  /usr/lib/libGL.so.1 [0xb60b058b]                       
  /usr/lib/libGL.so.1 [0xb60b0e0f]                       
  /usr/lib/libGL.so.1 [0xb60adfcf]                       
  /opt/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext15setSwapIntervalEi+0x124) [0xb2815a34]                                                          
  /opt/google-earth/libIGGfx.so(_ZN3Gap3Gfx18igOglVisualContext4openEv+0x5c8) [0xb2836358]                                                                      
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext11OpenContextEN3Gap3Gfx25igRenderDestinationFormatERKNS0_8InitInfoE+0x101) [0xb2448a01]             
  /opt/google-earth/libevll.so(_ZN5earth4evll13VisualContext4initERKNS0_8InitInfoE+0x22d) [0xb2453b6d]                                                          
  /opt/google-earth/libevll.so(_ZN5earth4evll17RenderContextImpl4initERKNS0_8InitInfoE+0x87) [0xb231c7a7]                                                       
  ./librender.so(_ZN12RenderWidget6SetApiEPN5earth4evll3APIE+0x47) [0xb6249e67] 
  ./librender.so(_ZN5earth6render12RenderWindow12createWidgetEv+0xae) [0xb622992e]                                                                              
  ./libgoogleearth_lib.so(_ZN5earth6client12ModuleWidget9showEventEP10QShowEvent+0x8e) [0xb6e9f14e]                                                             
  ./libQtGui.so.4(_ZN7QWidget5eventEP6QEvent+0x7cf) [0xb780f15f]                
  ./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa8) [0xb77cd130]                                                                  
  ./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x122) [0xb77d4916]
  ./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x9a) [0xb7ebb2f2]                                                                   
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x11f) [0xb7811fc3]        
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7b) [0xb7811d0f]      
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb7811e98]       
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb7811ee6]         
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78124bb]                 
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb7811e82]       
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb7811ee6]         
  ./libQtGui.so.4(_ZN14QWidgetPrivate14show_recursiveEv+0x7b) [0xb7811d0f]      
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x15c) [0xb7811e98]       
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb7811ee6]         
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78124bb]                 
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb7811e82]       
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb7811ee6]         
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78124bb]                 
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb7811e82]       
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb7811ee6]         
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78124bb]                 
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb7811e82]       
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb7811ee6]         
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78124bb]                 
  ./libQtGui.so.4(_ZN14QWidgetPrivate12showChildrenEb+0x146) [0xb7811e82]       
  ./libQtGui.so.4(_ZN14QWidgetPrivate11show_helperEv+0x42) [0xb7811ee6]         
  ./libQtGui.so.4(_ZN7QWidget10setVisibleEb+0x3bb) [0xb78124bb]                 
  ./libQtGui.so.4(_ZN7QWidget13showMaximizedEv+0x4d) [0xb7807865]               
  ./libgoogleearth_lib.so(_ZN10MainWindow18readScreensizeInfoEv+0xc1d) [0xb6e7097d]                                                                             
  ./libgoogleearth_lib.so(_ZN5earth6client11Application12SetupMainWinERK7QStringb+0x1f0) [0xb6ed9890]                                                           
  ./libgoogleearth_lib.so(_ZN5earth6client11Application3runEv+0x313) [0xb6eda5f3]
  ./googleearth-bin(main+0x286) [0x806cde6]
  /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe5) [0xb6c61685]
  ./googleearth-bin [0x806bad1]




We apologize for the inconvenience, but Google Earth has crashed.
 This is a bug in the program, and should never happen under normal
 circumstances. A bug report and debugging data are now being written
 to this text file:

    /root/.googleearth/crashlogs/crashlog-1C177AAB.txt

This bug report will be sent to Google automatically next time you run
 Google Earth. Its data, which contains no personal information, will help
 us correct problems without bothering you further. If you would rather
 this info not be transmitted, please delete the above file before running
 the program again. If you want bug reports to NEVER be sent, remove the
 above 'crashlogs' directory's read/write permissions.
```

What's the fix?

---

### Post by Dipper on 2009-09-08
bump

---

### Post by Dipper on 2009-09-09
bump

---

### Post by juliobahar on 2010-08-25
I have the same problem, discovered only recently
using Lucid on two PC one with an ATI and another with an NVIDIA card. Google Crashes when viewing "PLACES" links.

this is my crashlog

```


Major Version 5
Minor Version 2
Build Number 0001
Build Date Jun 10 2010
Build Time 16:15:55
OS Type 3
OS Major Version 2
OS Minor Version 6
OS Build Version 32
OS Patch Version 0
Crash Signal 11
Crash Time 1282708066
Up Time 43.5115

Stacktrace from glibc:
./libgoogleearth_free.so(+0xd030b)[0xb9630b]
[0x67b400]
/usr/lib/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_from_pixdata+0x13f)[0x2a2400f]
/usr/lib/libgdk_pixbuf-2.0.so.0(gdk_pixbuf_new_from_inline+0x63)[0x2a242d3]
/usr/lib/flashplugin-installer/libflashplayer.so(+0x4d395)[0x9ed8a395]
/usr/lib/flashplugin-installer/libflashplayer.so(+0x4bdee)[0x9ed88dee]
/usr/lib/flashplugin-installer/libflashplayer.so(NP_Initialize+0x1ae)[0x9ed8d28e]
./libQtWebKit.so.4(+0x747b22)[0x476ab22]
./libQtWebKit.so.4(+0x747c0c)[0x476ac0c]
./libQtWebKit.so.4(+0x6062ff)[0x46292ff]
./libQtWebKit.so.4(+0x604516)[0x4627516]
./libQtWebKit.so.4(+0x60476a)[0x462776a]
./libQtWebKit.so.4(+0x712beb)[0x4735beb]
./libQtWebKit.so.4(+0x5b1595)[0x45d4595]
./libQtWebKit.so.4(+0x5a185c)[0x45c485c]
./libQtWebKit.so.4(+0x5b40dd)[0x45d70dd]
./libQtWebKit.so.4(+0x5b40f6)[0x45d70f6]
./libQtWebKit.so.4(+0xaa520f)[0x4ac820f]
./libQtWebKit.so.4(+0x16ad57)[0x418dd57]
./libQtWebKit.so.4(+0x1749d5)[0x41979d5]
./libQtWebKit.so.4(+0x183282)[0x41a6282]
./libQtWebKit.so.4(+0x1bc22d)[0x41df22d]
./libQtWebKit.so.4(+0x29ac5d)[0x42bdc5d]
./libQtWebKit.so.4(+0x2a9410)[0x42cc410]
./libQtWebKit.so.4(+0x2a9f72)[0x42ccf72]
./libQtWebKit.so.4(+0x2b7fea)[0x42dafea]
./libQtWebKit.so.4(+0x4be45a)[0x44e145a]
./libQtWebKit.so.4(+0x4c6842)[0x44e9842]
./libQtWebKit.so.4(+0x501706)[0x4524706]
./libQtWebKit.so.4(+0x5017fb)[0x45247fb]
./libQtWebKit.so.4(+0x539f0b)[0x455cf0b]
./libQtWebKit.so.4(+0x54c290)[0x456f290]
./libQtWebKit.so.4(+0x547cc3)[0x456acc3]
./libQtWebKit.so.4(+0x6fd155)[0x4720155]
./libQtWebKit.so.4(+0x6fd83e)[0x472083e]
./libQtCore.so.4(_ZN11QMetaObject8metacallEP7QObjectNS_4CallEiPPv+0x3f)[0x94e5a7]
./libQtCore.so.4(_ZN14QMetaCallEvent13placeMetaCallEP7QObject+0x24)[0x9565ec]
./libQtCore.so.4(_ZN7QObject5eventEP6QEvent+0x185)[0x95703d]
./libQtGui.so.4(_ZN19QApplicationPrivate13notify_helperEP7QObjectP6QEvent+0xa0)[0x1103e20]
./libQtGui.so.4(_ZN12QApplication6notifyEP7QObjectP6QEvent+0x22e)[0x110d962]
./libQtCore.so.4(_ZN16QCoreApplication14notifyInternalEP7QObjectP6QEvent+0x70)[0x948d50]
./libQtCore.so.4(_ZN23QCoreApplicationPrivate16sendPostedEventsEP7QObjectiP11QThreadData+0x22d)[0x949989]
./libQtCore.so.4(_ZN20QEventDispatcherUNIX13processEventsE6QFlagsIN10QEventLoop17ProcessEventsFlagEE+0x37)[0x96e94b]
./libQtGui.so.4(+0x1d3ca4)[0x1198ca4]
./libQtCore.so.4(_ZN10QEventLoop13processEventsE6QFlagsINS_17ProcessEventsFlagEE+0x47)[0x947fbf]
./libQtCore.so.4(_ZN10QEventLoop4execE6QFlagsINS_17ProcessEventsFlagEE+0xff)[0x948223]
./libQtCore.so.4(_ZN16QCoreApplication4execEv+0x9d)[0x949c05]
./libQtGui.so.4(_ZN12QApplication4execEv+0x25)[0x11037a1]
./libgoogleearth_free.so(_ZN5earth6client11Application3runEv+0x4bc)[0xba150c]
./libgoogleearth_free.so(earthmain+0x27d)[0xb9573d]
./googleearth-bin(_init+0x122)[0x80486c2]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x126bd6]
./googleearth-bin(_init+0x91)[0x8048631]


```

No help was found on google!!!

---

### Post by Heero_Yuy_X on 2010-09-01
Same Problem here, seems everybody abandoned the whole thing ! :confused:

O well, I have to go to Microsoft's Windows, to get that working !! Thanks alot Google and Ubuntu ! :(

---

### Post by juliobahar on 2010-09-01
I agree quite a big disappointment!!!

---

### Post by amarintj1986 on 2011-11-03
This is the fix, is really simple:

[http://www.webupd8.org/2010/10/fix-google-earth-crashing-on-startup-in.html](http://www.webupd8.org/2010/10/fix-google-earth-crashing-on-startup-in.html)

Regards,

---

