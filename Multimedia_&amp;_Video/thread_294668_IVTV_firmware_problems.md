---
title: "IVTV firmware problems"
date: 2006-11-06
forum: Multimedia &amp; Video
---

### Post by pacadi on 2006-11-06
Hey!
I have been ](*,) with a WinTV PVR 350. Here is the deal:
I followed the instructions in this [thread]("https://wiki.ubuntu.com/Install_IVTV_Edgy") to get nthe ivtv driver working with a PVR 350 card and and a Via "epia m" board.

The first problem I ran into was that after the Edgy server install the system would not boot. I figured out that that was related to the server kernel being compiled for i686 (BTW that should be mentioned somewhere) and the epia m being an i586 architecture. I fixed this by booting from the Desktop live CD, chroot'ing into the server install and installing the 2.6.17.10-generic kernel, which is what I am running right now.

Then I followed the instructions to install the ivtv driver as well as its firmware (version 1.18.21.22254). When I modprobed ivtv, the system hung after a short while with the following message: "ivtv0: Error initializing firmware". I can't give a full log of what happened as the system froze and there was no log after reboot but once on the screen I was able to messages along the lines of: "encoder firmware dead!" and "decoder firmware dead!"

I tried several firmware versions including pvr_1.18.21.22254_inf.zip but no change. It just keeps hanging...:confused: 

Any idea anyone?
Again specs: Epia M, PVR350, Ubuntu server with kernel 2.6.17.10-generic.

Thanks for any help!!!

---

### Post by trubblemaker on 2006-12-06
not to good on this but I think that you need to copy the firmware, over the linked firmware in the ivtv, this howto shows you howto get [it up and running  on X on pvr-350 tv-out]("https://help.ubuntu.com/community/MythTV_Edgy_hardware_pvr-350_TV-out#preview")hope it helps you this howto shows you [howto get IVTV up ]("https://help.ubuntu.com/community/Install_IVTV_Dapper")and running and has the actual steps in it's trouble shooting section that I just refered to

---

