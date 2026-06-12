---
title: "[SOLVED] SLI question...please pardon the ignorance"
date: 2007-08-12
forum: Multimedia &amp; Video
---

### Post by dweez on 2007-08-12
Ok, I've seen a few other posts regarding SLI but none seem to give a definitive answer.

Here's my setup.  Ubuntu 7.04 AMD64, AMD +3700 proc, Asus A8N-SLI Premium, 4x512MB DDR ram, 2x eVGA nVidia 7800 GT (256MB). Based on the nVidia settings panel, the driver version is 1.0-9755.

My question is how to enable SLI in Ubuntu.  An older thread ([http://ubuntuforums.org/showthread.php?t=43621](http://ubuntuforums.org/showthread.php?t=43621) ) from 2005 hinted that support for it should be available soon but no eta was given.  Searching the forums and google, I either don't find much pertinent info or I can't find the proper search string to use.

Any help/info is greatly appreciated and just let me know if I need to post more info about my system config.

-dweez

---

### Post by dweez on 2007-08-14
No one?

---

### Post by proalan on 2007-08-14
I'm not sure about the open source nvidia driver but SLI support is available with the installation of proprietory nvidia drivers.  But so far I've found no practical use for it in linux or linux gaming.

---

### Post by tseliot on 2007-08-15
type:
```
sudo nvidia-xconfig --sli=Auto
```

and restart the Xserver

---

### Post by dweez on 2007-08-19
Thanks tseliot, that did it.

---

### Post by dweez on 2007-09-01
Hmm, well tseliot, I've recently removed 7.04 A64 and installed 7.04 x86 instead.  I used your Envy program to install the nVidia driver then I used the line you gave above to enable SLI.  Well previously when I did that, SLI was enabled and I could see SLI options in the nVidia Settings console utility.  This time it isn't working...any ideas?

---

