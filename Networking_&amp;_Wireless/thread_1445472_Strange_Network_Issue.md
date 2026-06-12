---
title: "Strange Network Issue"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by The Titan on 2010-04-02
I have a network set up, Lynksys router(BEFSX41), Ubuntu Server 9.10, aqnd 2 Windows XP Machines. All of the computers are set to have static IP addresses.

Both of the Windows machines stay on the network just fine, but the server drops off of the network periodically, Then at random times comes back online.

The Server's IP address cannot be pinged from my Windows machine.

There is no dropped packets or anything on the server, and the kernel log shows that the network is not going off and on.

If I put my keyboard on the server and ping the router, it immediately comes back online. Any suggestions?

---

### Post by Iowan on 2010-04-04
I doubt it provides much comfort to mention that I've seen similar threads before... The first thing that comes to mind is a power-saving setting in BIOS. I'm not sure if there's a similar setting in Ubuntu itself... desktop version has one - does server have desktop, or is it (normal) CLI-based server?

---

### Post by grandsatrap on 2010-04-04
You could check to see if your router has some sort of time out. Make sure that the keepalive setting is enabled.

Your server may not have the ports opened for ping. Can you ping the server from itself? 

I'm afraid I don't really understand the problem that you are trying to explain.

---

### Post by Iowan on 2010-04-04
Earlier this evening, I saw another thread mentioning **acpi=off** setting. I'll try to find it again...

---

