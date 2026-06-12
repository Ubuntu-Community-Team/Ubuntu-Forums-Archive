---
title: "No display on ThinkVision 201p flatpanel"
date: 2006-09-01
forum: Multimedia &amp; Video
---

### Post by Ghazgkull on 2006-09-01
I got a new flatpanel monitor today, but I'm not having any luck getting X to use the monitor. When X launches, my monitor goes black except for the error message "Input signal out of range."

I have tried rebooting into recovery mode and running    
   "dpkg-reconfigure xserver-xorg"

The configuration auto-completed my monitor name as Len-201p, which is correct. I then went through the advanced setup and entered the h_sync and v_sync values as they appear in my monitor's user manual (h_sync 30-92 kHz, v_freq 56-86). But to no avail. I should also mention that the resolution is set to 1600-1200, which is listed as the native resolution for this monitor.

I've since gone in and looked at the xorg.conf that was generated. It says:
 HorizSync   3092
 VertRefresh 6-86

I've also tried manually fixing this to read:
 HorizSync   30-92
 VertRefresh 56-86

But I'm still in the same spot.

I'm out of ideas here. It seems like adding a new monitor should be trivial, but there must be something I'm missing...

---

### Post by Ghazgkull on 2006-09-07
Can anyone suggest something to try?

---

