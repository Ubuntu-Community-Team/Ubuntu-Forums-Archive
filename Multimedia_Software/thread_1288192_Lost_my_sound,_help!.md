---
title: "Lost my sound, help!"
date: 2009-10-11
forum: Multimedia Software
---

### Post by Camilia on 2009-10-11
Since I did some upgrades I don't have sound. Went [to ]("http://ubuntuforums.org/showthread.php?t=205449")Comprehensive Sound Problem Solutions Guide

Pasted aplay -l in terminal and got my card
List of PLAYBACK Hardware Devices ****
card 0: CK8 [NVidia CK8], device 0: Intel ICH [NVidia CK8]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: CK8 [NVidia CK8], device 2: Intel ICH - IEC958 [NVidia CK8 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

Pasted alsamixer in the terminal and raised all of the volumnes

Went to [Jaunty 9.04]("http://ubuntuforums.org/showthread.php?t=1130384") Sound Solutions and downloaded the programs.

Did
sudo apt-get install libgstreamer-plugins-base0.10-dev


What else can I do?

---

### Post by khelben1979 on 2009-10-11
I know what you can try:

1. Open up the [Synaptic Package Manager]("http://en.wikipedia.org/wiki/Synaptic_package_manager").
2. Search for kernel.
3. Tick your present installed kernel for uninstallation and make a tick on the previous version which worked fine before.
4. Install and reboot.
5. Take a break.

Other than this, if the Grub boot menu still gives you the option on choosing the older kernel version, try this first.

---

### Post by Camilia on 2009-10-11
> **khelben1979 said:**
> 
Tick your present installed kernel for uninstallation and make a tick on the previous version which worked fine before. 


How do I find out what I had before?

> **khelben1979 said:**
> 
Other than this, if the Grub boot menu still gives you the option on choosing the older kernel version, try this first.

Tried another version still no sound. I get a beep when I log of thus problem is software.

---

### Post by onespeedbiker on 2009-10-11
> **Camilia said:**
> How do I find out what I had before?



Tried another version still no sound. I get a beep when I log of thus problem is software. I hate to mention the obvious, but I lost my sound once and noticed the little speaker in the upper right hand corner had a red "x" in front of it. I right clicked on the speaker and saw something I had done had switched it to mute mode. Sorry if that's the first thing you checked, but I'm new to ubuntu and it took me about 1/2 hour to figure it out.

---

### Post by Camilia on 2009-10-11
> **onespeedbiker said:**
>  I lost my sound once and noticed the little speaker in the upper right hand corner had a red "x" in front of it. I right clicked on the speaker 

I am still getting use to ubuntu, thus the obvious sometimes applies to me. I had seen that after I did an upgrade. I removed it from the panel.  

Went into the main menu and added the sound options.  Adjusted the volume and now have sound. 

These upgrades keep messing with my computer.  For example my printer printed blank pages for a while.

Thanks onespeedbiker

---

### Post by onespeedbiker on 2009-10-12
> **Camilia said:**
> I am still getting use to ubuntu, thus the obvious sometimes applies to me. I had seen that after I did an upgrade. I removed it from the panel.  

Went into the main menu and added the sound options.  Adjusted the volume and now have sound. 

These upgrades keep messing with my computer.  For example my printer printed blank pages for a while.

Thanks onespeedbiker Great! Glad I could help. BTW, I started with 9.04 and it seemed buggy so I went back and found 8.10. I really don't know if it's any better, but I decided to stick with it until April 2011 when support stops. I figure once I get ubuntu stable and working, might as well stay with what works, unless there is some issue that is addressed in an upgrade. This might relieve some of your upgrade stress.

---

