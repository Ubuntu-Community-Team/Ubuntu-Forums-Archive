---
title: "Sleep Problems with an Hp Pavilion DV7-3165dx"
date: 2010-12-18
forum: Multimedia Software
---

### Post by penguin10916 on 2010-12-18
Anyways, while I was in the process of fixing the various problems with my laptop, I came to discover that when I would shut my laptop, it would fail to wake. Since my laptop uses the ATi Mobility Radeon HD4200, I tested out the open-source driver and the proprietary driver. The problem exists for both, so I'm wondering if anyone knows how to fix this :p

Oh, and I am running Ubuntu 10.10 64 bit.

---

### Post by penguin10916 on 2010-12-22
Bump

---

### Post by penguin10916 on 2010-12-26
Bump again...

---

### Post by penguin10916 on 2011-01-01
Bump yet again...

---

### Post by stephenjbarr on 2011-02-08
Having the same problem. Did you get it fixed?

---

### Post by penguin10916 on 2011-02-19
I haven't had any luck. Although, I did find awhile back that Sabayon 5.4 didn't have this problem... so I'm trying out Sabayon 5.5 to see if it will still work.

---

### Post by core.ban on 2011-04-15
This is a problem with the videocards in that laptop. My DV7 has 2 video cards, and ubuntu is unable to select the right card upon being revived from sleep/suspend.

See these posts:
[http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html](http://linux.aldeby.org/howto-ubuntu-linux-on-hp-pavilion-dv2000-dv6000-dv9000-series-laptops.html)
[http://ubuntuforums.org/showthread.php?t=1542987](http://ubuntuforums.org/showthread.php?t=1542987)
[http://ubuntuforums.org/showthread.php?t=1469340&page=16](http://ubuntuforums.org/showthread.php?t=1469340&page=16)
[http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/](http://www.amitsrivastava.net/2008-03-23-hibernate-suspend-resolved-ubuntu-gutsy-nvidia-dell-vostro/)
[http://ubuntuforums.org/showthread.php?t=350265&page=3](http://ubuntuforums.org/showthread.php?t=350265&page=3)
[http://ubuntuforums.org/showthread.php?t=1566308](http://ubuntuforums.org/showthread.php?t=1566308)
[http://ubuntuforums.org/showthread.php?t=1565593](http://ubuntuforums.org/showthread.php?t=1565593)
[http://ubuntuforums.org/showthread.php?t=1331522](http://ubuntuforums.org/showthread.php?t=1331522)

Let me if any one of those solutions works for you. I am still testing.

---

### Post by stealth. on 2011-04-15
I have this problem too, but how did you get 2 video cards?

---

### Post by core.ban on 2011-04-15
> **stealth. said:**
> I have this problem too, but how did you get 2 video cards?

```
me@home:~$ lspci -nn | grep VGA
01:05.0 VGA compatible controller [0300]: ATI Technologies Inc M880G [Mobility Radeon HD 4200] [1002:9712]
02:00.0 VGA compatible controller [0300]: ATI Technologies Inc Redwood [Radeon HD 5600 Series] [1002:68c1]
```

One is built in (the 4200 one). The theory is that when the computer comes back from sleep it tries to use the 4200 card and it fails. I am like 80% sure it is the video card, because sometimes the screen doesn't go black, but just goes ****** up with the screen showing every single pixel in a different color (imagine a tv on a dead channel but in color).

I reported this as a bug. Please go to it and mention that this affects you too:
[https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/762440/+affectsmetoo](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/762440/+affectsmetoo)

Bug report: [https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/762440](https://bugs.launchpad.net/ubuntu/+source/pm-utils/+bug/762440)

---

### Post by penguin10916 on 2011-09-02
I found a solution. If you go on hps site, you will see a BIOS update titled f.13. My laptop shipped with the f.15 BIOS, but when I downgraded it, sleep began to work in Linux. So.... all problems are solved. :-)

---

