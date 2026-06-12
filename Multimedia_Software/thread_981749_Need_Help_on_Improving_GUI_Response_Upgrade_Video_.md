---
title: "Need Help on Improving GUI Response/ Upgrade Video Hardware"
date: 2008-11-14
forum: Multimedia Software
---

### Post by rajkumarm2 on 2008-11-14
**_The Issue:_**
I'm on Ubuntu 8.10. The GUI on my system is **very slow**. I'm giving my hardware configuration below. I'm using the on-board graphics device.
[LIST=1]
[*]If I change my video card to a better one, will it solve the issue?
[/LIST]
[LIST=2]
[*]If yes, can you suggest a PCI NVIDIA video card that's well supported by Ubuntu?
[/LIST]
*(I have only PCI slots. There are no PCI Express slots on the motherboard)*

_My Hardware Configuration:_
Intel Celeron 1.8GHz
Intel 845GLLY Motherboard ([http://support.intel.com/support/motherboards/desktop/D845GLLY/LY_manual.htm](http://support.intel.com/support/motherboards/desktop/D845GLLY/LY_manual.htm))
384MB RAM (SDRAM 133 MHz)
HDD - 80GB IDE
LG DVD RW
LG 17' TFT monitor at 1280x1024

_My Software Configuration:_
Video driver is xserver-xorg-video-intel.
This was selected automatically while installing. I've not changed any configurations.

---

### Post by shof2k on 2008-11-15
If you change your video card to a common Nvidia or ATI card, you should get better performance than the onboard card.  You may need to update the driver though.

I can't suggest a card, but any common card, between 1 and 3 years, old should be OK.  Ask at the shop.

xserver-xorg-vido-intel appears to be very cpu heavy when doing any sort of work. Writing on Abiword takes me to 100% CPU with top showing XORG as the culprit.  On Hardy, this uses < 20% cpu.

---

### Post by rajkumarm2 on 2008-11-16
Thank you **shof2k** for the reply.
You've mentioned that CPU usage goes up to 100%. In which version of Ubuntu does this happen for you?
In my case, CPU usage is high on 8.04 as well as 8.10.
Is the high CPU usage of xserver-xorg-video-intel in 8.04 & 8.10 due to any bug in the driver? I have dual-boot and WindozeXP GUI response is much faster.

---

### Post by psyke83 on 2008-11-16
> **rajkumarm2 said:**
> **_The Issue:_**
I'm on Ubuntu 8.10. The GUI on my system is **very slow**. I'm giving my hardware configuration below. I'm using the on-board graphics device.
[LIST=1]
[*]If I change my video card to a better one, will it solve the issue?
[/LIST]
[LIST=2]
[*]If yes, can you suggest a PCI NVIDIA video card that's well supported by Ubuntu?
[/LIST]
*(I have only PCI slots. There are no PCI Express slots on the motherboard)*

_My Hardware Configuration:_
Intel Celeron 1.8GHz
Intel 845GLLY Motherboard ([http://support.intel.com/support/motherboards/desktop/D845GLLY/LY_manual.htm](http://support.intel.com/support/motherboards/desktop/D845GLLY/LY_manual.htm))
384MB RAM (SDRAM 133 MHz)
HDD - 80GB IDE
LG DVD RW
LG 17' TFT monitor at 1280x1024

_My Software Configuration:_
Video driver is xserver-xorg-video-intel.
This was selected automatically while installing. I've not changed any configurations.

I have a very similar configuration to you (a Dimension 1100 with no AGP or PCI-E slots). I got a GeForce FX 5200 PCI (3D: was ok in Windows, slow in Linux). I later upgraded to a GeForce 6200 PCI (3D: good in Windows, adequate performance in Linux). What you need to know: both of these cards have *slower* 2D performance than an Intel integrated chipset (in my case, Intel 865G) in Linux.

Let's forget about purchasing a graphics card for a moment. The intel driver on Intrepid has performances issues due to the default configuration being suboptimal. You can improve 2D performance somewhat.

Edit /etc/X11/xorg.conf. In the "Device" section, test **one** of these lines at a time (they don't work well together):

```
Option "ExaOptimizeMigration" "true"
```
OR:
```
Option "MigrationHeuristic" "greedy"
```

Either of these options will dramatically improve 2D performance, and Compiz will be a lot smoother (especially scrolling). I use the first line to improve performance on my laptop with an Intel 855GM chipset - even Compiz is bearable, but I prefer to disable Desktop Effects for performance reasons. *You should consider this too*.

There are a few other options you can add to *possibly* improve 3D performance, including "TripleBuffer" and "PageFlip" - see the "man intel" page.

---

### Post by rajkumarm2 on 2008-11-16
Thank you **psyke83** for the reply.
With ***Option "MigrationHeuristic" "greedy"*** I got slight improvement, especially scrolling. But I'm still not satisfied with the results.

---

### Post by shof2k on 2008-11-16
There is a known issue with Intel cards within xorg for intrepid described at [http://www.ubuntu.com/getubuntu/releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810").

I've changed xorg.conf as discussed but this still takes up all my CPU when doing trivial things.  I will run some tests, but continue to use Hardy as my main machine.

On the Card front, I've tried Ubuntu Hardy on my other machine with an Nvidia 6800GTS card and performance is fine.

---

### Post by psyke83 on 2008-11-16
> **rajkumarm2 said:**
> Thank you **psyke83** for the reply.
With ***Option "MigrationHeuristic" "greedy"*** I got slight improvement, especially scrolling. But I'm still not satisfied with the results.

Disable Desktop Effects (System/Preferences/Appearances). Your chipset is simply too old to accelerate these effects smoothly. If the improved DRI2/GEM drivers are ready, then Jaunty may improve your situation when it's released, but there's no guarantee.

If you choose to go for a graphics card, remember that you've already been warned you that 2D performance would suffer... ;) If I were in your situation, and buying a new PC was out of the question, I would possibly buy an NVIDIA card - but only to play games. The problem is that your CPU is too underpowered to gain the real benefit from the graphics card (and since PCI transfer bandwidth is so low, the CPU still plays a factor in graphics performance).

---

### Post by rajkumarm2 on 2008-11-16
> On the Card front, I've tried Ubuntu Hardy on my **other machine** with an Nvidia 6800GTS card and performance is fine.
Thanks **shof2k**.
Does your *"other machine"* have a configuration similar to my PC?

---

### Post by rajkumarm2 on 2008-11-16
> Disable Desktop Effects...
Thanks psyke83.
Desktop effects were already disabled. It was done before I started this thread.
> If you choose to go for a graphics card....
I guess I should wait till I have enough money to upgrade my PC :(

---

### Post by shof2k on 2008-11-17
It's not too far from yours.  Best thing, as mentioned, is to try the live CD.  If that works OK then it should be safe to install.

---

### Post by rajkumarm2 on 2008-11-19
Thanks **shof2k**.
> Best thing, as mentioned, is to try the live CD. If that works OK then it should be safe to install.
Please explain. I didn't understand your point.

---

### Post by psyke83 on 2008-11-20
> **shof2k said:**
> There is a known issue with Intel cards within xorg for intrepid described at [http://www.ubuntu.com/getubuntu/releasenotes/810]("http://www.ubuntu.com/getubuntu/releasenotes/810").

I've changed xorg.conf as discussed but this still takes up all my CPU when doing trivial things.  I will run some tests, but continue to use Hardy as my main machine.

On the Card front, I've tried Ubuntu Hardy on my other machine with an Nvidia 6800GTS card and performance is fine.

You're using an AGP or PCI-E card.

There's a *major* difference in performance between PCI and AGP/PCI-E, so your experience will not match the original poster's. 

Also, the best PCI card on the market is the NVIDIA GeForce 6200, which is a lot slower than your card (ignoring the limitations of PCI bus transfer speed).

---

