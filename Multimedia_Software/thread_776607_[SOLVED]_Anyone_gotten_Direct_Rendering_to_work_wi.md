---
title: "[SOLVED] Anyone gotten Direct Rendering to work with a Radeon 9600 card?"
date: 2008-04-30
forum: Multimedia Software
---

### Post by herteljt on 2008-04-30
When I first installed Ubuntu (6.06) I configured my ATI Radeon 9600 card to work using the restricted ATI driver.  Everything worked fine.  I updated to 7.04 and had no troubles.  Then 7.10 came along and I lost it.  I thought the problem might go away with the update to 8.04 but alas I am still experiencing the pain of no direct rendering.  

Has anyone had similar issues with this card and gotten it to work properly?  I have been through all the tutorials I could find (including this one [https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")), changed my xorg.conf file quite a bit, tried Envy and nothing has seemed to fix my central issue of direct rendering.

Thanks for any insight!

---

### Post by CarpKing on 2008-05-01
I have an ATI 9600 as well.  I too had direct rendering using fglrx without issue in 6.06.  With 6.10 I switched to the open-source driver for Compiz support, and I had to add some modules to xorg.conf to get direct rendering working.  I tried the Feisty live CD and Gutsy and Hardy were fresh installs; with all of them it worked fine out of the box.  Now that fglrx supports Compiz I'm thinking about trying it out again to gain some speed, but I've yet to do so.  Unfortunately this means that I don't have any real help for you, but I will stop back here and report my results when I try it.

---

### Post by mc4man on 2008-05-01
> central issue of direct rendering.

On a dated p4 with a 9500pro i always had direct rendering on gutsy and hardy from using the open source drivers and from never going into appearences->visual effects. You can run some basic advanced effects from ccsm.

---

### Post by herteljt on 2008-05-07
Ok, after even more reading and resetting (only two reinstalls (let's just say you shouldn't try removing all the mesa drivers)) I have solved my problem.  

I installed the restricted driver and after a reboot ran 

dmesg | grep agp

and noticed that I had an "AGP not detected error."  This lead me to the following thread 

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/78684")

And the following fix:


Add lines to /etc/modprobe.d/blacklist:

blacklist i82875p_edac
blacklist edac_mc

I hope this can help some others out there.

---

