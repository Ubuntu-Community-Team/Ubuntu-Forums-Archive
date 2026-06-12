---
title: "Diablo II &amp; Wine =&gt; sound and focus problems"
date: 2009-01-25
forum: Multimedia Software
---

### Post by herr_tichy on 2009-01-25
Hi Forum!

I'm currently trying to get Diablo II LoD running under wine. I've completed installation and patching under Windows XP and the game DOES start up and work. However:

When I run it without the parameter "-w" (for windowed instead of fullscreen), I end up with something like [this]("http://thelow.ath.cx/img/uf/diablo.png"). The sound keeps playing in the background, however the screen is frozen and the only way to get out of there is to kill it from the console.

Ok, I might as well run it in window mode, however, there are also problems:

The sound is extremely distorted, as it is with all applications under wine. So far, that didn't disturb me much, now it does. Here is an [example]("http://thelow.ath.cx/img/uf/diablo2_problem.wav.mp3"). Anybody got any idea how to fix that?

And: When Diablo loses focus in windowed mode, it refuses to "accept" it again. Difficult to describe - the game continues to run, but it ignores all keyboard and mouse input.

I'm running Ubuntu 8.10 64 bits on a Samsung R70, specs as follow:

```
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GS (rev a1)
03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
04:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8055 PCI-E Gigabit Ethernet Controller (rev 13)
05:09.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b4)
05:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 18)
05:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 09)
05:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 04)
05:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
```

Compiz is enabled.

Would be nice, if someone could give me a push in the right direction, as I am completely baffled here :(

Thanks!

---

### Post by herr_tichy on 2009-01-26
Anyone?

---

### Post by nefigah on 2009-02-07
alt enter to unfreeze after losing focus. See [http://appdb.winehq.org/appview.php?iVersionId=315](http://appdb.winehq.org/appview.php?iVersionId=315)

---

