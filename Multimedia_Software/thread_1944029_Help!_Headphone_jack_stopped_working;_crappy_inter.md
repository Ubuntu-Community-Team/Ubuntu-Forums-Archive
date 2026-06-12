---
title: "Help! Headphone jack stopped working; crappy internal speakers still work"
date: 2012-03-20
forum: Multimedia Software
---

### Post by Dave.G on 2012-03-20
I don't know the precise moment when this started today, but I suspect it was after restoring from hibernation. My decent little external speakers are plugged into the headphone jack on my Dell Latitude E5400 laptop and they don't work anymore. I've tried plugging in headphones and they don't work either. When anything is unplugged the crappy internal speakers come on. I'm running Kubuntu 10.04.

The first thing I tried was to update everything, which I hadn't done it too long. After that I found [this other thread](http://ubuntuforums.org/showthread.php?t=1774627) and tried adding all of the following to my /etc/modprobe.d/alsa-base.conf
options snd-hda-intel model=auto
options snd-hda-intel model=dell-laptop
options snd-hda-intel model=laptop
options snd-hda-intel model=laptop position_fix=1 enable=yes

I've also tried the giant command in step 1 [in the troubleshooting page](https://help.ubuntu.com/community/SoundTroubleshootingProcedure) but I'm now wondering if it was not applicable to Kubuntu.

My alsa info is here:
[http://www.alsa-project.org/db/?f=0abf7e3fc0983ed436c8884d19ad7fe8a6f31b71](http://www.alsa-project.org/db/?f=0abf7e3fc0983ed436c8884d19ad7fe8a6f31b71)

Every once in a while when I boot up this laptop it doesn't load up in the correct screen resolution. It's fixed with a reboot. Every once in a while the touchpad doesn't get detected correctly, thus breaking the cursor speed and re-enabling the evil that is tap-to-click. Again, it's fixed with a reboot. There is clearly something crappy in its hardware detection, which is why I expect this sound issue to be on the same line.

Please help. The built in speakers are utter garbage.

---

### Post by Dave.G on 2012-03-20
Um... I don't know what happened. I rebooted about a dozen times in the course of trying things earlier, but now when I turn it on the sound is back. It's working now but I'm not going to declare this "solved" as I'm worried it'll happen again and would like to fix that if anyone knows what I need to fix.

*Edited to add:*
Ok, obvious next step: get the alsa info again and diff the two. Here's the new one with it currently working:
[http://www.alsa-project.org/db/?f=95aa3221bbac9d5b26fb673dcaa67bf10a05d568](http://www.alsa-project.org/db/?f=95aa3221bbac9d5b26fb673dcaa67bf10a05d568)

Ignoring some different times in the logs, there are two differences. The first is that "All Loaded Modules" shows "ricoh_mmc" is now loaded where it was not before. (the list is also reordered) The first hit on a Google search for this is the things's source. It is self described as "a conceptually ridiculous driver" which is a nice way of saying that it's an inglorious hack to disable a useless bit of hardware that interferes with things... nothing having to do with the sound card, one would think.

The other difference is "ALSA/HDA dmesg" at the bottom:

not working:
```
[    6.023134] vga16fb: not registering due to another framebuffer present
[    6.094173] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[    6.094204] HDA Intel 0000:00:1b.0: setting latency timer to 64
[    6.242814] Console: switching to colour frame buffer device 106x30
[    6.283402] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[    6.358593] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    6.358704] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    6.358769] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[    7.094444] composite sync not supported
```
working:
```
[   11.391205] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.391260] HDA Intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   11.391294] HDA Intel 0000:00:1b.0: setting latency timer to 64
[   11.394762] vga16fb: initializing
--
[   11.412451] EXT4-fs (sda6): mounted filesystem with ordered data mode
[   11.499582] input: HDA Digital PCBeep as /devices/pci0000:00/0000:00:1b.0/input/input10
[   11.522686] input: HDA Intel Mic at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   11.522893] input: HDA Intel Line Out at Sep Left Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   11.523081] input: HDA Intel HP Out at Ext Right Jack as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   11.666338] Console: switching to colour frame buffer device 180x56
```
If anyone has a clue as to what's going on here, it would be nice to know.

---

