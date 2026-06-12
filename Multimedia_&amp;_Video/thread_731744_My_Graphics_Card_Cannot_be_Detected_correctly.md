---
title: "My Graphics Card Cannot be Detected correctly"
date: 2008-03-22
forum: Multimedia &amp; Video
---

### Post by mattrobinson999 on 2008-03-22
Ive just installed Ubuntu on my old computer and it was working perfectly until I enabled my correct driver for my graphics card (ATI Radeon 7600)
Now when ever, I reboot I get a message saying...
"Ubuntu is running in low graphics" (800x600)
I click onto the configure option and Ubuntu knows what graphics card I got but uses a "plug and play" monitor where I can only use 800x600 and also uses the "vese - Generic VESA-compliant videocards" instead of my real "ATI Radeon 7600"
Ive enabled the correct graphics drivers in Administration but Ubuntu still wont let me use my preferred 1280x1024.

Does anyone have any advice?

---

### Post by michaelaly on 2008-03-22
Try running Envy(link below), It's a script that finds and installs the proper video drivers, I've had very good results from it. I have had errors when running the restricted drivers as well, Envy fixed it. 

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mikewhatever on 2008-03-22
I'd say you need to reconfigure your xserver.

Reboot to the recovery mode, the second boot option.

Backup first <cp /etc/X11/xorg.conf /xorg.conf_backup>.

<dpkg-reconfigure xserver-xorg>

reboot with <reboot>

---

