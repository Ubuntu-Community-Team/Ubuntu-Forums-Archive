---
title: "Curious networking issue"
date: 2009-07-20
forum: Networking &amp; Wireless
---

### Post by bobtown on 2009-07-20
I have two Ubuntu 9.04 machines, (I'll call them U1 and U2) which are both connected to the Internet through my wireless router.  I was trying to establish a connection (U2 to U1) between them (SSH, FTP, VNC, Samba) and was not having much success.  I couldn't even ping U1 from U2.  Then I realized that the only way I see U1 at all was to ping U2 from U1.  As soon as I do that, all the services start working, I can ping, port scan, everything.  If I stop talking to U1 for some period of time (5 minutes maybe) everything is broken and I have to ping U2 from U1 before U2 can connect to U1 again.

So it seems like U1 stops taking incoming request after a certain amount of time.  The Internet connection remains, but simply browsing the Internet won't "wake up" whatever is asleep.  I have to ping U2 before a connection can be reestablished.

I've turned off all the secuirty features I can think of and triple-checked the wireless router but I have not been able to find the cause of this problem.


Any ideas,
Thanks

---

### Post by dlmarti on 2009-07-20
Honestly this sounds like a router issue, when resolving the mac address to an IP address.
In order to test this, its going to get a little technical.

1. First disable any firewalls on both machines.
2. Run wireshark on both machines.
3. Try to connect from machine 1 to 2 (watching what happens with wireshark).
4. Reboot both machines
5. Try to connect from machine 2 to 1 (watching what happens with wireshark).

sorry I don't know of a simpler way to look into the problem, maybe someone else does.

---

### Post by bobtown on 2009-07-20
Thanks for the tip.  I'll download it and see what it tells me.

I investigated the problem a little more using a XP machine also on the network and it seems that the issue is only with machine 1 (U1).  I can ping between U2 and the XP laptop just fine while I cannot see U1 from XP until I ping the XP laptop from U1.

Also, the box in question is a HP desktop with a Atheros AR928X wireless network adapter in it.  I haven't come across others having issues with this card, so if anyone knows otherwise please let me know.

Thanks

---

### Post by dlmarti on 2009-07-20
Swap the ports on the router, see if it follows the port.

---

### Post by bobtown on 2009-07-20
Sorry, but I don't understand.  What port and I switching?

---

### Post by dlmarti on 2009-07-20
> **bobtown said:**
> Sorry, but I don't understand.  What port and I switching?

move the cables around to different holes on the router.

---

### Post by bobtown on 2009-07-20
It is wireless, there are none (other than the connection in).

---

### Post by bobtown on 2009-07-21
Seems that switching from NetworkManager to WICD fixed the problem.

---

