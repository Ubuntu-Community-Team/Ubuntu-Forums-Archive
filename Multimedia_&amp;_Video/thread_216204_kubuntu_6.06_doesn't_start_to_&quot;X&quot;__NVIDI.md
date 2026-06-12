---
title: "kubuntu 6.06 doesn't start to &quot;X&quot; / NVIDIA GeForce FX5200 with 2 screens"
date: 2006-07-15
forum: Multimedia &amp; Video
---

### Post by flying_penguin on 2006-07-15
Hi!

I'd like to test - and afterwards install - kubuntu 6.06. But every time I try to boot from CD kubuntu freezes at the second (?) progress bar. From that point on I can only shut down the system by pressing crtl+alt+del. That's why I can't post any configuration files. :confused: 

Maybe the problem is caused by my system-video-setup that isn't "liked" by "X":
1) video card with NVIDIA GeForce FX 5200-chipset
2) 2 Screens (2x TFT 19" but different manufacturers: fist one connected to the analogue port, second one connected to the DVI-port by the help of a digital-analogue-adapter.) 

Any ideas what to try to make kubuntu start to X? Or: Any links what to read?

The next problem will be to set up the desktop to use the two screen. But: first things first.  ;-)

Thanks!

flying_penguin

---

### Post by tseliot on 2006-07-15
Keep ONLY 1 Monitor plugged in 1 card and then follow these instructions:

1) Install Ubuntu using the alternate installation CD.

2) After the installation the xserver will crash

3) You will be able to boot in RECOVERY MODE from the GRUB Menu almost as soon as you turn on your computer (it will take you to the command line).

Then you will need to type:
```
dpkg-reconfigure xserver-xorg
```

and select the "vesa" driver. Press ENTER whenever you don't know the answer to a question.

4) Type:
```
reboot
```

The Xserver should work fine

---

### Post by flying_penguin on 2006-07-15
Hi Alberto,

thank you for your super-fast answer! That sounds great. :-D 

I'll try that as soon as possible.

flying_penguin

---

