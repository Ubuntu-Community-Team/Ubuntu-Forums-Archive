---
title: "setup items won't open"
date: 2017-08-29
forum: Multimedia Software
---

### Post by MBEeng on 2017-08-29
I have mythbuntu 0.28 running on Ubuntu 14.04 LTS. This setup with both front end and back end on the same computer.  After upgrading from 0.27 on 12.04LTS I used the front end setup to get video and audio working.  But now, several months after upgrading, many of the front end setup items, for example video and audio playback, won't open.  If I attempt to select them nothing happens.  I have to back out of the setup with esc.  And today I found that in back end setup the channel editor won't work.  It displays the channels, and I can toggle between channel number or channel name order.  But I can't edit any of the channels - the edit key does nothing.  And clicking on the entry for a channel does nothing.

Any suggestions of what has gone wrong?

---

### Post by MoebusNet on 2017-09-16
The only thing I've really done in Backend Setup Channel Editor is delete unwanted channels (e.g., Home Shopping Network). I do that by scrolling down to the unwanted channel then pressing the 'D' key on my keyboard (I don't use a traditional remote - too limiting). The popup menu asks me to confirm; I select 'Yes'.

I'm under the impression that some Frontend Setup items are for remote frontends (e.g., IP address, password, etc.). I try to change as little as possible in Frontend Setup for my combined FE/BE system; basically Video, Audio & USB DVD setup.

---

### Post by MBEeng on 2017-09-27
I solved this problem today.  I checked notes I had made, and found that a few months after upgrading to 0.28 I had turned on the anti-tearing option on the AMD video driver.  But that caused a problem with windows in MythTV.  Turning off compositing in Window Manager Tweaks fixed the window issue.  I didn't run into the setup problem for weeks or months, and by then I had forgotten about the anti-tearing and compositing changes.  
Turning off anti-tear did not fix the setup screen issue, but turning compositing back on solved the problem.  Of course now some videos will have tearing, but I guess I'll have to live with that.

---

