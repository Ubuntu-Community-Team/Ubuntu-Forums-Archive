---
title: "Resolution Problems"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by ukulele_ninja on 2007-07-19
Im having an issue with my screen resolution. While trying to get beryl to work, I lowered my screen res to see if it would work with a lower res (it didnt) When I restarted it was still on the 480X650 resolution and when I bumped it back up to the highest resolution, it went all wacky and glitchy. I tried restarting but to no avail. What could be causing this?

I thought maybe my video drivers or something were bad, I have the ATI Radeon Xpress 200M and I did download and install the drivers but I dont know how to check if they are doing what they need to be doing correctly.

Any ideas on fixing the resolution and making it pretty again? It looks like a fat kid took a dump on my screen right now and I dont like it...

---

### Post by yabbadabbadont on 2007-07-19
Try booting in recovery mode.  You may have to hit the escape key when grub first loads in order to get to the menu.  Then at the command prompt, run ```
sudo dpkg-reconfigure -p high xserver-xorg
```  When you are done, reboot (just run "sudo reboot" without the quotes) and you should have the same setup that you had right after you first installed.

---

### Post by ukulele_ninja on 2007-07-20
> **yabbadabbadont said:**
> Try booting in recovery mode.  You may have to hit the escape key when grub first loads in order to get to the menu.  Then at the command prompt, run ```
sudo dpkg-reconfigure -p high xserver-xorg
```  When you are done, reboot (just run "sudo reboot" without the quotes) and you should have the same setup that you had right after you first installed.

Problem solved! Thank you so much!

---

