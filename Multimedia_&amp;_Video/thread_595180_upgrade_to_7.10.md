---
title: "upgrade to 7.10"
date: 2007-10-28
forum: Multimedia &amp; Video
---

### Post by jpl80 on 2007-10-28
I updated from 7.04 to 7.10 and my display no longer shows the correct resolution of 1440 x 900. So I ran the line:

```
dpkg-reconfigure xserver-xorg
```

and I went through the settings to try and get the correct resolution. I fear I have made things worse... Now when I boot, I get this message:

```
Starting up ...
Loading, please wait...
kinit: name_to_dev_t(/dev/disk/by-uuid/902566b1-0fb1-4ea0-af8e-24d8a2db564a) = sda5(8,5)
kinit: trying to resume from /dev/disk/by-uuid/902566b1-0fb1-4ea0-af8e-24d8a2db564a
kinit: No resume image, doing normal boot...

Ubuntu 7.10 bishop-desktop tty1

bishop-desktop login:
```

this is accompanied by an error that says xorg isn't configured correctly:

```
/etc/gdm/failsafeXServer: line 47: [: too many arguments
Warning: Failsafe mode was already attempted within 30 seconds.
Warning: Falling back to gdm to report the issue.
```

please help!

---

### Post by bapoumba on 2007-10-28
Moved to "Video".

---

### Post by jpl80 on 2007-11-09
So my dilemma was that I could either spend countless hours trying to get a very old video card working or research which cards other users got working and buy one of those. I chose the later. I advise you to do the same. This what I recommend:

[Research which nvidia video cards that are shown to work well with Ubuntu here]("http://ubuntuforums.org/showthread.php?t=221313").

Research a relatively inexpensive card that fits your system (you need to know whether you have AGP, PCI, or PCI Express slots). This is the card I chose ($50) and it worked flawlessly:

[CHAINTECH SA5200-256 GeForce FX 5200 256MB 128-bit DDR AGP 4X/8X Video Card - Retail]("http://www.newegg.com/product/product.asp?item=N82E16814145083")

Detected perfect resolution for my Samsung 19" Widescreen LCD (Syncmaster 941BW) and it works great. Try the accelerated graphics feature in Ubuntu 7.10. Looks awesome!

Thanks,

---

### Post by Irontux on 2007-11-12
I have the same  problem.
I have upgrade my ubuntu feisty to gutsy.
I have change my monitor from 17" to 19"wide (is a philips 190CW).
Sometime serverX (sometimes all pc) freeze. It's go in failsafe mode. Reported "Too many argument in line 47 of /etc/gdm/failsafeXServer"

What i do?

---

