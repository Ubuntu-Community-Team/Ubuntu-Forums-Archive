---
title: "NAS access..."
date: 2010-05-05
forum: Networking &amp; Wireless
---

### Post by Jancarel on 2010-05-05
Dear Ubuntu Friends,

I have the following problem: I have two computers, one MAC and one Ubuntu, connected to a Router. Also connected is a LaCie NAS disk (EdMini). This configuration has been working for many years. A few weeks ago the power supply from my router died. Since I could not get a power supply, I had to buy a new router. I used to have a USRobotics router, now I have a D-Link router. Both computers connect to the Internet with no problem. The problem is that I have no access to the NAS disk with the D-Link router. This does not work from either computer, MAC or Ubuntu. When I reconnect my "old" router, with the power supply from the new router, everything works fine. It looks to me as if I have to open a port on the new router in order to connect to the NAS. If so, how do I do that...

Thanks for your help,

Jan

---

### Post by gzarkadas on 2010-05-06
You will have to use the documentation of your router, since the web interfaces that come with them, although similar in spirit are usually quite different in the details. Go to your router vendor's site and search for the router manual. Use the model to limit the search.

The ports you' ll have to open are typically those for CIFS (Samba) traffic, ie:
UDP: 137, 138, 445
TCP: 137, 139, 445

But again this depends on your NAS setup and whether additional features such as FTP and Webdav are enabled.

The best thing to do is to put on place your old router, access its web interface and record all its settings. Then plug in your new router and -from its web interface again- create the settings your have recorded previously.

---

