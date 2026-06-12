---
title: "How do I set a static IP for 8.04?"
date: 2009-06-21
forum: Networking &amp; Wireless
---

### Post by Castian on 2009-06-21
I just got Xbox Live last week, but I can't seem to connect both my computer and my Xbox to the internet at the same time.  I can have one or the other, but in order to switch the connection, I have to reset both my modem and my router.  My friend suggested I set up a static IP for both, but I don't know how to do that.  Help please?

---

### Post by Lord Noxarethor on 2009-06-21
Do you have dynamic IP? In that case, I think the only solution to make it static is to talk to your ISP, and maybe you'll pay a little extra (at least this is how it works in Romania).

---

### Post by Lampi on 2009-06-21
> **Castian said:**
> but in order to switch the connection, I have to reset both my modem and my router.
Sounds like your router is not doing his job, is it a router/switch combo?

---

### Post by Castian on 2009-06-21
I made it work before, having my Xbox and computer being able to use the internet at the same time.  I just don't know how I did it.  I had it set up before I moved, and now that I moved, it's like everything reset itself, and I don't know how to fix it.

---

### Post by Lampi on 2009-06-21
Have a look @ your router manual - most routers have a webinterface you can connect to with your browser. Try to get the corresponding url for this webinterface from that manual.

You might find out the routers is not properly configured to handle more than one machine, especially when you mention it used to work, but it doesn't anymore.

---

### Post by Iowan on 2009-06-22
Curious... I could see a problem if you were connected directly to the modem - some of them "lock onto" a MAC address and must be reset to recognize a different address.  I could also see a problem if NAT got turned off in the router (modem would be seeing client addresses instead of router's).
Is your system set up for DHCP - if so, is the router the DHCP server?

---

