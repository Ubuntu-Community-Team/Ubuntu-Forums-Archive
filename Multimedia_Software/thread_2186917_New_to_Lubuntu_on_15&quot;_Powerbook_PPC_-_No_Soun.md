---
title: "New to Lubuntu on 15&quot; Powerbook PPC - No Sound"
date: 2013-11-09
forum: Multimedia Software
---

### Post by btheoret on 2013-11-09
Hello,

I've searched far and wide, all over the internet to try and get my sound to work on my machine which has newly been brought back to life with Lubuntu installed.

After doing an "lspci" in terminal I got this:
```

0000:00:0b.0 Host bridge: Apple Inc. UniNorth 2 AGP
0000:00:10.0 VGA compatible controller: Advanced Micro Devices, Inc. [AMD/ATI] RV350/M10 [Mobility Radeon 9600 PRO Turbo]
0001:10:0b.0 Host bridge: Apple Inc. UniNorth 2 PCI
0001:10:12.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)
0001:10:13.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller
0001:10:17.0 Unassigned class [ff00]: Apple Inc. KeyLargo/Intrepid Mac I/O
0001:10:19.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:1a.0 USB controller: Apple Inc. KeyLargo/Intrepid USB
0001:10:1b.0 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:10:1b.1 USB controller: NEC Corporation OHCI USB Controller (rev 43)
0001:10:1b.2 USB controller: NEC Corporation uPD72010x USB 2.0 Controller (rev 04)
0002:24:0b.0 Host bridge: Apple Inc. UniNorth 2 Internal PCI
0002:24:0d.0 Unassigned class [ff00]: Apple Inc. UniNorth/Intrepid ATA/100
0002:24:0e.0 FireWire (IEEE 1394): Apple Inc. UniNorth 2 FireWire (rev 81)
0002:24:0f.0 Ethernet controller: Apple Inc. UniNorth 2 GMAC (Sun GEM) (rev 80)

```

...and then "cat /etc/issue" I got the following:
```

Ubuntu 12.04.3 LTS \n \l

```

...and finally "lsmod | grep ^snd" I got this:
```

snd_powermac           66397  0 
snd_pcm                88810  1 snd_powermac
snd_timer              23955  1 snd_pcm
snd                    71315  3 snd_powermac,snd_pcm,snd_timer
snd_page_alloc          7388  1 snd_pcm
```

I've tried everything I can think of and everything I could find online.  Now I'm coming to the source and where the experts are so hopefully I can get this machine running full speed ahead with sound.

I'm still learning as I'm a bit of a newbie with Linux.  I'm getting there...

Any help you can provide would be great.  Let me know if you need any more information.  Thanks again!

---

### Post by dan47 on 2014-01-23
Sorry to read no answer about sound over your PowerBook 15".
My post could have been : [SIZE=2][FONT=arial]New to Lubuntu on 15" Powerbook PPC - [/FONT]No Sound.

I'm still learning too as I'm a full newbie with Linux.We're getting there...
Cheers.
[/SIZE]

---

