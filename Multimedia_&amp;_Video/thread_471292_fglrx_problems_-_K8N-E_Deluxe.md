---
title: "fglrx problems - K8N-E Deluxe"
date: 2007-06-11
forum: Multimedia &amp; Video
---

### Post by saggio on 2007-06-11
I've tried just about everything to get fglrx to work on my system properly. I've done the simple enable-restricted-drivers in GNOME, I've tried to manually install via apt and via ati.com, and still I have been unable to get fglrx loaded and working! I read on one of the various howtos that I found online that there is a problem with the ASUS K8N-E Deluxe boards (specifically the nForce3 chipset) that required an update bios - so I flashed my bios and updated to the latest version (which was supposed to fix my issue), but still nothing has happened!

Please, I don't have the money to buy a new nVidia card just to get 3D working. I need help!

Thanks.

---

### Post by MCSE_Crossover on 2007-07-02
I just fixed this issue with mine. I run an Asus K8N with an ATI 9800PRO. I would try to install the ATI drivers via Envy ([http://www.albertomilone.com/index.html](http://www.albertomilone.com/index.html)). That configured everything for me properly as far as the driver was concerned and left little to question.

The next big hicup was actually with the Bios. It appears as though the only bios that detects the AGP/PCI bridge configuration correctly is the BETA 1012 bios (which I could not find for download) OR downgrading to the 1006 bios. I was running the 1011 bios and when I would type "fglrxinfo" at the command line, it would consistently tell me that the OpenGL information was run by Mesa 3D instead of ATI Technologies. I was not getting appropriate framerates either. As soon as I downgraded my bios to the 1006 and rebooted, everything came up fine! I would give that a whirl...hopefully it works.

My board is the nForce3 chipset as well...which is apparently a P.O.S.

---

### Post by newbie2 on 2007-07-03
[http://ubuntuforums.org/showthread.php?t=490937](http://ubuntuforums.org/showthread.php?t=490937)

---

