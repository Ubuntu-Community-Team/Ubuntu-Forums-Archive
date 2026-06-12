---
title: "Can with browsers, but can't ping or ssh"
date: 2009-09-30
forum: Networking &amp; Wireless
---

### Post by marshmallow1304 on 2009-09-30
I just started having a very strange problem.  I'm on Jaunty 64-bit.  I can connect to the internet via Firefox, but I cannot ping any site by hostname or IP or connect to my ssh server over the internet.  I'm on a college network, both wired and wireless, and it worked just until about a half-hour ago.  The last thing that happened was that my ssh had a "connection reset by peer", but that's happened before, and I usually just reconnect without any problems.

I just did a reboot, but that didn't help.

Internet also works in Opera and Evolution.


NEW: I used an internet checker for open ports, and it reported the port I use for my server as closed.  The server probably crashed as it's a crappy old laptop, but I still should be able to ping other sites successfully though.

---

### Post by bogdan.veringioiu on 2009-09-30
Hi.
Could it be that your college network admins enabled some firewall, filtering anything but http?
I know that in my former campus network, everything but http was filtered...

Bogdan

---

### Post by marshmallow1304 on 2009-09-30
I just tried pinging from one of the Macs in a lab.  That didn't work either.  I guess my problems (no ssh and no ping) are unrelated.  I'll just have to go reboot my server.  Thanks for your help.

---

