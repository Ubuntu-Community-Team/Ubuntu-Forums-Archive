---
title: "localhost works, but loopback and IP address do not"
date: 2012-10-10
forum: Networking &amp; Wireless
---

### Post by UrielCantarero on 2012-10-10
I've searched the forums but can't find something that matches my problem.

Fresh install of Ubuntu 12.04, followed by an installation of Zimbra.  Zimbra installed fine, but when I try going to the admin panel to configure it, I get a "This webpage is not available
The connection to 192.168.1.59 was interrupted."

I get this same result if I try it from one of my Windows machines or if I try it from the Linux machine itself.

I also get the same result if I type in 127.0.0.1 into Firefox, however, typing in "localhost" brings up the Zimbra web interface just fine.

I think the problem is with the machine itself since the loopback isn't working and localhost is.  Perhaps there are other problems too since my windows machines can't hit it either, but I think there's definitely something wrong with the configuration on the box.

The linus box is a VM running on MS HyperV.  It browses the net just fine and I can ping it from any other machine on the network, linux or windows.  I did update the system after installing zimbra, but I didn't check to see whether I had this problem before the updates.

Would love some ideas as to where to look and what to try.  It's not a production server, just testing for now, so I can re-install if I need to, but want to understand what's happening.

Running AD using Server2008SR2 which also runs DNS and have MS DHCP running, although the linux box has a static IP which is reserved.



Thanks in advance.

---

