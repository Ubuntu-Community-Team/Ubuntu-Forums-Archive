---
title: "Video Output issue with Atom based Mini PC"
date: 2012-12-26
forum: Multimedia Software
---

### Post by chandan_raka on 2012-12-26
Hello All,

I have installed Ubuntu 12.04 LTS on my Giada mini PC [http://www.giadapc.com/products/minipc/slim%20series/i35V.html](http://www.giadapc.com/products/minipc/slim%20series/i35V.html)

If I install Ubuntu 12.10 the graphics does not work at all. However, it worked perfectly with 12.04 LTS. When I look at Additional driver inside system settings I get Intel's Cedar trial drivers. After installing these additional accelerator drivers I do not get full resolution on my display monitor. I am using a old Dell 15' (non wide screen) monitor with VGA output.

I have little knowledge in playing with video card as I have never got Projectors worked on Linux so far (if it did not work automatically). 

lspci output


```
chandank@chandan:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Atom Processor D2xxx/N2xxx DRAM Controller [8086:0bf5] (rev 03)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor D2xxx/N2xxx Integrated Graphics Controller [8086:0be1] (rev 09)
```

---

### Post by chandan_raka on 2012-12-26
After installing All Intel Cedar Drivers from system settings, I got back my display. 

How I fixed it: System Settings -> Additional Drivers 

Installed all Cedar drivers one after another and rebooted. Configured the resolution and it fixed for it. Hopefully same should work with lubuntu or other light Destros, as Ubuntu unity desktop runs really slow in this such a tiny hardware.

---

