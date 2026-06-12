---
title: "Installing a new video card."
date: 2006-05-23
forum: Multimedia &amp; Video
---

### Post by AceRimmer on 2006-05-23
Hello all.  I'm a new person to Ubuntu and I have a problem.  I took out my ATI Radeon 9000 Pro and replaced it with a Nvidia GeForce 6600GT card.  Now I can't get the GUI to load.  I get an error message and from what I can tell its looking for the old ATI card and since it can't find it I can't get further.  I can get a command prompt but I'm not sure how to fix this in Linux. 

Thanks for any help.

---

### Post by johnc4510 on 2006-05-23
Try this:
sudo apt-get install nvidia-glx
sudo nvidia-glx-config enable
You may have to reboot for changes to take effect.

---

