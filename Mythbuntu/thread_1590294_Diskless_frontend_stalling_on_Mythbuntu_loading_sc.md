---
title: "Diskless frontend stalling on Mythbuntu loading screen"
date: 2010-10-07
forum: Mythbuntu
---

### Post by Zifnab966 on 2010-10-07
I have an old Thinkpad T43 laptop that I'm trying to get running as a diskless frontend for the latest version of Mythbuntu. I have a desktop running Ubuntu 10.04 that I've installed the Mythbuntu packages onto, and I have the backend running fine. I followed [this guide]("http://www.mythbuntu.org/wiki/network-boot-mythbuntu-diskless") to set up the network boot, and everything seems to be working properly up to a point.

The laptop boots, pulls down the image, and starts loading Mythbuntu. Once it gets to the loading screen, it will sit and play the animation indefinitely. I've let it sit for about an hour and it goes nowhere, so I'm assuming I'm not just being impatient. 

The log files in /var/log don't seem to have anything in them, unless I'm checking the wrong log. I've looked through a number of similar threads on here, but none of the solutions in them work/are applicable.

I'm limited to a diskless boot because the laptop fell prey to the IDE controller issue that so many of the T43s had. Where can I go from here to troubleshoot this?

---

### Post by Zifnab966 on 2010-10-11
Well, I tried building a PXE boot image of Ubuntu from the same server, and the laptop boots just fine into the Ubuntu desktop. This says to me that there is some sort of issue with the image being built of Mythbuntu.

Does anyone have any experience with this? I've been Googling for days and am still dead in the water. Even an idea of where this might be logged would be great so I have something to check.

---

