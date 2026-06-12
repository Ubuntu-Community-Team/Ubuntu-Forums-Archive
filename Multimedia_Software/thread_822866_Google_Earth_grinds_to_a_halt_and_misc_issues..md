---
title: "Google Earth grinds to a halt and misc issues."
date: 2008-06-08
forum: Multimedia Software
---

### Post by kangarooman1 on 2008-06-08
Hello mates

I installed google earth on my Hardy running on my Opteron x64. I have found it to be incredibly slow and after sometime it grinds to an absolute halt. the display freezes !

I also found the same problem with my Ant Spotlight screen saver, where the Ant grinds to a halt ! And I had to do a hard reboot.

My suspicion is on my graphics driver:
- My graphics card is: 
$ lspci | grep VGA
05:00.0 VGA compatible controller: nVidia Corporation NV41GL [Quadro FX 1400] (rev a2)

- I have "Nvidia accelerated graphics driver" enabled in the Hardware Drivers configuration.

- I had already installed the Nvidia-glx-new package through Synaptic.

Any help would be much appreciated.

Thanks
kangarooman.

---

