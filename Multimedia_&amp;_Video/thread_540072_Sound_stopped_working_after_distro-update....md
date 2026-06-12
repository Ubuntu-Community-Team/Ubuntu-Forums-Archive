---
title: "Sound stopped working after distro-update..."
date: 2007-09-01
forum: Multimedia &amp; Video
---

### Post by Jest3r on 2007-09-01
Hello all.
  I did the distro-update today... after the reboot all my sound has stopped working.. I have followed the "Comprehensive Sound Problem Solutions Guide v0.5e", But still no luck :(
[http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)

$ uname -a
Linux jester-desktop 2.6.20-16-generic #2 SMP Thu Aug 30 23:16:15 UTC 2007 x86_64 GNU/Linux

$ alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

$ aplay -l
aplay: device_list:222: no soundcards found...

$ lspci -v
00:04.0 Multimedia audio controller: nVidia Corporation CK804 AC'97 Audio Controller (rev a2)
        Subsystem: Giga-byte Technology Unknown device ae01
        Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 10
        I/O ports at b400 [size=256]
        I/O ports at b800 [size=256]
        Memory at f5005000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

$ sudo modprobe snd-
FATAL: Module snd_ not found.
$ sudo modprobe snd_
FATAL: Module snd_ not found.

tried  the following
 Getting the ALSA drivers from a *fresh* kernel
 ALSA driver Compilation

---

### Post by Jest3r on 2007-09-01
[Realtek Driver's ]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=14&PFid=23&Level=4&Conn=3&DownTypeID=3&GetDown=false")

**Download..**
"Others"	4.06a	2007/6/8	4570k

**Install**
$ bunzip2 realtek-linux-audiopack-4.06a.tar.bz2
$ tar -xf realtek-linux-audiopack-4.06a.tar 
$ cd realtek-linux-audiopack-4.06a
# ./install


I have sound again :guitar:

---

### Post by aboutblank on 2007-09-02
Sweet! Thanks a bunch! 

I had the exact same problem with the same audio chipset. Darn updates b0rking my setup!

---

