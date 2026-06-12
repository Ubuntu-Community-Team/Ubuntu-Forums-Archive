---
title: "Server Not Visible From Outside"
date: 2011-05-03
forum: Networking &amp; Wireless
---

### Post by MartyrOfKharak on 2011-05-03
Hi Everyone,

I've been searching around the internet for the last two days trying to solve this problem, because I know how much everyone hates people who ask questions without looking first.  Alas, I haven't found anything.

I have Ubuntu Server 11.04 running on a spare machine, which I've configured and got running just fine.  I am trying to set up an IRC server on this machine for some friends of mine using UnrealIRCd.  I have built and configured the server program, and am able to run it.  Anyone who is connected to my home router (wirelessly or hard-wired) can connect to the server while it is up using either the internal IP, external (router) IP, or the dyndns.org name which is tied to the external IP.

However, anyone outside my home network cannot connect to the server.  I DO have ports 6660-6669 forwarded on my router (IRC standard port is 6667).  When connected to an external network, I cannot join the server by using the external IP, nor the DNS name.

I also have OpenSSH set up on the server machine, and have port 22 forwarded on my router.  I CAN ssh into my server machine from within my home network, and I CAN ssh into my server machine from an external network.

Strangely, I can successfully ping my DNS name from inside my network, but not from outside.  This doesn't make sense to me considering I am able to successfully ssh into the machine.

I hope I'm asking this in the right place.
Thanks in advance.

---

### Post by Cheesehead on 2011-05-03
Check your router settings again.

If you can connect from the LAN, then the machine is working properly and listening. The most likely cause of failure is some setting on your router.

---

