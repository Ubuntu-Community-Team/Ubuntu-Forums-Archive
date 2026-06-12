---
title: "Can't configure 1280x800 resolution - Acer Aspire 1690"
date: 2007-02-28
forum: Multimedia &amp; Video
---

### Post by NoxDineen on 2007-02-28
Okay, I'm a total Linux noob, just installed Ubuntu a day or so ago on my personal and work laptops. I was able to get the ATI drivers and resolution on my work Dell Inspiron 6400 configured to a 1280x800 resolution, but I haven't had any luck with my personal machine, an Acer Aspire 1690.

Most of the support I've read for this model of laptop indicates it should have an ATI Radeon video card, however, when I check (via lspci) I get the following info:

lspci -x yields:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
00: 86 80 92 25 07 00 90 00 03 00 00 03 00 00 80 00
10: 00 00 08 b0 01 18 00 00 08 00 00 c0 00 00 00 b0
20: 00 00 00 00 00 00 00 00 00 00 00 00 25 10 66 00
30: 00 00 00 00 d0 00 00 00 00 00 00 00 0a 01 00 00

```

while lspci -v tells me:
```
00:02.0 VGA compatible controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03) (prog-if 00 [VGA])
        Subsystem: Acer Incorporated [ALI] Unknown device 0066
        Flags: bus master, fast devsel, latency 0, IRQ 177
        Memory at b0080000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at 1800 [size=8]
        Memory at c0000000 (32-bit, prefetchable) [size=256M]
        Memory at b0000000 (32-bit, non-prefetchable) [size=256K]
        Capabilities: <access denied>

00:02.1 Display controller: Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller (rev 03)
        Subsystem: Acer Incorporated [ALI] Unknown device 0066
        Flags: fast devsel
        Memory at 52000000 (32-bit, non-prefetchable) [disabled] [size=512K]
        Capabilities: <access denied>
```

So I am confounded. I tried installing the driver that worked on the Dell, but that ended up making my machine so angry that I had to just re-install Ubuntu.

Any help or insight would be very appreciated. I do a lot of photography and I have a video podcast, so I'm editing video. The screwy aspect ratio I'm dealing with now makes everything look horrible.

Edited to add: The graphics solution I tried (which worked on my Dell) was "sudo apt-get install xorg-driver-fglrx" and then editing xorg.conf so that the "fglrx" driver is being used. When I tried that with the Acer and re-booted Ubuntu couldn't even load X.

Thanks!

---

### Post by deadgobby on 2007-03-01
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1690WLCi?highlight=%28Acer%29](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire1690WLCi?highlight=%28Acer%29)
Hope this info helps.
Gobby

---

