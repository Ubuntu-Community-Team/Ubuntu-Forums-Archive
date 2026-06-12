---
title: "Uninstall ATI/AMD drivers from CLI in Natty"
date: 2011-03-19
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by Ben Page on 2011-03-19
Hey Guys, need help!

I am testing 11.04, and I get occasional graphics card fan spin ups, it's noisy. This happens on any distro when using open source fglrx ATI drivers. The card is HD 3850 PCIe.

So I decided to install the proprietary ATI/AMD drivers, since I found a couple of threads that describe them as "stable" in 11.04. Installation went fine, but I got a couple of errors, checked the log, but there are only "numbered errors" so I can't really see what went wrong. Anyway, my 11.04 install is rendered useless with these drivers, but the CLI works fine, how to remove these drivers from CLI, because I can't start X? I found instructions dating from 2007, but they don't work in 11.04. I need uninstallation syntax and reinstallation syntax for reinstalling the open source fglrx and libraries.

---

### Post by cariboo on 2011-03-19
You can use jockey-text to remove the driver at the command line to see what driver is loaded type:

```
jockey-text -list
```

On my system I get the following output from the above command:

```
jockey-text --list
xorg:nvidia_current - NVIDIA accelerated graphics driver (Proprietary, Enabled, In use)
```

To disable the driver the following command would be used:

```
jockey-text -d nvidia-current
```

---

### Post by Harry33 on 2011-03-19
> **Ben Page said:**
> Hey Guys, need help!
...
So I decided to install the proprietary ATI/AMD drivers, since I found a couple of threads that describe them as "stable" in 11.04.
...


Well I wonder how "stable" those threads are. Perhaps back from the time before xserver 1.10.
But with this new stable xserver 1.10 ATI proprietary drivers do not work ATM.
Use instead open source drivers:
xserver-xorg-video-ati

---

### Post by coffeecat on 2011-03-19
> **Ben Page said:**
> open source fglrx ATI drivers.

....

 reinstallation syntax for reinstalling the open source fglrx and libraries.

Let's get one thing straight otherwise you're going to be mightily confused by the link I'm posting. The 'fglrx' driver is the proprietary one, not the open source one. The open source driver is the 'ati' driver. Package description for xserver-xorg-video-ati package:

> This package provides the 'ati' driver for the AMD/ATI Mach64, Rage128,
Radeon, FireGL, FireMV, FirePro and FireStream series. This driver is
actually a wrapper that loads one of the 'mach64', 'r128' or 'radeon'
sub-drivers depending on the hardware.
These sub-drivers are brought through package dependencies.And package description for xserver-xorg-video-radeon:

> This package provides the 'radeon' driver for the AMD/ATI Radeon, FireGL,
FireMV, FirePro and FireStream series.

Note that this is not the same as the ATI-provided, binary-only, 'fglrx'
driver, which provides additional 3D functionality for some newer Radeon
cards, but is not supported.Now we've got that out of the way :), this is what you want:

[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

I suggest you go for the full monty "Problem:  Need to fully remove -fglrx and reinstall -ati from scratch" option.

---

### Post by Ben Page on 2011-03-20
Well, I tried with these instructions, followed them to the letter, no errors were displayed, everything went smooth, BUT still no cigar! :(

I still get the same symptoms, when I boot in verbose mode, I can't see anything unusual, there are no errors. When kernel and services load the text just blinks fast a couple of times and I am left hanging with nothing happening. I can still enter the CLI via ALT+CTRL+F2. When I try to startx, I get a long error(s) which practically says that there is no device on BUS this-and-that (fglrx says this). Ubuntu or xorg is trying to load settings from /etc/X11/xorg.conf. When I open xorg.conf, in here it says that the machine is still using "ATI proprietary drivers".

So I guess that I'm still using the proprietary drivers, or that Ubuntu - X is set to use them, but they are uninstalled?

Any ideas?

---

### Post by coffeecat on 2011-03-20
> **Ben Page said:**
> 
Any ideas?

When did you last update the system? There were some inconsistencies in the xserver packages within the last day or so  during the upgrade to xserver 1.10. See:

[http://ubuntuforums.org/showthread.php?t=1709374](http://ubuntuforums.org/showthread.php?t=1709374)

In particular:

> **Harry33 said:**
> For ATI cards, no suitable driver yet, the xserver-xorg-video-ati_6.14.0-0ubuntu3 is faulty.

Do you still have xserver-xorg-video-ati_6.14.0-0ubuntu3? xserver-xorg-video-ati 1:6.14.0-0ubuntu4 appeared yesterday and that's working OK on my system.

Those instructions I posted should have re-installed the latest xserver-xorg-video-ati package, but only if you did a sudo apt-get (or aptitude) update first.

---

### Post by zika on 2011-03-20
> **Ben Page said:**
> Well, I tried with these instructions, followed them to the letter, no errors were displayed, everything went smooth, BUT still no cigar! :(

I still get the same symptoms, when I boot in verbose mode, I can't see anything unusual, there are no errors. When kernel and services load the text just blinks fast a couple of times and I am left hanging with nothing happening. I can still enter the CLI via ALT+CTRL+F2. When I try to startx, I get a long error(s) which practically says that there is no device on BUS this-and-that (fglrx says this). Ubuntu or xorg is trying to load settings from /etc/X11/xorg.conf. When I open xorg.conf, in here it says that the machine is still using "ATI proprietary drivers".

So I guess that I'm still using the proprietary drivers, or that Ubuntu - X is set to use them, but they are uninstalled?

Any ideas?Try making it use open-source (in /etc/X11/xorg.conf) ```
Section "Device"
Identifier    "Configured Video Device"
Driver        "radeon"
EndSection
```Since I do not know how You've installed ATI proprietary driver, there are, at least, three ways to remove fglrx from Your system...
Most often I use Synaptic to remove fglrx... Check if xserver-xorg-video-ati is installed and, as I wrote, check (and force use of radeon, if necessary) xorg.conf... It should work...

---

### Post by coffeecat on 2011-03-20
> **Ben Page said:**
> When I open xorg.conf, in here it says that the machine is still using "ATI proprietary drivers".

Sorry, missed that. You don't need the xorg.conf file at all with the open source ATI driver. I didn't realise removing xorg.conf was missing from those instructions. Try deleting or at least renaming xorg.conf. Or try zika's edit.

---

### Post by Ben Page on 2011-03-20
Thanks for the help guys, but I'm still unable to get my GUI to run.

This may be a bug or an issue related to the Alpha nature of Nutty, I will report this bug in Launchpad.

---

### Post by jfernyhough on 2011-03-20
$ sudo apt-get purge fglrx
$ sudo rm /etc/X11/xorg.conf

This should be all you need to do.

---

### Post by zika on 2011-03-20
> **jfernyhough said:**
> $ sudo apt-get purge fglrx
$ sudo rm /etc/X11/xorg.conf

This should be all you need to do.There are situations where user have some important stuff in xorg.conf so I, personally, never propose removal of xorg.conf. Either editing or moving it to a safe place, for backup, until it is clear that it is not needed... Better safe than sorry...

---

### Post by jfernyhough on 2011-03-20
True, but if you're running ubuntu+1 the user /should/ know this already. :D

---

