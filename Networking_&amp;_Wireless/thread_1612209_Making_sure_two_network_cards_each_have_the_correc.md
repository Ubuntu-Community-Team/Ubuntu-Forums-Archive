---
title: "Making sure two network cards each have the correct IP addresses"
date: 2010-11-02
forum: Networking &amp; Wireless
---

### Post by 5circles on 2010-11-02
I've got two NICs connected to two different routers, and on different subnets of course.  Each is set for static IP.

But somehow I must have mixed up the connections at some point, so the NICs don't always have the IP addresses I expect.  I think there may also be a mixup with different ways of setting the network addresses.  When I click the Network Icon on the Desktop, I see that each NIC has both addresses as options.  The /etc/network/interfaces file has some information about eth0, but all commented out, so there must be another place the addresses get set.

And I just discovered that eth0 and eth1 aren't physical but virtual.  I guess eth0 is the first one that is set.

Can someone help me clean up this mess?

Thanks

---

### Post by Iowan on 2010-11-02
One option would be to have the router(s) assign a static lease (based on MAC address). I presume you can delete the unneeded address option...

---

### Post by 5circles on 2010-11-02
> **Iowan said:**
> One option would be to have the router(s) assign a static lease (based on MAC address). I presume you can delete the unneeded address option...

That's an idea. Unfortunately my Linksys WRT54GS won't do static leases (unless I flash it to open source).

Meanwhile, I took a look at settings in /etc/udev/rules.d/70-persistent-net.rules and found that eth0 and eth1 are apparently connected to the right MAC addresses - at least according to my reading of the man page. Then I changed the names of the NIC cards in the Network widget to match the MAC Address.  Then I rebooted and the widget showed only one address for each NIC.  So maybe its fixed - as long as I don't mess it up. :)

---

