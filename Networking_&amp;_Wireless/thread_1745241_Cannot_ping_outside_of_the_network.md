---
title: "Cannot ping outside of the network"
date: 2011-04-30
forum: Networking &amp; Wireless
---

### Post by latitude22 on 2011-04-30
I'm completely stumped, i've looked through all of the posts on the forum and found nothing.

I can ping the router, but I cannot ping anything outside of the network.  The ping just sits there and eventually times out, no error message.  I cannot download updates and it is the only box inside the network having any issues accessing the internet.  I am running 10.10 server.  I can get a list of packages on the update server, but not download them, it appears to be in an incoming issue.  I'm using a motorola Netopia router in bridge mode with a netgear SRXN3205 as a router. Again every other system can download fine. I have tried running on one nic, no help dhcp, static again does nothing.

I can pulls host yahoo.com and I get

yahoo.com has address 98.137.149.56
yahoo.com has address 209.191.122.70
yahoo.com has address 67.195.160.76
yahoo.com has address 69.147.125.65
yahoo.com has address 72.30.2.43
yahoo.com mail is handled by 1 e.mx.mail.yahoo.com.

Sudo route give me this:
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0
192.168.1.0     *               255.255.255.0   U     0      0        0 bond0
default         192.168.1.1     0.0.0.0         UG    100    0        0 bond0
default         192.168.1.1     0.0.0.0         UG    100    0        0 eth0


I would appreciate any help you can give me.

It may be worth noting that I set the box up at home on a dlink router and it worked fine, however I am confused why it is the only system on the network having these issues every other box can ping just fine.

Thanks

---

### Post by latitude22 on 2011-04-30
OK so now I have done a little more investigation if I take eth1 and eth2 offline and just eth0 it everything works fine.  So why is that???  what am i doing wrong?

---

### Post by latitude22 on 2011-05-01
I've sorted this out, for anyone who is interested and since I'm pretty sure after searching the forums for hours the answer isn't easy to find.

I had originally bound the nics using the direction in the wiki, those didn't work. When I bound the nics using this link here:

[http://ubuntuforums.org/showpost.php?p=8763893&postcount=3](http://ubuntuforums.org/showpost.php?p=8763893&postcount=3)

they work perfectly now.  All three nics are bound to one ip and I am able to ping outside servers.

---

