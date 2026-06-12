---
title: "Screen tearing and undetected Radeon graphics"
date: 2013-02-18
forum: Multimedia Software
---

### Post by CPtAJ on 2013-02-18
I recently defenestrated this laptop and I'm having some issues with the graphics.

I'm seeing some pretty nasty screen tearing on this thing. I didn't notice any while the machine had windows 8 (a brief amount of time, admittedly) which leads me to suspect some kind of driver issue.

Googling led me to some tearing issues from ATI drivers and the new version of X but since most posts are a bit dated I don't know if that is what is happening to me.

The machine is a g6-2211nr model with an AMD A4-4300 APU and it's running 12.10.

The computer details dialog is showing "Driver: Unknown", this makes me wonder if the graphics adapter is even detected at all. I would like to try the open source drivers first if possible, but I dont know if they're being used or not right now.

Any ideas?

---

### Post by Bucky Ball on 2013-02-18
*Thread moved to **Multimedia & Video**.*

---

### Post by coffeecat on 2013-02-18
> **CPtAJ said:**
> The computer details dialog is showing "Driver: Unknown", this makes me wonder if the graphics adapter is even detected at all.

I don't know whether that should be called a bug or a package omission in the install CD, but if you install mesa-utils, you will see more information.

> **CPtAJ said:**
> I would like to try the open source drivers first if possible, but I dont know if they're being used or not right now.

If you haven't installed the proprietary fglrx driver, the open source radeon will be in use, but to be sure, post the output of this terminal command:

```
sudo lshw -c video
```


> **CPtAJ said:**
> AMD A4-4300 APU 

A google hit says that this APU has the Radeon HD 7420G graphics. I don't know how well this is supported by the radeon driver in 12.10.

---

### Post by wisecat on 2013-02-19
I have a similar issue, using Ubuntu 12.10 (amd64) with AMD E2-1800 APU with Radeon HD 7340 graphics.  My graphics card is listed as 'unknown', I also get slow video, and tearing.  I tried several other settings in my xorg.conf file (see my post about it here: [http://ubuntuforums.org/showthread.php?t=2117230](http://ubuntuforums.org/showthread.php?t=2117230) , notice the chart I made) but everything seems to go back to 'fallback' mode.

right now, graphics card is listed as 'unknown' and the output when I type: 
sudo lshw -c video

is:
*-display               
       description: VGA compatible controller
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:47 memory:e0000000-efffffff ioport:4000(size=256) memory:f0300000-f033ffff

I also tried going back one version of ubuntu (to 12.04), because it is rumoured that the Radeon drivers work well on 12.04, just not on 12.10 (due to 12.10 using a newer version of Xserver). I reformatted my hard drive and tried to install 12.04, but this was a complete failure, it cannot get through the install, because drivers for OTHER hardware pieces (the WIFI and the USB devices) cause it to freeze during the process. Your computer might not have this issue, though. I tried 4 times in a row, gave up, and just re-installed Ubuntu 12.10 and now I have to live with slow video, because apparentlyl there is no solution yet. Every post I can find on every forum (for Radeon 7xxx) ends with no resolution.

We need a solution, but it looks like one will be a long time coming. We might have to write our own driver. Argh.  I hope that my post helps you in some way, I'm not expecting any help for myself by posting these things here on your thread.

---

### Post by CPtAJ on 2013-02-20
Oh man, don't tell me that... Why do I always run into the unresolved goodies? brother...

Anyway, I installed the proprietary drivers. Upon reboot I reached the login screen and it looks flawless. However, after accessing my account, I can only see the desktop background and the mouse pointer. Nothing else.

I'll be trying to remove the drivers now.

edit: successfully reset everything. I'm back in but the screen tearing is back. I checked to see if the tearing appears during the login screen with this "working" configuration that uses the opensource drivers and no, tere is no tearing during the login screen no matter how hard I try to bring it about.

Here is the output of lshw -c video right now:

>   *-display               
       description: VGA compatible controller
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:48 memory:e0000000-efffffff ioport:3000(size=256) memory:f0300000-f033ffff


Aside from a fix, isn't there a way to just turn off hardware acceleration altogether? Just CPU render the whole thing?

---

### Post by CPtAJ on 2013-02-20
I installed 12.04, it has the same tearing under the open source drivers but this time the proprietary ones DID work. I think I'll leave it like this for now. Thanks for the help!

---

### Post by wisecat on 2013-02-23
Hmm..  I finally managed to get Ubuntu 12.04 LTS installed on my system.  However, still having problems with graphics drivers.  I tried using the proprietary ones from AMD website (AMD catalyst), installing using their script, with the  ' --force '  option  (because I can't seem to get rid of old flgrx drivers no matter how many times I try the remove commands).  I also tried using the 'Additional Drivers' program from System Settings.  Neither worked right.:

1) AMD Catalyst has two options: install ver 9.xxx for xserver (result: VESA:HONDO fallback), and 'Generate distribution-specific driver' which, when I select 'ubuntu' as the distribution, errors out and can't generate a driver.

2) both driver options from 'Additional Drivers' gives a VESA:HONDO fallback or a VESA:HONDO standard  result, after rebooting.

How did you install your proprietary drivers?

---

