---
title: "VLC Crashes"
date: 2007-04-22
forum: Multimedia &amp; Video
---

### Post by lukemack on 2007-04-22
Hi,

I have installed VLC media player and it quits when I try to open any file. I'm running Ubuntu 6.10 server. I also have gxine and m-player installed.

when running vlc from the terminal and opening a file (any format - wmv, mov, mpeg, dvd) i get:

luke@DeepThought:~$ sudo vlc
Password:
VLC media player 0.8.6 Janus
starting VLC root wrapper... using UID 1000 (luke)
GTK Accessibility Module initialized
[00000292] access_file access error: seeking too far
[00000338] main private error: option glx-shm does not exist
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  143 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  52
  Current serial number in output stream:  52
luke@DeepThought:~$ 


any ideas on how to resolve?

thanks,

<L>

---

### Post by dmizer on 2007-08-23
i know this is ancient but it was the first thread to pop up under a google search for:
'vlc option glx-shm does not exist'

so i thought i'd post the answer, because i just ran into the problem and resolved it.  it is because of running beryl.

open vlc (no video, just open it as a program), and do the following:
click - settings > preferences > video
in the bottom right, put a checkmark in "advanced options"
then click - output modules
and change "video output module" from "opengl video output" to "x11 video output".

note:
if you later want to run vlc while in using beryl, you may have to change this setting back to opengl.

---

### Post by Dark Star on 2007-08-23
Hey why my Video appear black in CF.. any idea ? No output in default movie player :(

---

### Post by Bablefish on 2007-08-23
I know what your going through it is really a matter of codecs for the DVDs, MPegs, and wmvs. I reccomend Automatrix for that. But I hate to tell you but it's the truth there is no way to play movs on Linux. I have tried every fix there is and nothing works period.

---

### Post by raijinsetsu on 2007-08-23
Why are you sudoing VLC? That doesn't make sense.
That could be your problem... try it without sudo.

---

### Post by wolfen69 on 2007-08-23
everything works on my machine. i have yet to try a media format that i can't play.

---

### Post by sulemankm on 2008-05-27
I'm running ubuntu 8.04.  VLC crashes on startup even if I'm not opening a media file. Just trying to run vlc crashes it.  This problem is persisting since I upgraded to Gutsy Gibbon (7.10) and it has since then made even into hardy.

Here is the output of VLC.


VLC media player 0.8.6e Janus
*** glibc detected *** vlc: double free or corruption (out): 0x08396da0 ***
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6[0xb7be6a85]
/lib/tls/i686/cmov/libc.so.6(cfree+0x90)[0xb7bea4f0]
/usr/lib/libglib-2.0.so.0(g_free+0x31)[0xb6b228b1]
/usr/lib/libwx_gtk2u_core-2.6.so.0[0xb746b950]
/usr/lib/libwx_gtk2u_core-2.6.so.0(_ZN8wxButton10SetDefaultEv+0x76)[0xb746ba36]
/usr/lib/vlc/gui/libwxwidgets_plugin.so(_ZN5wxvlc8MessagesC1EP13intf_thread_tP8wxWindow+0x5d2)[0xb78f1162]
======= Memory map: ========
08048000-08049000 r-xp 00000000 08:07 747917     /usr/bin/vlc
08049000-0804a000 rw-p 00000000 08:07 747917     /usr/bin/vlc
0804a000-08476000 rw-p 0804a000 00:00 0          [heap]
aec00000-aec21000 rw-p aec00000 00:00 0 
aec21000-aed00000 ---p aec21000 00:00 0 
aed8c000-aed90000 r-xp 00000000 08:07 280799     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
aed90000-aed91000 rw-p 00003000 08:07 280799     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-png.so
aed92000-aed9c000 r--p 00000000 08:07 537332     /usr/local/share/icons/hicolor/icon-theme.cache
aed9c000-af76a000 r--p 00000000 08:07 278616     /usr/share/icons/hicolor/icon-theme.cache
af76a000-b0881000 r--p 00000000 08:07 758        /usr/share/icons/crystalsvg/icon-theme.cache
b0881000-b0ade000 r--p 00000000 08:07 700821     /usr/share/icons/Tango/icon-theme.cache
b0ade000-b12b0000 r--p 00000000 08:07 35750      /usr/share/icons/gnome/icon-theme.cache
b12b0000-b135b000 r--p 00000000 08:07 532906     /usr/share/icons/Tangerine/icon-theme.cache
b135b000-b145f000 rw-p b135b000 00:00 0 
b145f000-b14f0000 r--p 00000000 08:07 60455      /usr/share/fonts/truetype/ttf-dejavu/DejaVuSans.ttf
b14f0000-b1550000 rw-s 00000000 00:09 1703967    /SYSV00000000 (deleted)
b1550000-b15b0000 rw-s 00000000 00:09 1671198    /SYSV00000000 (deleted)
b15b0000-b15b6000 r-xp 00000000 08:07 52479      /usr/lib/libgailutil.so.18.0.1
b15b6000-b15b7000 rw-p 00006000 08:07 52479      /usr/lib/libgailutil.so.18.0.1
b15b7000-b15e6000 r-xp 00000000 08:07 568733     /usr/lib/libgnomecanvas-2.so.0.2001.0
b15e6000-b15e7000 rw-p 0002f000 08:07 568733     /usr/lib/libgnomecanvas-2.so.0.2001.0
b15e7000-b1625000 r-xp 00000000 08:07 109218     /usr/lib/libgnomeprintui-2-2.so.0.1.0
b1625000-b1627000 rw-p 0003d000 08:07 109218     /usr/lib/libgnomeprintui-2-2.so.0.1.0
b1627000-b163c000 r-xp 00000000 08:07 59217      /usr/lib/libart_lgpl_2.so.2.3.20
b163c000-b163d000 rw-p 00014000 08:07 59217      /usr/lib/libart_lgpl_2.so.2.3.20
b163d000-b16a0000 r-xp 00000000 08:07 266234     /usr/lib/libgnomeprint-2-2.so.0.1.0
b16a0000-b16a2000 rw-p 00063000 08:07 266234     /usr/lib/libgnomeprint-2-2.so.0.1.0
b16b4000-b16b6000 r-xp 00000000 08:07 140164     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b16b6000-b16b7000 rw-p 00001000 08:07 140164     /usr/lib/pango/1.6.0/modules/pango-basic-fc.so
b16b7000-b16ba000 rw-s 00000000 00:09 1736736    /SYSV00000000 (deleted)
b16ba000-b16c0000 r-xp 00000000 08:07 309945     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b16c0000-b16c1000 rw-p 00005000 08:07 309945     /usr/lib/gtk-2.0/2.10.0/loaders/libpixbufloader-xpm.so
b16c1000-b16c7000 r--s 00000000 08:07 530300     /var/cache/fontconfig/945677eb7aeaf62f1d50efc3fb3ec7d8-x86.cache-2
b16c7000-b16ca000 r--s 00000000 08:07 445393     /var/cache/fontconfig/e383d7ea5fbe662a33d9b44caf393297-x86.cache-2
b16ca000-b16cb000 r--s 00000000 08:07 445382     /var/cache/fontconfig/fd9505950c048a77dc4b710eb6a628ed-x86.cache-2
b16cb000-b16cd000 r--s 00000000 08:07 445380     /var/cache/fontconfig/ddc79d3ea06a7c6ffa86ede85f3bb5df-x86.cache-2
b16cd000-b16ce000 r--s 00000000 08:07 386020     /var/cache/fontconfig/5bc99d13c41710fd4d04a3be3075ea0a-x86.cache-2
b16ce000-b16cf000 r--s 00000000 08:07 229194     /var/cache/fontconfig/e3fa16a14183b06aa45b3e009278fd14-x86.cache-2
b16cf000-b16d1000 r--s 00000000 08:07 613065     /var/cache/fontconfig/52728cdc49031813f272d4aa720952ff-x86.cache-2
b16d1000-b16d2000 r--s 00000000 08:07 172081     /var/cache/fontconfig/e7071f4a29fa870f4323321c154eba04-x86.cache-2
b16d2000-b16d3000 r--s 00000000 08:07 142946     /var/cache/fontconfig/9620031e5ef3d9f8db76a0a1427e3349-x86.cache-2
b16d3000-b16d4000 r--s 00000000 08:07 139945     /var/cache/fontconfig/a2ab74764b07279e7c36ddb1d302cf26-x86.cache-2
b16d4000-b16d5000 r--s 00000000 08:07 114920     /var/cache/fontconfig/cf9cbdda15ec67a08a35a9edc14b8c27-x86.cache-2
b16d5000-b16d9000 r--s 00000000 08:07 114839     /var/cache/fontconfig/921a30a17f0be15c70ac14043cb7a739-x86.cache-2
b16d9000-b16da000 r--s 00000000 08:07 114834     /var/cache/fontconfig/e4d1462cb5eaf1246b0d92281b502011-x86.cache-2
b16da000-b16db000 r--s 00000000 08:07 114702     /var/cache/fontconfig/c69f04ab05004e31a6d5e715764f16d8-x86.cache-2
b16db000-b16dc000 r--s 00000000 08:07 114697     /var/cache/fontconfig/4c73fe0c47614734b17d736dbde7580a-x86.cache-2
b16dc000-b16de000 r--s 00000000 08:07 114681     /var/cache/fontconfig/646addb8444faa74ee138aa00ab0b6a0-x86.cache-2
b16de000-b16e1000 r--s 00000000 08:07 113709     /var/cache/fontconfig/a755afe4a08bf5b97852ceb7400b47bc-x86.cache-2
b16e1000-b16e3000 r--s 00000000 08:07 113687     /var/cache/fontconfig/20bd79ad97094406f7d1b9654bfbd926-x86.cache-2
b16e3000-b16e4000 r--s 00000000 08:07 99694      /var/cache/fontconfig/32fc3cbe01df6a30798854a2c93eb444-x86.cache-2
b16e4000-b16e6000 r--s 00000000 08:07 99692      /var/cache/fontconfig/9c0624108b9a2ae8552f664125be8356-x86.cache-2
b16e6000-b16ed000 r--s 00000000 08:07 99688      /var/cache/fontconfig/6d41288fd70b0be22e8c3a91e032eec0-x86.cache-2
b16ed000-b16f0000 r--s 00000000 08:07 99684      /var/cache/fontconfig/de156ccd2eddbdc19d37a45b8b2aac9c-x86.cache-2
b16f0000-b16f2000 r--s 00000000 08:07 90645      /var/cache/fontconfig/da1bd5ca8443ffe22927a23ce431d198-x86.cache-2
b16f2000-b16fa000 r--s 00000000 08:07 88092      /var/cache/fontconfig/e3de0de479f42330eadf588a55fb5bf4-x86.cache-2
b16fa000-b1702000 r--s 00000000 08:07 88076      /var/cache/fontconfig/0f34bcd4b6ee430af32735b75db7f02b-x86.cache-2
b1702000-b1724000 r--s 00000000 08:07 71185      /var/cache/fontconfig/365b55f210c0a22e9a19e35191240f32-x86.cache-2
b1724000-b1727000 r--s 00000000 08:07 71019      /var/cache/fontconfig/de9486f0b47a4d768a594cb4198cb1c6-x86.cache-2
b1727000-b172e000 r--s 00000000 08:07 63777      /var/cache/fontconfig/d52a8644073d54c13679302ca1180695-x86.cache-2
b172e000-b1733000 r--s 00000000 08:07 63606      /var/cache/fontconfig/105b9c7e6f0a4f82d8c9b6e39c52c6f9-x86.cache-2
b1733000-b1814000 r--p 00000000 08:07 464986     /usr/lib/locale/en_US.utf8/LC_COLLATE
b1814000-b1815000 ---p b1814000 00:00 0 
b1815000-b2015000 rwxp b1815000 00:00 0 
b2015000-b2016000 ---p b2015000 00:00 0 
b2016000-b2816000 rwxp b2016000 00:00 0 
b2816000-b2817000 ---p b2816000 00:00 0 
b2817000-b3017000 rwxp b2817000 00:00 0 
b3017000-b3018000 ---p b3017000 00:00 0 
b3018000-b3818000 rwxp b3018000 00:00 0 
b3818000-b3819000 ---p b3818000 00:00 0 
b3819000-b4019000 rwxp b3819000 00:00 0 
b4019000-b4028000 r-xp 00000000 08:07 28714      /usr/lib/libjack.so.0.0.28
b4028000-b402a000 rw-p 0000f000 08:07 28714      /usr/lib/libjack.so.0.0.28
b402a000-b4032000 rw-p b402a000 00:00 0 
b4034000-b4035000 r--s 00000000 08:07 83106      /var/cache/fontconfig/4794a0821666d79190d59a36cb4f44b5-x86.cache-2
b4035000-b4038000 r--s 00000000 08:07 60754      /var/cache/fontconfig/6386b86020ecc1ef9690bb720a13964f-x86.cache-2
b4038000-b4043000 r--s 00000000 08:07 57651      /var/cache/fontconfig/089dead882dea3570ffc31a9898cfb69-x86.cache-2
b4043000-b404a000 r--s 00000000 08:07 28415      /var/cache/fontconfig/e13b20fdb08344e0e664864cc2ede53d-x86.cache-2
b404a000-b404c000 r--s 00000000 08:07 530301     /var/cache/fontconfig/88003bed7f466853056f4a2e5ce7e0f6-x86.cache-2
b404c000-b404e000 r--s 00000000 08:07 56942      /var/cache/fontconfig/7ef2298fde41cc6eeb7af42e48b7d293-x86.cache-2
b404e000-b4050000 r-xp 00000000 08:07 747977     /usr/lib/vlc/audio_output/libaout_file_plugin.so
b4050000-b4051000 rw-p 00001000 08:07 747977     /usr/lib/vlc/audio_output/libaout_file_plugin.so
b4051000-b4054000 r-xp 00000000 08:07 124488     /lib/libcap.so.1.10
b4054000-b4055000 rw-p 00002000 08:07 124488     /lib/libcap.so.1.10
b4055000-b40a2000 r-xp 00000000 08:07 291975     /usr/lib/libpulse.so.0.4.1
b40a2000-b40a3000 rw-p 0004c000 08:07 291975     /usr/lib/libpulse.so.0.4.1
b40a3000-b40b4000 r-xp 00000000 08:07 41208      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b40b4000-b40b5000 rw-p 00011000 08:07 41208      /usr/lib/gtk-2.0/2.10.0/engines/libubuntulooks.so
b40b5000-b40b7000 r-xp 00000000 08:07 747978     /usr/lib/vlc/audio_output/libjack_pluAborted

---

