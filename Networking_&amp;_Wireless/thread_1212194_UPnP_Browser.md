---
title: "UPnP Browser?"
date: 2009-07-13
forum: Networking &amp; Wireless
---

### Post by FishGills on 2009-07-13
Hey all,
I'm looking for a tool to find all the UPnP devices on the network.

Not a media client but, and I hate to do this in an unbuntu forum, something that mirrors window's network places with UPnP devices turned on.

At the bare minimum, something that will return the IP addresses of UPnP devices.

---

### Post by jonobr on 2009-07-14
Im not sure if this will be useful for you, but if you run a wireshark trace or a tcpdump, and filter based on ssdp (the UPNP discovery protocol)
it will show you what is issuing the the upnp requests and the associated ip address.

ONe caveat with that is that you need to be on the same network segment as the devices

---

### Post by Anafiel on 2011-08-28
I know this is an old thread, but I need the exact same thing.  I have two UPnP devices on my network that I would like to see/access from my desktop network folder.  

How do I add these devices to list with the other 5 machines?  3 XP machines, and 2 Ubuntu machines show just fine, using Samba.  The other 2 (UPnP) don't show.

Thanks!

---

