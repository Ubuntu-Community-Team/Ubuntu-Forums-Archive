---
title: "Myth problems after Oct 4 update"
date: 2009-10-06
forum: Mythbuntu
---

### Post by mookie60 on 2009-10-06
old dell 2.3ghz
512 ram
mythbuntu 9.04
nvidia geforce 6200
hauppauge 1600 & 150


myth had been running well for months.   on Oct 4 I did an update (last update about 2 wks prior); not sure what was included, but it was a large update and required a reboot.  after the reboot i can no longer "watch tv" (it just bounces back to the home screen without producing any error msg), nor will it record.

one of the cards (likely the 150) seems to be stuck in an attempt to record something.   after every reboot it attempts to record fox (ch 14, the last one properly recorded) even though nothing is programed to record.  the little preview window (in "watch recordings") is blank and it errors when i attempt to watch it. 

as i've had problems with the system sometimes losing the 1600, i've tried resetting the backend's card setup to v4l, the back to mpeg2 - this has helped in the past, but not now.  the backend seems to find and identify the cards correctly, and rescanning the channels seemed normal.   

i've seen posts where "klc5555" has mentioned trying "sudo rmmod cx18, sudo modprobe cx18" - tried it but it didnt' help.   i did get the following error when using "sudo modprobe cx18" - "warning: all config files need .conf: /etc/modprobe.d/oss-compat. it will be ignored in a future release."   i don't know whether this is significant.

though i always worry whether the 1600 will revive properly after a reboot, it doesn't seem to be the problem this time as neither tuner card can be used to record or watched live.  

thanks in advance for any suggestions,

john

---

### Post by mookie60 on 2009-10-06
it's fixed.   i omitted the fact that i had also added a new storage group (first attempt).   it was simple enough and seemed to be setup correctly - i guess i need to look into how that drive is mounted.  so, i just deleted the storage group and all is well.

reminder to self - make one change at a time

J

---

### Post by novellahub on 2009-10-08
> **mookie60 said:**
> it's fixed.   i omitted the fact that i had also added a new storage group (first attempt).   it was simple enough and seemed to be setup correctly - i guess i need to look into how that drive is mounted.  so, i just deleted the storage group and all is well.

reminder to self - make one change at a time

J

Make sure your new storage group is writable (chmod 775) and mythtv has rights to is (chown).  See the examples here:

[http://ubuntuforums.org/showpost.php?p=6965380&postcount=2](http://ubuntuforums.org/showpost.php?p=6965380&postcount=2)

---

