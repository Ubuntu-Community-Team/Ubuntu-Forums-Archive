---
title: "MPlayer &amp; VLC disappear with &quot;House....avi&quot; (gutsy)"
date: 2007-11-02
forum: Multimedia &amp; Video
---

### Post by bliffle on 2007-11-02
On my #2 system (IBM TP570 with 256mb RAM) with "gutsy", both MPlayer and VLC will simply disappear when I try to run an AVI episode of "House" from BitTorrent. Both drag'n drop and Browse fail.

Of course, it works on my Good 'ol Reliable sytem #1 (IBM T40) with "feisty".

So, I explored this forum and google and got to this website:
```
http://www.mplayerhq.hu/design7/dload.html#binary_codecs
```

went down to this entry:
```
Linux x86 20071007  	 [ CH  | HU  | US  | US  | KR  | DE  ]  	 [ CH  | HU  | US  | KR  | FR  | DE  | DE2  ]  	 [ BT  ]

```
I selected the "FR" entry, of course, because the French are very good cheaters and they have little compunction.

DLed it to my Desktop and unpacked at:
```
/home/john/Desktop/win32codecs/essential-20071007
```

Here's part of the README file from there:
```
"Put the files contained in this archive in a directory where MPlayer will find
them. The default directory is /usr/local/lib/codecs/ ($prefix/lib/codecs/) if
you are compiling from source, but you can change that value by passing the
'--with-codecsdir' option to './configure'.

If you use a prebuilt MPlayer package it will most likely be /usr/lib/codecs,
see the documentation of your package for details."
```

I put the files as directed and listed them:
```
/usr/local/lib/codecs$ ls -l
total 23076
-rw-r--r-- 1 root root   61952 2007-11-02 11:30 acelpdec.ax
-rw-r--r-- 1 root root   38912 2007-11-02 11:30 alf2cd.acm
-rw-r--r-- 1 root root  118784 2007-11-02 11:30 aslcodec_dshow.dll
-rw-r--r-- 1 root root   92160 2007-11-02 11:30 AvidQTAVUICodec.qtx
-rw-r--r-- 1 root root   76800 2007-11-02 11:30 BeHereiVideo.qtx
-rw-r--r-- 1 root root  312832 2007-11-02 11:30 CLRVIDDC.DLL
-rw-r--r-- 1 root root  135168 2007-11-02 11:30 clrviddd.dll
-rwxr-xr-x 1 root root   42956 2007-11-02 11:30 cook.so
-rw-r--r-- 1 root root   81920 2007-11-02 11:30 CtWbJpg.DLL
-rw-r--r-- 1 root root   88464 2007-11-02 11:30 DECVW_32.DLL
-rwxr-xr-x 1 root root  321008 2007-11-02 11:30 drvc.so
-rwxr-xr-x 1 root root   69648 2007-11-02 11:30 dspr.so.6.0
-rw-r--r-- 1 root root  199680 2007-11-02 11:30 iac25_32.ax
-rw-r--r-- 1 root root  307200 2007-11-02 11:30 icmw_32.dll
-rw-r--r-- 1 root root  739328 2007-11-02 11:30 ir41_32.dll
-rw-r--r-- 1 root root  755200 2007-11-02 11:30 ir50_32.dll
-rw-r--r-- 1 root root  225280 2007-11-02 11:30 ivvideo.dll
-rw-r--r-- 1 root root   90112 2007-11-02 11:30 jp2avi.dll
-rw-r--r-- 1 root root  245760 2007-11-02 11:30 LCMW2.dll
-rw-r--r-- 1 root root   81920 2007-11-02 11:30 LCODCCMW2E.dll
-rw-r--r-- 1 root root   33040 2007-11-02 11:30 lhacm.acm
-rw-r--r-- 1 root root  204800 2007-11-02 11:30 lsvxdec.dll
-rw-r--r-- 1 root root  422912 2007-11-02 11:30 m3jp2k32.dll
-rw-r--r-- 1 root root   57344 2007-11-02 11:30 mi-sc4.acm
-rw-r--r-- 1 root root  167696 2007-11-02 11:30 msh261.drv
-rw-r--r-- 1 root root  424960 2007-11-02 11:30 msms001.vwp
-rw-r--r-- 1 root root   76112 2007-11-02 11:30 msscds32.ax
-rw-r--r-- 1 root root   49664 2007-11-02 11:30 nsrt2432.acm
-rw-r--r-- 1 root root   34304 2007-11-02 11:30 qpeg32.dll
-rw-r--r-- 1 root root  225280 2007-11-02 11:30 qtmlClient.dll
-rw-r--r-- 1 root root  563200 2007-11-02 11:30 QuickTimeEssentials.qtx
-rw-r--r-- 1 root root  904704 2007-11-02 11:30 QuickTimeInternetExtras.qtx
-rw-r--r-- 1 root root 4544512 2007-11-02 11:30 QuickTime.qts
-rw-r--r-- 1 root root    1037 2007-11-02 11:30 README
-rw-r--r-- 1 root root  299008 2007-11-02 11:30 rt32dcmp.dll
-rwxr-xr-x 1 root root   62896 2007-11-02 11:30 sipr.so.6.0
-rwxr-xr-x 1 root root   22472 2007-11-02 11:30 tokf.so.6.0
-rwxr-xr-x 1 root root   59696 2007-11-02 11:30 tokr.so.6.0
-rw-r--r-- 1 root root  573440 2007-11-02 11:30 tvqdec.dll
-rw-r--r-- 1 root root   76800 2007-11-02 11:30 VDODEC32.dll
-rw-r--r-- 1 root root   82432 2007-11-02 11:30 vdowave.drv
-rwxr-xr-x 1 root root  319480 2007-11-02 11:30 vid_3ivX.xa
-rw-r--r-- 1 root root  211968 2007-11-02 11:30 ViVD2.dll
-rw-r--r-- 1 root root  122880 2007-11-02 11:30 vivog723.acm
-rw-r--r-- 1 root root   56320 2007-11-02 11:30 voxmsdec.ax
-rw-r--r-- 1 root root  466944 2007-11-02 11:30 vp4vfw.dll
-rw-r--r-- 1 root root  438272 2007-11-02 11:30 vp6vfw.dll
-rw-r--r-- 1 root root  626688 2007-11-02 11:30 vp7vfw.dll
-rw-r--r-- 1 root root   49152 2007-11-02 11:30 vssh264core.dll
-rw-r--r-- 1 root root  421888 2007-11-02 11:30 vssh264dec.dll
-rw-r--r-- 1 root root   98304 2007-11-02 11:30 vssh264.dll
-rw-r--r-- 1 root root  454656 2007-11-02 11:30 vsshdsd.dll
-rw-r--r-- 1 root root  706696 2007-11-02 11:30 vsslight.dll
-rw-r--r-- 1 root root  167936 2007-11-02 11:30 vsswlt.dll
-rw-r--r-- 1 root root  409720 2007-11-02 11:30 wma9dmod.dll
-rw-r--r-- 1 root root  410216 2007-11-02 11:30 wmadmod.dll
-rw-r--r-- 1 root root  773368 2007-11-02 11:30 wmsdmod.dll
-rw-r--r-- 1 root root  486504 2007-11-02 11:30 wmspdmod.dll
-rw-r--r-- 1 root root  807032 2007-11-02 11:31 wmv9dmod.dll
-rw-r--r-- 1 root root 1181944 2007-11-02 11:31 wmvadvd.dll
-rw-r--r-- 1 root root  807528 2007-11-02 11:31 wmvdmod.dll
-rw-r--r-- 1 root root   93184 2007-11-02 11:31 wnvwinx.dll
-rw-r--r-- 1 root root 1184984 2007-11-02 11:31 wvc1dmod.dll
-rw-r--r-- 1 root root   35840 2007-11-02 11:31 xanlib.dll
```

Tried both VLC (my fave) and MPlayer (the Gold Standard, apparently) and both disappeared when I tried to view the movie.

Any ideas?

Different win32codecs?

Different directory?

Further test?

---

### Post by g4ry.l33 on 2007-11-03
I have the same problem when I try to play mpg's or wmv's. I tried Medibuntu with no luck. :confused:

---

### Post by g4ry.l33 on 2007-11-04
UPDATE!

I forgot.... my intel graphics card is on the compiz Black List. If I turn off Desktop Effects
and all is good.

        :guitar:

---

### Post by bliffle on 2007-11-04
I'm not running 'compiz', that I know of. I just checked 'compiz -?' and it said:

```
 compiz -?
/usr/bin/compiz.real: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.
/usr/bin/compiz.real: No manageable screens found on display :0.0
Window manager warning: Screen 0 on display ":0.0" already has a window manager; try using the --replace option to replace the current window manager.

```

---

