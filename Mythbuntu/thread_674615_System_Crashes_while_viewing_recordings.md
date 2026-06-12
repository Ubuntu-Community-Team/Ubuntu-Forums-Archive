---
title: "System Crashes while viewing recordings"
date: 2008-01-21
forum: Mythbuntu
---

### Post by Dragonflyoh on 2008-01-21
When I playback HDTV recordings the frontend crashes and the only way to continue is to reboot the system. Everything else works fine, playing DVD's, avi files, viewing photos live HDTV, etc. The only thing I have been able to find concerning crashes is that MYTHTV cannot cause a system to crash so it must be something else such as overheating or video card drivers. My set up is the latest Mythbuntu running a frontend on a PC with a 3.0 MHZ Pentium D Dual processor, 1 GB Memory, NVIDIA GeForce 6200 video card using NV drivers connected to the backend through a wired router. I looked through all of the log files I could find and found one comment about a broken bios problem. I updated the bios and the problem continues. I am a Linux newbie at best and would appreciate any assistance.

---

### Post by tgalati4 on 2008-01-21
Most computer buses don't have the throughput to effectively deal with high definition throughput.  You would think a dual-core 3 GHz processor could handle it.  The processor is not the problem, it's the data path.  

I made printouts from a website that show the bandwidth bottlenecks.  HD content typically requires 25 to 34 Mbits/sec steam.  

What kind of hard disk are you using?  What are the hdparm -tT /dev/sda results?  The 6200 graphics card should have enough horsepower.

It's also possible that your power supply is failing.  HD content will draw a lot of power from everything in the system.

The fact that dmesg | tail is not showing anything would point to a power problem.

Just about any other problem would leave droppings in /var/log.

---

### Post by Dragonflyoh on 2008-01-21
The hard drive is a 250 GB SATA 7200 RPM Hitachi.
The results of hdparm are:
-t 1132 mb in 2.05 sec = 565.52 mb/sec
-T 126 mb in 3.02 sec = 41.74 mb/sec

The power supply is a two month old Antec 80 PLUS® Certified EarthWatts 380W power supply.

What website had the bandwidth bottle necks?

Aaalso dmseg |tai results are:
~$ dmesg |tail
[   37.360623] NET: Registered protocol family 10
[   37.360920] lo: Disabled Privacy Extensions
[   37.735363] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   37.815031] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   37.830012] NFSD: starting 90-second grace period
[   40.945348] agpgart: Found an AGP 3.5 compliant device at 0000:00:00.0.
[   40.945369] agpgart: Putting AGP V3 device at 0000:00:00.0 into 8x mode
[   40.945446] agpgart: Putting AGP V3 device at 0000:01:00.0 into 8x mode
[   43.337527] NET: Registered protocol family 17
[   56.162239] eth0: no IPv6 routers present

---

### Post by rosegarden78 on 2008-01-21
Are you using Mythbuntu?  I should give it a look.  You probably need to use XFCE or Xubuntu because it has restricted extras for media support.

---

### Post by Dragonflyoh on 2008-01-21
Yes I am using Mythbuntu.

---

### Post by tgalati4 on 2008-01-22
PCI bus bandwidth Dell White Paper:

[http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp](http://www.dell.com/content/topics/global.aspx/vectors/en/2004_pciexpress?c=us&l=en&s=corp)

I have an AOpen multimedia PC with a 2.94 GHz Pentium D and it doesn't have the bandwidth to display HD smoothly with an i945gm graphics chipset.  AOpen dropped it and quickly redesigned a 965 chipset multimedia PC, but I haven't seen reviews on its performance yet.

Antec make decent 97% efficient power supplies, so I would agree with you that power is unlikely.

Hitachi DeathStar drives are OK until they blow up.  Your 41 MB/sec read speed should be OK for sustained HD content, but I have an identical drive (in a slower machine and it stutters badly with HD movie trailers.)  So you need to find some errors in /var/log to see where myth front end is failing.

I haven't set up myth in my AOpen box yet so I can't comment on how it performs.  Can you run myth with a debug mode?

Try running it in a separate terminal or a remote machine and see what comes up.

One other thing, I believe envy only works for 7600 cards and later but there may be better drivers than "nv".  I would search the forums.  It could be as simple as a resolution/modeline issue.  How much video RAM on the card?  PCI-E or is it AGP 8X?

---

### Post by Dragonflyoh on 2008-01-26
Thanks for the ideas. I installed Envy, the latest version, and after installing the latest nvidia drivers, playback worked without crashing. On to issues with my remote that I will post with a new thread. Again, thank you for your help.

---

