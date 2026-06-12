---
title: "How do I set a fixed IP address?"
date: 2009-03-02
forum: Networking &amp; Wireless
---

### Post by BradleyAtkins on 2009-03-02
Hi Folks

Wonder if you can help out, I think what I need to do is configure my Ubuntu laptop to use a fixed IP address but please advise if you can think of a better solution: -

The problem is not with my Ubuntu laptop but my Windows machines. They keep losing site of each other and I think it may be to do with the Router dynamically assigning IP addresses.

With this in mind I thought I would cut them all over to using fixed IP addresses. I can mange it ok with the Windows machines but haven't got a clue how to do it with the Ubuntu laptop.

Also I would like to be able to switch the laptop back to dynamic IP addresses when I take it out to another location and want to log into another router.

Any advice appreciated.

Thanks

Brad

---

### Post by Titan8990 on 2009-03-02
IMO, your best bet here will be to setup static leases with your DHCP server. If your DHCP server does not support static leases, check the DD-WRT compatibility list to see if you can change your router's firmware.


If you need to set up a static address, it is configured in /etc/network/interfaces. I found this guide this guide I believe will help: [http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/](http://www.howtogeek.com/howto/ubuntu/change-ubuntu-server-from-dhcp-to-a-static-ip-address/)


When you hook it up to another router, all you will need to do is run dhclient against the interface you are wanting to acquire a dynamic IP. This may overwrite your /etc/resolv.conf, so keep a backup. To this:


sudo dhclient eth0

Where eth0 is the interface you need to acquire an ip.


Good luck.

---

### Post by BradleyAtkins on 2009-03-05
Thanks I'll give that a try

---

