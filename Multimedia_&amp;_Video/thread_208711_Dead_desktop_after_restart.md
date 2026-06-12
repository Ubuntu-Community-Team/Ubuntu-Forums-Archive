---
title: "Dead desktop after restart"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by CaptSammy on 2006-07-04
I am running Dapper on a 2.6.15-25-686 kernel and an nvidia5200. I installed a LAMP and the gnome desktop on top. All was running fine, then I tried to install the nvidia drivers with apt-get and got nowhere. All was still running so I tweeked a little space by uninstalling CUPS and OpenOffice. I have since uninstalled all nvidia drivers and purged, then uninstalled the restricted modules and installed the latest nvidia driver per the instructions on nvidias site. All still looked fine, then I rebooted...
Now when the system comes up, I see the nvidia logo, then GDM comes up beautiful. I log in and I get my custom cursor, which works fine, but nothing else: just a blank desktop with no functionality.
Did I break something along the way or do I need to reset my desktop somehow? I restart X and every time the same story. I even tried the Envy script and directions.
Any help much appricated, happy 4th!

---

### Post by CaptSammy on 2006-07-04
Solved the issue: When I uninstalled the office package it must have taken gnome with it. I performed a "sudo apt-get install gnome" and poof it installed all the gnome basics and worked.

---

