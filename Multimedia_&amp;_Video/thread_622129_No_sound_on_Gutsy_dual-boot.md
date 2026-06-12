---
title: "No sound on Gutsy dual-boot"
date: 2007-11-24
forum: Multimedia &amp; Video
---

### Post by twin_57103 on 2007-11-24
Hi,
  I just dual-booted my Dad's laptop and I am having some of the same sound glitches as many others.  Sound works fine under Windows XP pro, but does not work under Ubuntu (Gutsy, standard install).  System specs: Dell Inspiron 8200, 1.2GHz, 512 Mb RAM.  Sound worked from the live CD and during installation, but failed after reboot.

I have tried to follow the various guides and forums, including [http://ubuntuforums.org/showthread.php?t=205449]("http://ubuntuforums.org/showthread.php?t=205449"), but am still having trouble.  I attempted to recompile the ASLA driver, but I'm not sure if I did it correctly (since it didn't work; I was also a little uncertain about the driver selection).  I'd appreciate any ideas or pointers!

Output of   lspci | grep Audio
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)

Output of   sudo lshw -C sound
  *-multimedia            
       description: Multimedia audio controller
       product: 82801CA/CAM AC'97 Audio Controller
       vendor: Intel Corporation
       physical id: 1f.5
       bus info: pci@0000:00:1f.5
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=Intel ICH latency=0 module=snd_intel8x0


Thanks!

---

### Post by mushroomcloudwarrior on 2007-11-24
```
 Originally Posted by professor fate  View Post
I was able to get the sound card working on a Dell Vostro 1400 with an Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


At the terminal type in: sudo gedit /etc/modprobe.d/alsa-base
Then paste this into the file: options snd-hda-intel model=5stack
```

---

### Post by twin_57103 on 2007-11-27
Thanks for the idea.  I will try this next time he and I are in the same place (he drives truck and I live 5 hours away) - probably Christmas.
twin_57103

---

### Post by twin_57103 on 2007-12-24
> **mushroomcloudwarrior said:**
> ```
 Originally Posted by professor fate  View Post
I was able to get the sound card working on a Dell Vostro 1400 with an Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)


At the terminal type in: sudo gedit /etc/modprobe.d/alsa-base
Then paste this into the file: options snd-hda-intel model=5stack
```

HI!  I've finally been able to work on this computer.  Unfortunately, it didn't help.  Can anyone offer any suggestions for this problem?
Thanks,
twin_57103

---

