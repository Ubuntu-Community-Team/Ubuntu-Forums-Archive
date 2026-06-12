---
title: "No internet whatsoever, wired or wireless on dell inspiron 1545. ubuntu 10.04"
date: 2010-10-03
forum: Networking &amp; Wireless
---

### Post by sam4673 on 2010-10-03
Hi
i am using a dell inspiron 1545 whith windows 7. I decided to try and duel boot it with ubuntu 10.04 and so dowloaded the iso disc image and burned the disc. I tried it out first booting from the cd and it seemed to work fine, but now i have installed alongside win7 i cannot get a glimpse of internet either wired or wireless. In the demo i was able to install drivers from an automated message in ubuntu. no such option has materialised in the full install. I am completely new to ubuntu but reasonably comfortable with windows. its a shame because i preferred the ubuntu desktop and general efficiency of the system. useless without internet though, please help, i am lost
many thanks
sam

---

### Post by spiky001 on 2010-10-03
If it worked on disc should work installed, go to System/Administration/software sources  tick the box down the bottom cd rom then it will ask to reload, I hope then that yo can update drivers from disc, To update drivers system administration hardware drivers, hope this works

---

### Post by sam4673 on 2010-10-03
Thank you for replying so quickly. I did what you said and got significantly further, the hardware driver has appeared as an option to install, but when i click activate it says, "sorry the installation of this driver has failed. please have a look at the log file for details.: /var/log/jockey.log" what next?

---

### Post by spiky001 on 2010-10-04
If it,s not to much bother maybe reinstall with eth0 cable in I have had 2 dell,s everything has worked straight away just seems strange eth0 not working, can you check the md5sum of the iso [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)  if it matches then the disc is good.

---

