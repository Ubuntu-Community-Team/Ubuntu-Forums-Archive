---
title: "Low frame rate VLC in Ubuntu version 11.04"
date: 2011-08-17
forum: Multimedia Software
---

### Post by kingjimbo on 2011-08-17
Ever since I switched from ubuntu 10.04 to 11.04 I am having problems with playing videos.
I keep getting low frame rates while playing avi and mkv video files. I have tried messing around with the vsync option in compiz and the Catalyst control center but all to no avail. 

I have read there are more ATI users with this problem. Is there a way to fix this?

Help will be greatly appreciated.

---

### Post by kingjimbo on 2011-08-19
bump

---

### Post by kingjimbo on 2011-08-26
Bump for justice!

---

### Post by Johnny Buffalkill on 2011-08-26
Based on my own tinkering and googling, it seems the proprietary ATI drivers and Natty don't get along.  I ended up reverting back to the open source drivers because I do alot of movie watching and very little gaming.  

If you need the proprietary drivers for better 3D graphics, you might be better off using Maverick instead of Natty.  I was able to get video to work fine with the proprietary drivers by switching the video output drivers in VLC  to gl instead of xv (or x11 - can't remember exactly).  This gave good framerates and got rid of tearing.  I tried the same in Natty and it didn't work.

---

### Post by kingjimbo on 2011-08-27
> **Johnny Buffalkill said:**
> Based on my own tinkering and googling, it seems the proprietary ATI drivers and Natty don't get along.  I ended up reverting back to the open source drivers because I do alot of movie watching and very little gaming.  

If you need the proprietary drivers for better 3D graphics, you might be better off using Maverick instead of Natty.  I was able to get video to work fine with the proprietary drivers by switching the video output drivers in VLC  to gl instead of xv (or x11 - can't remember exactly).  This gave good framerates and got rid of tearing.  I tried the same in Natty and it didn't work.

hmm yeah I was using Ubuntu 10.04 without any issues... If only it'd so easy as to switch back. I don't believe that is an option anymore, I'd have to do a clean install again.

---

