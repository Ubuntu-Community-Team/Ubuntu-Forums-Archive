---
title: "Ripping music from CD so MP3 player plays in correct order"
date: 2010-05-05
forum: Multimedia Software
---

### Post by mortenalver on 2010-05-05
I have a Creative Zen Mozaic player, which appears as a USB drive. I've got Ubuntu 10.04 installed.

Ripping the MP3s with Sound Juicer is no problem, but my MP3 player doesn't recognize artist or album names, putting it under "Unknown artist" and "Unknown album". The song names appear correct, but the songs are in the wrong order. In the Sound Juicer interface, the album title and artist are correctly detected and displayed.

I assume this is an ID3 tag problem. I could get the process working perfectly with Grip earlier when using Mandriva, but now I'm on Ubuntu and Grip isn't in the repository. I tried with RipperX, which appears to do the correct thing, but seems to crash, and only sets the correct tags for the first few songs (for this particular CD).

The mp3 setup in Sound Juicer is as follows:
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux

I'm hoping someone can shed some light on what I need to do to get this right :-k

---

### Post by lidex on 2010-05-06
You could also try Asunder. But I'm curious about RipperX, as that is what I use. Try running it from a terminal to see any error messages.

---

### Post by mortenalver on 2010-05-06
Thanks for the reply, I'll have a look at Asunder.

Below is the output from RipperX when it crashes. I've tested with two different music CDs, and the same happens. It crashes after ripping and encoding all files, apparently while doing the ID3 tag stuff.

alver@alver-laptop:~$ ripperX
*** buffer overflow detected ***: ripperX terminated
======= Backtrace: =========
/lib/tls/i686/cmov/libc.so.6(__fortify_fail+0x50)[0xa74350]
/lib/tls/i686/cmov/libc.so.6(+0xe128a)[0xa7328a]
/lib/tls/i686/cmov/libc.so.6(+0xe09c8)[0xa729c8]
/lib/tls/i686/cmov/libc.so.6(_IO_default_xsputn+0x9e)[0x9fbafe]
/lib/tls/i686/cmov/libc.so.6(_IO_vfprintf+0xe24)[0x9cfa34]
/lib/tls/i686/cmov/libc.so.6(__vsprintf_chk+0xad)[0xa72a7d]
/lib/tls/i686/cmov/libc.so.6(__sprintf_chk+0x2d)[0xa729bd]
ripperX[0x8054830]
ripperX[0x80560b8]
ripperX[0x805680c]
/lib/libglib-2.0.so.0(+0x3bd5c)[0x7d2d5c]
/lib/libglib-2.0.so.0(g_main_context_dispatch+0x1d5)[0x7d25e5]
/lib/libglib-2.0.so.0(+0x3f2d8)[0x7d62d8]
/lib/libglib-2.0.so.0(g_main_loop_run+0x187)[0x7d6817]
/usr/lib/libgtk-x11-2.0.so.0(gtk_main+0xb9)[0x247299]
ripperX[0x8056bf6]
/lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xe6)[0x9a8bd6]
ripperX[0x804b8b1]
======= Memory map: ========
00110000-004dd000 r-xp 00000000 08:06 11275548   /usr/lib/libgtk-x11-2.0.so.0.2000.0
004dd000-004e1000 r--p 003cd000 08:06 11275548   /usr/lib/libgtk-x11-2.0.so.0.2000.0
004e1000-004e3000 rw-p 003d1000 08:06 11275548   /usr/lib/libgtk-x11-2.0.so.0.2000.0
004e3000-004e5000 rw-p 00000000 00:00 0 
004e5000-004e7000 r-xp 00000000 08:06 10883431   /lib/tls/i686/cmov/libutil-2.11.1.so
004e7000-004e8000 r--p 00001000 08:06 10883431   /lib/tls/i686/cmov/libutil-2.11.1.so
004e8000-004e9000 rw-p 00002000 08:06 10883431   /lib/tls/i686/cmov/libutil-2.11.1.so
004e9000-004eb000 r-xp 00000000 08:06 11275058   /usr/lib/libXcomposite.so.1.0.0
004eb000-004ec000 r--p 00001000 08:06 11275058   /usr/lib/libXcomposite.so.1.0.0
004ec000-004ed000 rw-p 00002000 08:06 11275058   /usr/lib/libXcomposite.so.1.0.0
004ed000-004ef000 r-xp 00000000 08:06 11275062   /usr/lib/libXdamage.so.1.1.0
004ef000-004f0000 r--p 00001000 08:06 11275062   /usr/lib/libXdamage.so.1.1.0
004f0000-004f1000 rw-p 00002000 08:06 11275062   /usr/lib/libXdamage.so.1.1.0
004f2000-00517000 r-xp 00000000 08:06 11275798   /usr/lib/libpangoft2-1.0.so.0.2800.0
00517000-00518000 r--p 00024000 08:06 11275798   /usr/lib/libpangoft2-1.0.so.0.2800.0
00518000-00519000 rw-p 00025000 08:06 11275798   /usr/lib/libpangoft2-1.0.so.0.2800.0
00519000-00531000 r-xp 00000000 08:06 11275393   /usr/lib/libgdk_pixbuf-2.0.so.0.2000.0
00531000-00532000 r--p 00017000 08:06 11275393   /usr/lib/libgdk_pixbuf-2.0.so.0.2000.0
00532000-00533000 rw-p 00018000 08:06 11275393   /usr/lib/libgdk_pixbuf-2.0.so.0.2000.0
00533000-00557000 r-xp 00000000 08:06 10883405   /lib/tls/i686/cmov/libm-2.11.1.so
00557000-00558000 r--p 00023000 08:06 10883405   /lib/tls/i686/cmov/libm-2.11.1.so
00558000-00559000 rw-p 00024000 08:06 10883405   /lib/tls/i686/cmov/libm-2.11.1.so
00559000-005f3000 r-xp 00000000 08:06 11275406   /usr/lib/libgio-2.0.so.0.2400.0
005f3000-005f4000 ---p 0009a000 08:06 11275406   /usr/lib/libgio-2.0.so.0.2400.0
005f4000-005f5000 r--p 0009a000 08:06 11275406   /usr/lib/libgio-2.0.so.0.2400.0
005f5000-005f6000 rw-p 0009b000 08:06 11275406   /usr/lib/libgio-2.0.so.0.2400.0
005f6000-005f7000 rw-p 00000000 00:00 0 
005f7000-00637000 r-xp 00000000 08:06 11275794   /usr/lib/libpango-1.0.so.0.2800.0
00637000-00638000 ---p 00040000 08:06 11275794   /usr/lib/libpango-1.0.so.0.2800.0
00638000-00639000 r--p 00040000 08:06 11275794   /usr/lib/libpango-1.0.so.0.2800.0
00639000-0063a000 rw-p 00041000 08:06 11275794   /usr/lib/libpango-1.0.so.0.2800.0
0063a000-0064d000 r-xp 00000000 08:06 10879174   /lib/libz.so.1.2.3.3
0064d000-0064e000 r--p 00012000 08:06 10879174   /lib/libz.so.1.2.3.3
0064e000-0064f000 rw-p 00013000 08:06 10879174   /lib/libz.so.1.2.3.3
0064f000-00653000 r-xp 00000000 08:06 11275068   /usr/lib/libXfixes.so.3.1.0
00653000-00654000 r--p 00003000 08:06 11275068   /usr/lib/libXfixes.so.3.1.0
00654000-00655000 rw-p 00004000 08:06 11275068   /usr/lib/libXfixes.so.3.1.0
00655000-00659000 r-xp 00000000 08:06 11275544   /usr/lib/libgthread-2.0.so.0.2400.0
00659000-0065a000 r--p 00003000 08:06 11275544   /usr/lib/libgthread-2.0.so.0.2400.0
0065a000-0065b000 rw-p 00004000 08:06 11275544   /usr/lib/libgthread-2.0.so.0.2400.0
0065b000-00674000 r-xp 00000000 08:06 11275139   /usr/lib/libatk-1.0.so.0.3009.1
00674000-00675000 ---p 00019000 08:06 11275139   /usr/lib/libatk-1.0.so.0.3009.1
00675000-00676000 r--p 00019000 08:06 11275139   /usr/lib/libatk-1.0.so.0.3009.1
00676000-00677000 rw-p 0001a000 08:06 11275139   /usr/lib/libatk-1.0.so.0.3009.1
00677000-0068c000 r-xp 00000000 08:06 10883423   /lib/tls/i686/cmov/libpthread-2.11.1.so
0068c000-0068d000 r--p 00014000 08:06 10883423   /lib/tls/i686/cmov/libpthread-2.11.1.so
0068d000-0068e000 rw-p 00015000 08:06 10883423   /lib/tls/i686/cmov/libpthread-2.11.1.so
0068e000-00690000 rw-p 00000000 00:00 0 
00690000-0069e000 r-xp 00000000 08:06 11275066   /usr/lib/libXext.so.6.4.0
0069e000-0069f000 r--p 0000d000 08:06 11275066   /usr/lib/libXext.so.6.4.0
0069f000-006a0000 rw-p 0000e000 08:06 11275066   /usr/lib/libXext.so.6.4.0
006a0000-006a2000 r-xp 00000000 08:06 11275076   /usr/lib/libXinerama.so.1.0.0
006a2000-006a3000 r--p 00001000 08:06 11275076   /usr/lib/libXinerama.so.1.0.0
006a3000-006a4000 rw-p 00002000 08:06 11275076   /usr/lib/libXinerama.so.1.0.0
006a6000-006b0000 r-xp 00000000 08:06 11275796   /usr/lib/libpangocairo-1.0.so.0.2800.0
006b0000-006b1000 r--p 00009000 08:06 11275796   /usr/lib/libpangocairo-1.0.so.0.2800.0
006b1000-006b2000 rw-p 0000a000 08:06 11275796   /usr/lib/libpangocairo-1.0.so.0.2800.0
006b2000-00723000 r-xp 00000000 08:06 11275353   /usr/lib/libfreetype.so.6.3.22
00723000-00727000 r--p 00070000 08:06 11275353   /usr/lib/libfreetype.so.6.3.22
00727000-00728000 rw-p 00074000 08:06 11275353   /usr/lib/libfreetype.so.6.3.22
00728000-00756000 r-xp 00000000 08:06 11275345   /usr/lib/libfontconfig.so.1.4.4
00756000-00757000 r--p 0002d000 08:06 11275345   /usr/lib/libfontconfig.so.1.4.4
00757000-00758000 rw-p 0002e000 08:06 11275345   /usr/lib/libfontconfig.so.1.4.4
00758000-00795000 r-xp 00000000 08:06 11275460   /usr/lib/libgobject-2.0.so.0.2400.0
00795000-00796000 r--p 0003c000 08:06 11275460   /usr/lib/libgobject-2.0.so.0.2400.0
00796000-00797000 rw-p 0003d000 08:06 11275460   /usr/lib/libgobject-2.0.so.0.2400.0
00797000-0085f000 r-xp 00000000 08:06 10879063   /lib/libglib-2.0.so.0.2400.0
0085f000-00860000 r--p 000c7000 08:06 10879063   /lib/libglib-2.0.so.0.2400.0
00860000-00861000 rw-p 000c8000 08:06 10879063   /lib/libglib-2.0.so.0.2400.0
00861000-0094a000 r-xp 00000000 08:06 11275958   /usr/lib/libstdc++.so.6.0.13
0094a000-0094b000 ---p 000e9000 08:06 11275958   /usr/lib/libstdc++.so.6.0.13
0094b000-0094f000 r--p 000e9000 08:06 11275958   /usr/lib/libstdc++.so.6.0.13
0094f000-00950000 rw-p 000ed000 08:06 11275958   /usr/lib/libstdc++.so.6.0.13
00950000-00957000 rw-p 00000000 00:00 0 
00957000-00958000 r-xp 00000000 08:06 11272638   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
00958000-00959000 r--p 00000000 08:06 11272638   /usr/lib/gtk-2.0/2.10.0/loaders/svg_loader.so
00959000-0095a000 rw-p 00001000 08:06 11272638   /usr/lib/gtk-2.0/2.10.0/loaAborted

---

### Post by mortenalver on 2010-05-06
Hm... Asunder looks nice, rips the songs, and the MP3 players finds the correct artist and album names. However, it puts the songs in the wrong order, so there is clearly something missing.

---

### Post by mortenalver on 2010-05-06
Checking the tags with id3tool, I see that Asunder correctly sets the track number tags. It looks like Grip set the tags in the same way, but my MP3 player only orders the albums ripped by Grip correctly.

---

### Post by mc4man on 2010-05-06
Here's a ppa for grip - can't vouch for how it works - don't use grip

[https://launchpad.net/~futurepilot/+archive/ppa](https://launchpad.net/~futurepilot/+archive/ppa)

---

### Post by mortenalver on 2010-05-09
I've found that Rubyripper does the right thing as long as I set the Lame parameters to "-V 3 --id3v2-only". The only disadvantage is that Rubyripper for some reason takes exceptionally long time to rip a CD compared to other programs. Perhaps it is possible to tweak the settings to speed it up.

---

### Post by mc4man on 2010-05-09
> The only disadvantage is that Rubyripper for some reason takes exceptionally long time to rip a CD compared to other programs

The Rubyripper gui (gtk) is somewhat borked in lucid - the cli works fine and is quite fast.

Best bet is to set up your basic config options in the gui but use the cli to do the rip.

Mentioned a bit about here and elsewhere
[http://ubuntuforums.org/showthread.php?p=9264136#post9264136](http://ubuntuforums.org/showthread.php?p=9264136#post9264136)

Otherwise abcde ripper is a good alt.   - link here can help you get set up
[http://ubuntuforums.org/showthread.php?p=9265736#post9265736](http://ubuntuforums.org/showthread.php?p=9265736#post9265736)

---

### Post by mortenalver on 2010-05-09
Thanks for the tip - the CLI version looks nice, but for some reason instead of starting the rip it says "Ripping progress (0%)" and just quits. It creates the album directory and a log file which ends with the track listing and a line with the text "STATUS".

---

### Post by mc4man on 2010-05-09
@ mortenalver
What version of rr are you using and how did you acquire it?

---

### Post by mortenalver on 2010-05-09
Hm, it's version 0.5.7-1~getdeb2, installed from the getdeb repository.

---

### Post by mc4man on 2010-05-09
If you look back in that thread ( starts page before) you'll see ron999 was having issues with the getdeb's package.

If you want, uninstall the getlib's package and I've got a 0.6 beta attached on page 9 (#86

Then from terminal either...
for interactive
```
rrip_cli
```
or to do complete disk
```
rrip_cli -a
```

---

### Post by mortenalver on 2010-05-09
Thanks again! I'm trying the 0.6b2 deb, and it seems to be working fine in CLI mode. It definitely seems faster than the getdeb version in GUI mode.

---

### Post by lidex on 2010-05-11
I notice RipperX has a field in mp3 configuration tab for extra options. Would the parameter you mentioned previously work there?

---

### Post by mortenalver on 2010-05-12
There is a field for extra options in RipperX. However, RipperX actually did the tagging correctly, the problem was that it crashed before tagging all the songs.

---

