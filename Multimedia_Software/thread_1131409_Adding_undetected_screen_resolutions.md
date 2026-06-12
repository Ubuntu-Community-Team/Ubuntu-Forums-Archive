---
title: "Adding undetected screen resolutions"
date: 2009-04-20
forum: Multimedia Software
---

### Post by m.cowan on 2009-04-20
Hi Everyone, 

I have a Samsung syncmaster 225uw with a native screen resolution of 1680x1050. However jaunty detects the maximum resolution to be 1280x1024. After some research I found this support article: 

[https://wiki.ubuntu.com/X/Config/Resolution](https://wiki.ubuntu.com/X/Config/Resolution)

I'm trying to add the undetected resolution however when it tells you to 'create a modeline using the gtf or cvt utility' I have no idea how to do this. 

Can someone shed some light on this for a noob? 
Cheers \\:D/

---

### Post by m.cowan on 2009-04-21
Okay, 

So I've worked out how to add the resolution. But I still get a problem: 

```
don@office:~$ gtf 1680 1050 60

  # 1680x1050 @ 60.00 Hz (GTF) hsync: 65.22 kHz; pclk: 147.14 MHz
  Modeline "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync

don@office:~$ xrandr --newmode "1680x1050_60.00"  147.14  1680 1784 1968 2256  1050 1051 1054 1087  -HSync +Vsync
don@office:~$ xrandr --addmode default 1680x1050_60.00
don@office:~$ xrandr --output default --mode 1680x1050_60.00
xrandr: Configure crtc 0 failed
don@office:~$ 
```

Note: Default is the name for my VGA (according to xrandr), so that's not the issue. It's really annoying having a beautiful monitor and not being able to have full resolution. I really want to solve this one :(

System info: 

uname -r
2.6.28-11-generic

**Video card**
don@office:~$ lspci | grep VGA 
02:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a2)

**NVIDA driver version** (installed via ubuntu's restricted driver application): 96.43.10

---

### Post by m.cowan on 2009-04-22
Just an update. After reinstalling Jaunty all is well. Seemed to be the only solution. Possibly a bug when upgrading your monitor to a larger model (I installed jaunty a few days ago with a much smaller monitor).

---

