---
title: "Novatel 760USB broadband dropping connection"
date: 2011-04-18
forum: Networking &amp; Wireless
---

### Post by Z.K. on 2011-04-18
I finally managed to get my Novatel USB760 working reliably by disabling the WI-FI hardware.  It seemed to work okay after that until I noticed that it was disabling itself somehow every few days.  I would try and connect and it would not connect until I right click and disable it and then click on the connection after which it would connect again.  Anyone know why it might be doing this?  And how to fix it?  Do I need some kind of stay alive script?  I am using network manager so I am not sure how to get network manager to do that.

:?

---

### Post by Z.K. on 2011-04-20
> **Z.K. said:**
> I finally managed to get my Novatel USB760 working reliably by disabling the WI-FI hardware.  It seemed to work okay after that until I noticed that it was disabling itself somehow every few days.  I would try and connect and it would not connect until I right click and disable it and then click on the connection after which it would connect again.  Anyone know why it might be doing this?  And how to fix it?  Do I need some kind of stay alive script?  I am using network manager so I am not sure how to get network manager to do that.

:?

Not sure if this is related to the connection dropping, but I noticed the internal cd would sometimes mount itself.  Then the connection would sometimes drop and then reconnect.  Even if the cd did not mount, it was still available in Computer (Equivalent to My Computer on Windows) and could still be mounted by the user.

Finally though I managed to find some instructions to get the USB760 to work without the cd mounting or being visible.  The link [http://forum.eeeuser.com/viewtopic.php?id=54692]("http://forum.eeeuser.com/viewtopic.php?id=54692") was extremely helpful in getting this to work in case anyone else has a similar problem.  The key is the usb760.conf file in /etc/modprobe.d directory.

:D

---

