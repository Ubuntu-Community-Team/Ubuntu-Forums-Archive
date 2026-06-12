---
title: "NVIDIA 2D speed very slow in Gutsy"
date: 2007-10-31
forum: Multimedia &amp; Video
---

### Post by benton on 2007-10-31
Hi there,

Right after installing Xubuntu 7.10, I installed the nvidia-glx package as suggested by the Restricted Drivers Manager. I've noticed that 2D speed is very slow, i.e., I can see the (slow) repainting of web pages while scrolling, and 2D game "Abe's Amazing Adventure" runs at lame frame rates.

I'm using a 1Ghz Pentium III laptop, running at full speed (997Mhz according to cat/proc/cpuinfo). Video card is NVIDIA GeForce 2Go with 16MB DDR running at 1024x768.

Do u think this slow speed is 'normal' for my hardware specs? Is there anything I can do to speed up the driver's 2D performance?

Thanks!

---

### Post by bwallum on 2007-10-31
I think your card needs to use the nvidia-glx driver (nv) and not the nvidia-glx-new driver (nvidia).

Try running this in a terminal first

```
sudo nvidia-xconfig
```

If no improvement make sure you are not trying to run with nvidia-glx-new driver. You can check this with System>Administration>Synaptic Package Manager. Just search for nvidia-glx. If the nvidia-glx-new is installed then you should install the nvidia-glx (the '-new driver' will be automatically removed).

The following are listed in Ubuntu Wiki as requiring the legacy nvidia driver:-

GeForce 256 0x0100
GeForce DDR 0x0101
Quadro 0x0103
GeForce2 GTS/GeForce2 Pro 0x0150
GeForce2 Ti 0x0151
GeForce2 Ultra 0x0152
Quadro2 Pro 0x0153

I note that your card is a NVIDIA GeForce 2Go. This card is not listed here but you may like to check it out. The following is a good place to get up to speed with nVidia drivers.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by sulligogs on 2008-05-07
Hi there,

Been using Xubuntu since the Gutsy release and I am now currently running Hardy on three seperate machines:-

1) AMD Athlon 2200XP+, 1. GB RAM, 40 GB hard disk and nVidia 6600 AGP
2) AMD Duron 750, 768 MB (SDRAM) 40 GB hard disk and nVidia FX 5500 AGP
3) IBM ThinkPad T22, P3 900MHZ, 256 GB RAM and 20 GB hard disk

Out of the three, one is going through a massive slowdown with rendering 2D and every second or so has 100% hit on it's CPU when looking in System Monitor.  Which one?

The 750mhz Duron.

The other two are sound.  The Athlon runs like a charm.  The ThinkPad is sweet with hardly any slowdowns in 2D performance (such as when running FireFox 3 Beta 5) and  both of them do not have any unusal CPU hit.

The Athlon and the Duron has the 169.12 version of the "nvidia-glx-new" installed from EnvyNG.  Every second I can see the Duron's System Monitor showing something like "28%" to "65%" to "100%" over and over.  Yet, looking at System Monitor on the Performances tab the app that seems to take the most CPU time is Gnome System Monitor at only about %20.  No other app seems to take any CPU load.

It is a fresh install and I could install it again, I suppose.  But, has anybody else had this with the Duron?

Thanks anyway for reading.

This affects the

---

### Post by sulligogs on 2008-05-08
Har har!

I got to the bottom of the problem.  Now my average CPU time runs at about 40%, according to System Monitor.

The offending app (and I don't like to call it that) is WICD.  I just remembered someone saying it can play havoc with your resources and they are right.

Shame really!

I can still use it to connect to my preferred network though.  It will still do that on start up.  I just disabled the tray icon from the system tray.

Much better now thanks!

---

