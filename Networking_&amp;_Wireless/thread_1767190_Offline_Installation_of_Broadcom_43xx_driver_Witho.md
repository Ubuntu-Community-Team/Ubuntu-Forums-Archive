---
title: "Offline Installation of Broadcom 43xx driver Without CD"
date: 2011-05-25
forum: Networking &amp; Wireless
---

### Post by Denizen08 on 2011-05-25
Hi Everyone,

I'm having problems installing the drivers after doing an install using WUBI.

I no longer have the installation disc for 10.10 as I had to reformat my HD after having problems with my Win7 and Ubuntu installation (on separate partitions), so I did this set up so they can co-exist better on the single HD. It's a bit of a long story, so that's the short version.

My particular problem is that I am unable to install the drivers needed because I had let WUBI download the disc and after installation I couldn't locate it on my HD. It must have been removed right after installation. I have a copy of the contents on a bootable USB, but I don't know how to point the system/repository to it. So I'm sure I have the all the required materials to make this happen. I just don't know how.

I've located the driver in the media/usb/pool/restricted/ folder, but synaptic/software installer insists on downloading the dependencies even if I don't have internet. I checked the CDROM option of in the repositories panel, but it can't locate the disc.

Can anyone tell me which dependency files are needed and the command to install them, if need be. I'm so sorry. I am still very new to linux, but I am quite satisfied about using it as my working environment.

Thank you very much! :)

---

### Post by Denizen08 on 2011-05-25
Got it running. Having written this post got me thinking clearer. :)

Thanks to synaptic's error reporting I got the filenames of the dependencies I needed so I just followed the breadcrumb until I got it running.

Thanks to Ubuntu's excellent team! :D

---

