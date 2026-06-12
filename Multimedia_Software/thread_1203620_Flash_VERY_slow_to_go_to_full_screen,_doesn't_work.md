---
title: "Flash VERY slow to go to full screen, doesn't work once there"
date: 2009-07-03
forum: Multimedia Software
---

### Post by grsing on 2009-07-03
If I try to have YouTube or Hulu go full screen, it takes a very long time (about 2 minutes) to get there (first a white screen, then black slowly filling the screen from the top down, then the picture). Once it finally is full screen, it plays about half a second, then takes another minute or so to load the next 5 seconds. Running normally, inside the browser page, they work just fine. It's not my internet, because when I try the same videos on my netbook, they work fine (the problem computer is a Lenovo T61, discrete NVIDIA graphics, with the 180 version driver running). Other applications (VLC, rhythmbox visualization, etc) work just fine. And full screen flash worked fine before I installed 9.04 (clean install, not upgrade). Any ideas?

---

### Post by lovinglinux on 2009-07-03
Try [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567)

---

### Post by antiloop on 2009-07-03
Like it says in the link lovinglinux provided, try this: 
> sudo mkdir /etc/adobe
echo "OverrideGPUValidation=true" >~/mms.cfg
sudo mv ~/mms.cfg /etc/adobe/

Restart Firefox.

Fixed all my fullscreen flash problems. I am a NVIDIA user also. :guitar:

---

### Post by grsing on 2009-07-03
Thanks, that fixed it perfectly!

---

