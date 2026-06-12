---
title: "static IP will NOT stick"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by terry_opie on 2010-05-15
I've tried just about every suggestion that I have been able to find on google, or in these forums.  But I'm stumped.  Its never been this hard before.

I'm on 10.04, I've tried editing /etc/network/interfaces, I've tried with network manager switching it from dhcp to "manual" and setting the IP, mask, and gateway.

I then thought, well Maybe there's a problem with network-manager.  So I removed it, and installed wicd.  I set the IP.

In all instances ifconfig would show me that the IP had changed... BUT, when I look at my router, the DHCP table shows that I'm still on the old IP.

I have to assume that the router is correct...  Because the port forwarding that I have setup is from the router's perspective.

Any one else having issues setting static IPs on 10.04?  I did have this working just fine on 8.04 last week before my install...

Thanks!

---

### Post by BoneKracker on 2010-05-15
Um... when you use a static IP, it doesn't matter what's in the DHCP server's lease table.

See, it's like this: when you use a static IP, you're not using DHCP.  You're assigning your own IP.  The lease table is irrelevant.

The router is still keeping holding the old lease from when you last connected with dhcp, but that doesn't mean it thinks that's your machine's IP address.  It just means that if your machine connects using dhcp again, it will get that address.  Eventually, the lease will go away (or you could reboot the router to get rid of it).

---

### Post by gradinaruvasile on 2010-05-15
Remove network-manager and wicd and then configure the /etc/network/interfaces correctly.
Then either reboot or restart the "networking" service.

---

### Post by BoneKracker on 2010-05-15
> **gradinaruvasile said:**
> Remove network-manager and wicd and then configure the /etc/network/interfaces correctly.
Then either reboot or restart the "networking" service.

Actually, from what he's saying, I don't think he has a problem.  A stale lease file entry on the dhcp server is not a problem.

As long as the static IP configuration is surviving reboot, and as long as he is able to access the network, where is the problem?

terry_opie:

Are you able to access the network?  After you reboot, does the command 'ifconfig' show the settings you had chosen?

---

### Post by davec64 on 2010-05-15
> **BoneKracker said:**
> Actually, from what he's saying, I don't think he has a problem.  A stale lease file entry on the dhcp server is not a problem.

As long as the static IP configuration is surviving reboot, and as long as he is able to access the network, where is the problem?

terry_opie:

Are you able to access the network?  After you reboot, does the command 'ifconfig' show the settings you had chosen?

+1

It sounds like the DHCP table is showing the leases. They'll show on the router depending on the length of the lease time.

---

### Post by terry_opie on 2010-05-15
Yes, I am able to access the network after the change to a static IP...  I guess it makes sense now that the list of IPs on the router are the ones it assigns.

I guess I just thought that it should be showing up there in the table with the rest of the devices...

I guess this is a non-problem then, just my mis-understanding.
Thanks for straightening me out!

---

### Post by BoneKracker on 2010-05-15
Glad to be able to help.

---

