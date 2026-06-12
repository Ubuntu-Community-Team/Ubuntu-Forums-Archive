---
title: "Latest Nvidia Driver(169.12)"
date: 2008-03-09
forum: Multimedia &amp; Video
---

### Post by survient on 2008-03-09
Ok, I was able to get back up and running my x server with the nvidia drivers after many long and frustrating hours of messing with my modules, xorg.conf file, and nvidia installer files. Right now I'm running with a manually installed nvidia driver that was off the site awhile back, version 100.14.19, which seems to be the latest in the gutsy modules. What interests and slightly confuses me is that I can run the latest installer (ver 169.12) off the nvidia website, restart the X server, and have everything run fine, but when I restart the computer overall, it gives me a module mismatch error, which I assume is the nvidia module included in the gutsy modules being loaded instead of the one that was manually built when I ran the nvidia installer. My question is, what would I have to do to install the latest nvidia driver and keep the default module from being loaded, and the custom built module instead to be loaded, so I don't have to keep reinstalling the driver each time I boot. I know it works because after I install it it runs fine, but after a restart I have to reinstall the driver over. Also, I am running Ubuntu Studio with the rt kernel if it matters.

---

### Post by erginemr on 2008-03-10
Please follow this thread:
[http://ubuntuforums.org/showthread.php?t=691371](http://ubuntuforums.org/showthread.php?t=691371)

and follow what PmDematagoda suggested about disabling Ubuntu's NVidia module.

---

