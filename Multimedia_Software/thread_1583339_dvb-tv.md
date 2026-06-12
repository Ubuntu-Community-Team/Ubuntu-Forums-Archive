---
title: "dvb-tv"
date: 2010-09-27
forum: Multimedia Software
---

### Post by gordo89 on 2010-09-27
hello im trying to set up the pinnacle pctv dvb-t stick ultimate

but no matter what i try it doesn't seem to find any channels im pretty sure its been seen correctly by the pc 

im running Ubuntu 10.4
tried various software to get it working hopefully get it working as a back-end for myth TV 

anybody have any knowledge of these cards or enough to help much appreciated

---

### Post by gordintoronto on 2010-09-27
If might help if you said, "I ran such-and-such program, and did X, Y and Z, and expected this_result. Instead, some_other_result happened."

Have you searched through the mythbuntu wiki?

How does the stick appear when you run Accessories/Terminal, and enter the command lsusb? Have you Googled those words?

---

### Post by gordo89 on 2010-09-28
lsusb shows
Bus 001 Device 002: ID 2304:0236 Pinnacle Systems, Inc. [hex]

i tied running a scan in terminal kaffine mytv and mythtv backend but get no results sometimes it says no device found 

iv read through various sites

---

### Post by gordintoronto on 2010-09-28
Excellent!  From Googling 2304:0236, it appears that you have a PCTV 72e [DiBcom DiB7000PC]

I found some really murky text at:
[http://cateee.net/lkddb/web-lkddb/DVB_USB_DIB0700.html](http://cateee.net/lkddb/web-lkddb/DVB_USB_DIB0700.html) 

and more at
[http://osdir.com/ml/linux-media/2009-07/msg00067.html](http://osdir.com/ml/linux-media/2009-07/msg00067.html)

By the way, it's Ubuntu 10.04, the "04" is for April.

---

