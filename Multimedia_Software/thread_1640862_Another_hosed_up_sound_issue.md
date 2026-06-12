---
title: "Another hosed up sound issue"
date: 2010-12-08
forum: Multimedia Software
---

### Post by b1381 on 2010-12-08
I am runing Ubuntu 10.10, with all of the latest updates.  My sound card was working, before the latest upgrade, I tried to follow the directions outlined in the following:
  [http://ubuntuforums.org/showthread.php?t=205449](http://ubuntuforums.org/showthread.php?t=205449)
But the process errors out when it tries to create /proc/asound and /proc/asound/cards.

I tried to create the directories manually using 'sudo mkdir /proc/asound' and  'sudo mkdir /proc/asound/cards' but linux errors out.

I obviously need help, and any help will be appriciated.

 Command Line Output Follows:
aplay -l
aplay: device_list:235: no soundcards found...

lspci -v
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
    Subsystem: IBM NetVista A30p
    Flags: bus master, medium devsel, latency 0, IRQ 9
    I/O ports at 1c00 [size=256]
    I/O ports at 18c0 [size=64]
    Memory at 90000c00 (32-bit, non-prefetchable) [size=512]
    Memory at 90000800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: snd-intel8x0

---

