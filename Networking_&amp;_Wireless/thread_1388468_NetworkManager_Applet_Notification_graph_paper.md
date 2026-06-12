---
title: "NetworkManager Applet Notification graph paper?"
date: 2010-01-23
forum: Networking &amp; Wireless
---

### Post by madtom1999 on 2010-01-23
My networking seems to be OK but when any changes are made the NetworkManager Applet 0.7.996 (I think) in the panel pops up a small window ~ 300*80 pixels which displays some faint coloured lines and dotted lines where, presumably, there should be a message of some form.

How can I configure it to get the message?

---

### Post by efflandt on 2010-01-23
I did have that issue on an old PC (cross hatched notifications or System Monitor), and the ATI specific xorg-driver-fglrx seemed to solve it.

Others have had that issue, and someone said it was due to not enough video RAM (32 MB or less?).  He gave an example of something to put in xorg.conf to use less memory, but I lost track of that post or what to search for to find it.

---

