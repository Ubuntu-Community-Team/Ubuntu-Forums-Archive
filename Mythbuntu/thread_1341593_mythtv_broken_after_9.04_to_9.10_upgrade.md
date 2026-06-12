---
title: "mythtv broken after 9.04 to 9.10 upgrade"
date: 2009-11-29
forum: Mythbuntu
---

### Post by gettingby on 2009-11-29
I just installed mythbuntu 9.10 (up from 9.04 where I was able to record from HDhomerun, look at previously recorded shows and watch tv. 64 bit intel processor) The filesystem that I was storing the videos was /media/disk/video. This was renamed (during the installation) to  /media/2C441D17441CE4FC. From the dir /media I used 
sudo mkdir disk
sudo mount --move 2C441D17441CE4FC disk
I changed the backend to point to /media/disk/video
and was able to see the video but no sound yet

then tried the myth front end and it still will not tune to the channel selected.
I noticed that the 2C441D17441CE4FC was recreated.
[http://mythbuntu.pastebin.com/f33f3f201](http://mythbuntu.pastebin.com/f33f3f201)

What can be done to restore my system to working again?
Here is the log   [http://mythbuntu.pastebin.com/f33f3f201](http://mythbuntu.pastebin.com/f33f3f201)

---

### Post by OffAxis on 2009-11-30
you've got a couple of 'Permission Denied' errors in there...
have you set the permissions properly on what you're trying to access?

---

