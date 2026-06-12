---
title: "[SOLVED] NVIDIA 6150 bye bye... stop cx18 driver"
date: 2008-05-11
forum: Multimedia Software
---

### Post by Sin@Sin-Sacrifice on 2008-05-11
So yeah.... I left a post 3 days ago about the cx18 driver killing my nvidia drivers and not one reply as to how to fix it came about so I did some thinking.... the ears smoked a bit but I finally thought to try other nvidia drivers and settings to see what I could do. I got a very blurry screen if not just the low grafix mode after reboot. So I replaced the xorg.conf file and deleted the proprietary cx23418 crap from the firmware file and rebooted again to find it hanging up when it ran the boot scripts. Well right above that line was a line saying the cx18 driver was still loading but getting an error because it couldn't find those files in the firmware folder I deleted. I used the modprobe -r command on it with sudo and in the root terminal and it's still trying to load. Don't know if that was what I was suppose to do to get it to stop but I read somewhere that it was..... anyone know how I can get that to stop all together? I have a feeling that if I can get cx18 to stop I'll get my wobbly windows and what-not back.

---

### Post by Sin@Sin-Sacrifice on 2008-05-12
So.... I, again, figured it out myself. Seems like I can't get a single reply on this site. Anyway... if you ever happen to come upon this problem you have to do the 2 makes. cd into the folder you made the cx18 installer in, type "sudo make clean", "sudo make uninstall", and then finally "sudo modprobe -r cx18". You also have to delete the firmware files added. I assume this would apply to any driver that messes with your system in a negative way. Depending of course upon how it was installed. Linux....Always a learning experience.....

---

### Post by 67GTA on 2009-02-21
This is an old thread I just found, but there is a solution: [http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia](http://ubuntuforums.org/showthread.php?t=1004660&highlight=cx18+nvidia)

---

