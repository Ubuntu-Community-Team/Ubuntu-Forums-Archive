---
title: "How do I Disable IPv6?"
date: 2010-03-18
forum: Networking &amp; Wireless
---

### Post by teward on 2010-03-18
My ISPs do not support IPv6 IP addresses, so its kind of useless for my system to support it, so is there an easy way to disable it without recompiling the 9.04 opsys that I use?

---

### Post by _h_ on 2010-03-18
Try this:

[http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html](http://www.ubuntugeek.com/how-to-disable-ipv6-in-ubuntu.html)

---

### Post by teward on 2010-03-18
Thanks, I'll take a look at that, and get back to you.

How do I confirm that it worked, though?

---

### Post by _h_ on 2010-03-18
> **TrekCaptainUSA said:**
> How do I confirm that it worked, though?

Here:

[http://ubuntuforums.org/showpost.php?p=478459&postcount=9](http://ubuntuforums.org/showpost.php?p=478459&postcount=9)


Didn't know there was a thread in Tutorials forum here. :P

---

### Post by Iowan on 2010-03-18
There may be more current threads - seems like IPv6 support can now be (de)selected via a setting somewhere (else). I'll try to find something for Karmic...

---

### Post by Skaperen on 2010-03-18
I'm curious what your reason is for wanting to delete it.  You said it is because your ISP doesn't support it.  But Linux has tons of things in it you are likely not using (but someone else might).  Do you want to disable all those?

A good reason might be to save space, or speed things up.  But in the case of IPv6, there are also some know bugs and gotchas.  So I'm curious if you ran into any of these, specifically, and if you tried any other approaches to deal with them.  I'm trying to assess all the problems Linux and Ubuntu will have with IPv6 as the (dragged out) transition continues to take place, and try to develop workarounds and fixes.  Knowing more about what problems people run into can help that.

---

### Post by teward on 2010-03-18
FYI: 

(1) I use Jaunty Jackalope (9.04)
(2) The OS (on this specific machine) auto-converts my IPv4 addresses into IPv6 addresses, doesn't keep the IPv4 address, and causes outside-of-local-network issues because the ISP doesn't use IPv6.
(3) My ethernet connection has about 80 IPv6 addresses mapped to it because it reboots every so often, and I'm sick of it adding a new IPv6 every time networking reboots.

---

