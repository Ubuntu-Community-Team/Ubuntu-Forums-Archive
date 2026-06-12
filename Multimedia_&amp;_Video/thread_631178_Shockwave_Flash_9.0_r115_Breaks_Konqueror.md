---
title: "Shockwave Flash 9.0 r115 ***Breaks Konqueror***"
date: 2007-12-04
forum: Multimedia &amp; Video
---

### Post by pointfivezero on 2007-12-04
I have installed the latest update of Adobe Flash Player for Linux on my system (Kubuntu 7.10 Linux 2.6.22-14-generic / KDE 3.5.8 / Konqueror 3.5.8), however this has removed konquerors' ability to load swf files and crashes nspluginwrapper.

When started from a konsole and after opening a swf file:
```

$ konqueror

(process:10052): Gtk-CRITICAL **: gtk_clipboard_get_for_display: assertion `display != NULL' failed
Adobe Flash Player: gtk_clipboard_get(GDK_SELECTION_PRIMARY); failed. Trying to call gtk_init(0,0);

```

And then closing the tab:

```

X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  10
  Minor opcode:  0
  Resource id:  0x2a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  7
  Minor opcode:  0
  Resource id:  0x2a00008
X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  25
  Minor opcode:  0
  Resource id:  0x2a00008
KCrash: Application 'nspluginviewer' crashing...

```

With the following crash handler Backtrace:

```

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1208408384 (LWP 10414)]
[New Thread -1253942384 (LWP 10423)]
[New Thread -1245549680 (LWP 10422)]
[New Thread -1237156976 (LWP 10421)]
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[KCrash handler]
#6  0x4f89d1b7 in XtRemoveTimeOut () from /usr/lib/libXt.so.6
#7  0xb74d7db1 in ?? () from /home/pxn7/.mozilla/plugins/libflashplayer.so
#8  0xb74cd338 in ?? () from /home/pxn7/.mozilla/plugins/libflashplayer.so
#9  0xb74c6181 in ?? () from /home/pxn7/.mozilla/plugins/libflashplayer.so
#10 0xb74ca937 in ?? () from /home/pxn7/.mozilla/plugins/libflashplayer.so
#11 0x080b06a8 in ?? ()
#12 0xbfe20048 in ?? ()
#13 0xbfe20018 in ?? ()
#14 0x42a67d81 in operator delete () from /usr/lib/libstdc++.so.6
#15 0x0805b62f in NSPluginInstance::destroy ()
#16 0x0805d78d in NSPluginInstance::~NSPluginInstance ()
#17 0x4ff4fe50 in QGList::remove () from /usr/lib/libqt-mt.so.3
#18 0x0805652f in NSPluginClass::timer ()
#19 0x080565c1 in NSPluginInstance::shutdown ()
#20 0x080593b9 in NSPluginInstanceIface::process ()
#21 0x4139d6b7 in DCOPClient::receive () from /usr/lib/libDCOP.so.4
#22 0x4139ea14 in ?? () from /usr/lib/libDCOP.so.4
#23 0x080a5160 in ?? ()
#24 0xbfe203a4 in ?? ()
#25 0xbfe2039c in ?? ()
#26 0xbfe20394 in ?? ()
#27 0xbfe2038c in ?? ()
#28 0xbfe20384 in ?? ()
#29 0xbfe2037c in ?? ()
#30 0xbfe2033c in ?? ()
#31 0xbfe203ac in ?? ()
#32 0xbfe203a4 in ?? ()
#33 0xbfe2039c in ?? ()
#34 0xbfe20394 in ?? ()
#35 0xbfe2038c in ?? ()
#36 0xbfe20384 in ?? ()
#37 0xbfe2037c in ?? ()
#38 0x00000010 in ?? ()
#39 0xbfe20354 in ?? ()
#40 0x08062da8 in vtable for QMemArray<char> ()
#41 0x0000007d in ?? ()
#42 0x00f4f3d0 in ?? ()
#43 0x010e9901 in ?? ()
#44 0x000000b6 in ?? ()
#45 0x00000002 in ?? ()
#46 0x080b0ba0 in ?? ()
#47 0x0809fe08 in ?? ()
#48 0x080a5160 in ?? ()
#49 0x426b413c in ?? () from /lib/tls/i686/cmov/libc.so.6
#50 0x00000001 in ?? ()
#51 0x00000047 in ?? ()

```

If anyone is having similar issues or anyone can suggestions, please post them here!

Thanks in advance.

Note: Flash Player 9.0 Update 3 (Final) has been released and worked fine under firefox on the same system

---

### Post by tim71 on 2007-12-04
How did you make this installation?

I converted the rpm with alien and got it installed...and same here - it works with Firefox and Opera, but not with Konqueror.

---

### Post by FuturePilot on 2007-12-04
Yep, not working here with Konqueror either. Works with Firefox though.

---

### Post by pointfivezero on 2007-12-04
> **tim71 said:**
> How did you make this installation?

I converted the rpm with alien and got it installed...and same here - it works with Firefox and Opera, but not with Konqueror.

I installed from [.tar.gz]("http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz") and ran the installation script.

 It shows up as the correct version in about:plugins in both firefox and konqueror


Cheers

---

### Post by pointfivezero on 2007-12-04
[Bug report submitted]("https://bugs.launchpad.net/bugs/174343")

---

### Post by emuman on 2007-12-06
Is there a mirror for the old 9.0.48 Version?

---

### Post by pointfivezero on 2007-12-06
> **emuman said:**
> Is there a mirror for the old 9.0.48 Version?

Yes, there are [older versions for download]("http://www.adobe.com/go/tn_14266"), it is quite large at 61.8MB but it does provide all 9.0 revisions as a single download.

---

### Post by Anezthetikal on 2007-12-10
I was having the same trouble with the Flash Player.  I went ahead and downloaded the 9r48 version of the player and placed it into another folder that only Konqueror could use to allocate plugins.  It works just fine.  So Firefox has his own plugin of the 9r115 and Konqueror has her own with the 9r48.  Horrible workaround, but a workaround, nonetheless.

---

### Post by amd77j on 2007-12-10
> **pointfivezero said:**
> Yes, there are [older versions for download]("http://www.adobe.com/go/tn_14266"), it is quite large at 61.8MB but it does provide all 9.0 revisions as a single download.

Thanks for the information. The latest flash version 9_115 was too sluggish/choppy on my firefox browser. I am running xubuntu on an older system with only 128MB RAM and only 11MB RAM on my video card:). That said, I had NEVER had this problem before the latest flash upgrade. I simply used the link you provided and reinstalled version 9r48. Everything is back to normal after that reversion back to the tried and true.

Thanks again!:guitar:

---

### Post by -error on 2007-12-21
i wonder is there a chance that patch, named in that thread can creep into kubuntu 7.10?

---

