---
title: "Which interface is dhcpd bound to?"
date: 2009-03-11
forum: Networking &amp; Wireless
---

### Post by pocketchange on 2009-03-11
I installed dhcp3-server package on my machine.  I'm configuring it to connected to an embedded device so I have a 2nd NIC and a cross-over cable going to the device.

I ran this:

```
sudo dpkg-reconfigure dhcp3-server
```

I answered the interface question with "eth1" which is the interface I want it to look at.  I'm 99% sure that it's looking at the right interface, but if I mess up, I'm on a large network and I don't want IS knocking on my door for handing out addresses.  Is there a command like a netstat command to tell which services are bound to which interface or do I just have to trust the /etc/defaults/dhcp3-server file?

I'd like to just be able to run a command that will tell me which interface it's using.

--
Shane

---

