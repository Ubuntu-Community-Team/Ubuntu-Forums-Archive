---
title: "using Hauppauge 950Q with 12.04"
date: 2012-07-14
forum: Multimedia Software
---

### Post by interglossa on 2012-07-14
The output of dmesg tells me that the drivers for my dongle are all loading correctly, but I cannot get TVTime or Me-TV to work on 12.04, although Me-TV worked very well on 10.04.  What applications do people use to watch TV that are in fact working on 12.04?

---

### Post by fixitdude on 2012-07-14
Try kaffeine, and I also upgraded to the 3.3.6 kernel and it solved a few problems. Check my other posts.

Don't forget to do a scan, and you have to hit the "update channels file" (or something like that) button before you do that for some silly reason.

I also wrote this little "tivo" "mythtv" type of automatic Digital Video Recorder DVR script that is pretty simple to use.

[http://ubuntuforums.org/showthread.php?t=2009778](http://ubuntuforums.org/showthread.php?t=2009778)

---

### Post by interglossa on 2012-07-14
Thanks, kaffeine worked perfectly!  I used an earlier version of this years ago and now it works really well with the dongle.

---

### Post by fixitdude on 2012-07-15
Mencoder should work for recording, and atsc_epg should work for getting a schedule after you get a good channels.conf file going.

If you start having problems getting a channel to tune after you change channels, you may want to move to the 3.3.6 kernel, it does it a lot less.

You want to check some of my previous posts about the stuff I ran into.

Are you using it on a laptop or a desktop?

---

