---
title: "Radeon driver issues (ATI 200m) Karmic"
date: 2010-02-06
forum: Multimedia Software
---

### Post by lavinog on 2010-02-06
I had an issue recently with my laptop trying to suspend and failing, loosing all of my work.  I don't know why it suspended (thought I had it disabled) but I have decided to attempt to get suspend to ram to work.

It appears the problem has to do with the open source radeon driver:
```

Package: xserver-xorg-video-radeon
State: installed
Automatically installed: no
Version: 1:6.12.99+git20090929.7968e1fb-0ubuntu1

```
```

01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)

```

The computer will suspend, but upon resuming, the screen is blank, and the system freezes requiring me to hold the power button to turn off.

I tried the nomodeset option on the kernel line but it didn't fix it.

I also noticed some new settings for the radeon driver:
```

       Option "R4xxATOM" "boolean"
              This option enables modesetting on R/RV4xx chips using atombios.  The default is off.

       Option "ClockGating" "boolean"
              Enable dynamic clock gating.  This can help reduce heat and increase battery life by reducing power usage.  Some users  report  reduced  3D
              performance with this enabled.  The default is off.

       Option "ForceLowPowerMode" "boolean"
              Enable a static low power mode.  This can help reduce heat and increase battery life by reducing power usage at the expense of performance.
              The default is off.

       Option "DynamicPM" "boolean"
              Enable dynamic power mode switching.  This can help reduce heat and increase battery life by reducing power usage when the system  is  idle
              (DPMS active). The default is off.


```

Enabling DynamicPM caused the display to not come up if the splash was displayed at boot...replacing splash with verbose let it boot just fine.

I tried enabling and disabling R4xxATOM and suspend still failed.

Anyone have any ideas or any luck.  Maybe compiling a new driver is what I should do.

It isn't a major deal for me to get suspend working, but it would be a nice change.

---

### Post by mushwars on 2010-02-06
Laptops and linux I hate to say it are not a good combo because of the screen. It has to do with how the kernel is compiled, wheather is has acpi support for display suspention, for me my display suspends just fine, but if I close my screen, I have to switch over into a tty and ( without being able to see anything because the screen is off ) log on as root and reboot.

I am too lazy to recompile my kernel is the problem, but in ubuntu you can to that, I would first try installing the proprietary driver, the fglrx one, in the restricted driver menu.

That will allow you to have the real driver, and that might in and of itself fix your suspention problem.

I wish the /var/log/Xorg.0.log would tell us info about our display problems, but the problem is strictly hardware, and not software.

---

### Post by pme 72 on 2010-02-06
Take a look at this post:
[http://ubuntuforums.org/showthread.php?t=1113768](http://ubuntuforums.org/showthread.php?t=1113768)

I had the same problem with my ATI x1550 card in my desktop in 8.10 Intrepid Ibex with the open source Radeon driver. I could hear the machine startup but the display would remain in sleep mode. 

The previous poster recommended trying to install the proprietary driver from the restricted driver menu. I believe you will find that it is not available. The proprietary restricted driver for the 200M was last available from Ubuntu in 8.10. There were changes made to later distributions that made the fglrx driver for the 200M incompatible. I have read posts from 200M owners who have attempted to load the 9.3 legacy driver from the ATI website and they have universally gotten an incompatible message.

---

### Post by Melcar on 2010-02-06
Compaq Presario V2000 here (200M chip).  I'm currently using xorg-edger packages, the latest 2.6.32 kernel from the kernel ppa, kernel modsetting, and my laptop suspends and resumes fine.  I found that suspend and hibernation just did not work without KMS, but with it on I had to update the kernel for proper modsetting.  By the way, suspend never did work for me with the proprietary drivers.

---

### Post by lavinog on 2010-02-06
Thanks for the info Melcar.  I kind of figured that was going to be the best solution.
@pme 72: Thanks for the link, I will give that a try too.

---

### Post by pme 72 on 2010-02-12
I pulled the x1550 out of my machine and enabled the onboard ATI Radeon Xpress200 card to see if the fix would work in Karmic. Although it did work in Intrepid Ibex the fix did not allow me to wake from Suspend in Karmic 9.10. The integrated card is an RS480 series 200G.

---

### Post by SonOfOdin on 2010-04-01
My Metabox 722 laptop has the ATI Radeon XPRESS 200M 5955 (PCIE) which is onboard/integrated, running U-8.10_II and have been having all manner of problems trying to configure it to run decent resolution across two monitors.  Suspend luckily has not ever been an issue.

In 8.10 the support out of the box is ok, I get both monitors to work easily and the resolution doesnt suck, however the system runs no visual effects.

When running the fglrx I fall back to mirrored display, the monitors are unknown and the system without fail freezes completely, requiring a hard shutoff, after about 45 seconds of X finishing loading (just enough time to unload the hardware drivers and revert back to opensource.)

Have tried envyng (Synaptic) and xorg.edger + compiling to no avail.

No sign of driver updates at the AMD website so I figure this is going to be as good as it gets until I can afford a new machine or until better support is offered by the community.  Unfortunately Im just an (ab)user, not a guru so I cant fix it (by writing my own drivers etc) myself.

---

### Post by lavinog on 2010-04-01
> **SonOfOdin said:**
> My Metabox 722 laptop has the ATI Radeon XPRESS 200M 5955 (PCIE) which is onboard/integrated, running U-8.10_II and have been having all manner of problems trying to configure it to run decent resolution across two monitors.  Suspend luckily has not ever been an issue.
...
No sign of driver updates at the AMD website so I figure this is going to be as good as it gets until I can afford a new machine or until better support is offered by the community.  Unfortunately Im just an (ab)user, not a guru so I cant fix it (by writing my own drivers etc) myself.

Support for 8.10 ends this month, and any newer version is not compatible with the old fglrx drivers.  New fglrx drivers do not support the 200m so the open source driver will be the only way to go.

I have installed Lucid beta on my laptop, and suspend works...but now resume is borked.  I have been debugging the resume slowly but surly, but other unrelated bugs have been hindering the debug procedure.

---

