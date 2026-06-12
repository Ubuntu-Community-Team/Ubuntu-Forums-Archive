---
title: "GNOME Wave Cleaner keeps crashing..."
date: 2010-01-30
forum: Multimedia Software
---

### Post by fredbird67 on 2010-01-30
...anytime I try to open a file, and it's a file I've already converted to WAV.  It's a recording of an old Haven of Rest Quartet album, "Glory to His Name", and if possible, I'd like to get all the pops and clicks edited out before I burn it to a CD.  I've seen GNOME Wave Cleaner mentioned on here before, so I tried it, but whenever I open a file, it crashes.  I then tried entering the program name in the terminal.  When it crashed, I got the following:

```

00110000-00168000 r-xp 00000000 08:01 3139       /usr/lib/libgnomevfs-2.so.0.2400.2
00168000-0016a000 r--p 00057000 08:01 3139       /usr/lib/libgnomevfs-2.so.0.2400.2
0016a000-0016c000 rw-p 00059000 08:01 3139       /usr/lib/libgnomevfs-2.so.0.2400.2
0016c000-001fe000 r-xp 00000000 08:01 10627      /usr/lib/libgdk-x11-2.0.so.0.1800.3
001fe000-00200000 r--p 00092000 08:01 10627      /usr/lib/libgdk-x11-2.0.so.0.1800.3
00200000-00201000 rw-p 00094000 08:01 10627      /usr/lib/libgdk-x11-2.0.so.0.1800.3
00201000-00294000 r-xp 00000000 08:01 10624      /usr/lib/libgio-2.0.so.0.2200.3
00294000-00295000 r--p 00092000 08:01 10624      /usr/lib/libgio-2.0.so.0.2200.3
00295000-00296000 rw-p 00093000 08:01 10624      /usr/lib/libgio-2.0.so.0.2200.3
00296000-00297000 rw-p 00000000 00:00 0 
00297000-002dd000 r-xp 00000000 08:01 3545       /usr/lib/libpango-1.0.so.0.2600.0
002dd000-002de000 r--p 00045000 08:01 3545       /usr/lib/libpango-1.0.so.0.2600.0
002de000-002df000 rw-p 00046000 08:01 3545       /usr/lib/libpango-1.0.so.0.2600.0
002e0000-00329000 r-xp 00000000 08:01 2633       /usr/lib/libORBit-2.so.0.1.0
00329000-00331000 r--p 00049000 08:01 2633       /usr/lib/libORBit-2.so.0.1.0
00331000-00333000 rw-p 00051000 08:01 2633       /usr/lib/libORBit-2.so.0.1.0
00333000-0035e000 r-xp 00000000 08:01 2996       /usr/lib/libfontconfig.so.1.3.0
0035e000-0035f000 r--p 0002a000 08:01 2996       /usr/lib/libfontconfig.so.1.3.0
0035f000-00360000 rw-p 0002b000 08:01 2996       /usr/lib/libfontconfig.so.1.3.0
00360000-00367000 r-xp 00000000 08:01 316567     /lib/tls/i686/cmov/librt-2.10.1.so
00367000-00368000 r--p 00006000 08:01 316567     /lib/tls/i686/cmov/librt-2.10.1.so
00368000-00369000 rw-p 00007000 08:01 316567     /lib/tls/i686/cmov/librt-2.10.1.so
00369000-0037e000 r-xp 00000000 08:01 314347     /lib/tls/i686/cmov/libpthread-2.10.1.so
0037e000-0037f000 r--p 00014000 08:01 314347     /lib/tls/i686/cmov/libpthread-2.10.1.so
0037f000-00380000 rw-p 00015000 08:01 314347     /lib/tls/i686/cmov/libpthread-2.10.1.so
00380000-00382000 rw-p 00000000 00:00 0 
00384000-003b7000 r-xp 00000000 08:01 3123       /usr/lib/libgnomecanvas-2.so.0.2600.0
003b7000-003b8000 r--p 00032000 08:01 3123       /usr/lib/libgnomecanvas-2.so.0.2600.0
003b8000-003b9000 rw-p 00033000 08:01 3123       /usr/lib/libgnomecanvas-2.so.0.2600.0
003b9000-00430000 r-xp 00000000 08:01 17140      /usr/lib/libcairo.so.2.10800.8
00430000-00432000 r--p 00076000 08:01 17140      /usr/lib/libcairo.so.2.10800.8
00432000-00433000 rw-p 00078000 08:01 17140      /usr/lib/libcairo.so.2.10800.8
00433000-0044f000 r-xp 00000000 08:01 2875       /usr/lib/libdbus-glib-1.so.2.1.0
0044f000-00450000 r--p 0001b000 08:01 2875       /usr/lib/libdbus-glib-1.so.2.1.0
00450000-00451000 rw-p 0001c000 08:01 2875       /usr/lib/libdbus-glib-1.so.2.1.0
00451000-00453000 r-xp 00000000 08:01 1471       /usr/lib/libavahi-glib.so.1.0.1
00453000-00454000 r--p 00001000 08:01 1471       /usr/lib/libavahi-glib.so.1.0.1
00454000-00455000 rw-p 00002000 08:01 1471       /usr/lib/libavahi-glib.so.1.0.1
00455000-00457000 r-xp 00000000 08:01 316570     /lib/tls/i686/cmov/libutil-2.10.1.so
00457000-00458000 r--p 00001000 08:01 316570     /lib/tls/i686/cmov/libutil-2.10.1.so
00458000-00459000 rw-p 00002000 08:01 316570     /lib/tls/i686/cmov/libutil-2.10.1.so
00459000-0045d000 r-xp 00000000 08:01 2637       /usr/lib/libORBitCosNaming-2.so.0.1.0
0045d000-0045e000 r--p 00003000 08:01 2637       /usr/lib/libORBitCosNaming-2.so.0.1.0
0045e000-0045f000 rw-p 00004000 08:01 2637       /usr/lib/libORBitCosNaming-2.so.0.1.0
00460000-004c5000 r-xp 00000000 08:01 2779       /usr/lib/libbonoboui-2.so.0.0.0
004c5000-004c6000 r--p 00064000 08:01 2779       /usr/lib/libbonoboui-2.so.0.0.0
004c6000-004c8000 rw-p 00065000 08:01 2779       /usr/lib/libbonoboui-2.so.0.0.0
004c8000-004f7000 r-xp 00000000 08:01 3023       /usr/lib/libgconf-2.so.4.1.5
004f7000-004f8000 r--p 0002e000 08:01 3023       /usr/lib/libgconf-2.so.4.1.5
004f8000-004fa000 rw-p 0002f000 08:01 3023       /usr/lib/libgconf-2.so.4.1.5
004fa000-00504000 r-xp 00000000 08:01 3895       /usr/lib/libavahi-common.so.3.5.1
00504000-00505000 r--p 00009000 08:01 3895       /usr/lib/libavahi-common.so.3.5.1
00505000-00506000 rw-p 0000a000 08:01 3895       /usr/lib/libavahi-common.so.3.5.1
00506000-00508000 r-xp 00000000 08:01 2658       /usr/lib/libXcomposite.so.1.0.0
00508000-00509000 r--p 00001000 08:01 2658       /usr/lib/libXcomposite.so.1.0.0
00509000-0050a000 rw-p 00002000 08:01 2658       /usr/lib/libXcomposite.so.1.0.0
0050c000-00568000 r-xp 00000000 08:01 2775       /usr/lib/libbonobo-2.so.0.0.0
00568000-00569000 ---p 0005c000 08:01 2775       /usr/lib/libbonobo-2.so.0.0.0
00569000-0056c000 r--p 0005c000 08:01 2775       /usr/lib/libbonobo-2.so.0.0.0Aborted

```

Any ideas what's up with all that?  To be sure, Audacity's pop and click filter improved the original recording somewhat, and I could live with it like that, but I'd like to improve upon that, if possible.

Thanx in advance,
Fred in St. Louis

---

### Post by fredbird67 on 2010-02-01
Never mind, I found a way around it!

I had tried Gramofile, but never could tell that it was working or created a cleaned-up version of each WAV file.  I then gave Gramofile another try and paid closer attention to everything the program displayed in the terminal, and then figured out what I had been doing wrong -- that album sounds much better now! :-)

---

### Post by AdamGott on 2010-02-15
Any solutions?  This program was working well for me for a while but it now crashes every time I try to load a file.  Audacity does a pretty crappy job of noise removal and I have not been able to find a better substitute than this.

---

