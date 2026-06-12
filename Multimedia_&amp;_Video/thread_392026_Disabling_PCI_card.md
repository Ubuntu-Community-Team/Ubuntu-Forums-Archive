---
title: "Disabling PCI card"
date: 2007-03-24
forum: Multimedia &amp; Video
---

### Post by jord1242 on 2007-03-24
First time poster, I did a search and look through to find my issue, to no avail. So if anyone can shed some light on what to do, I would appreciate it. Thank you.

I have a setup where I have an AGP Matrox dual-head (which Ubuntu recognizes) and a PCI S3 Virge graphics card (again, which Ubuntu recognizes). Upon bootup, my BIOS works correctly and defaults to the AGP card (which I want it to), but when Ubuntu loads and the login screen comes up, it switches over to the PCI card (so I have to manually switch the graphics plug from the AGP to the PCI).

I want to disable the PCI card so that Ubuntu always uses the Matrox dual-head card. I have tried removing the PCI card, and after the BIOS screen, it goes blank (as if it is still trying to switch to the PCI card).

is there any way in the device manager to disable the PCI card? Sorry for the noob question, tried everything to get it working. 

Thanks again for anyone that can shed some light on it.

JJ

---

### Post by teaker1s on 2007-03-25
possibly, 
remove one  card and boot recovery kernel
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by jord1242 on 2007-03-25
Hey thanks a lot. That did the trick. although I had to throw in an old Nvidia card. For some reason, when I ran the reconfig, Matrox was not one of the options to choose, and I tried a couple, but none of them worked (actually threw an error about a problem with the xorg.conf).

Also, if anyone knows of a way to get a higher resolution rate for me on my card then 1024x768, let me know. I tried editing the xorg.conf file, adding 1152x864 but when I look at available resolutions on restart, it doesn't show as an option.

Thanks again for your help! I am up and running with one graphics card.

JJ

---

