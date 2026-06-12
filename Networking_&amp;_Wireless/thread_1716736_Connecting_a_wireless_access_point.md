---
title: "Connecting a wireless access point"
date: 2011-03-28
forum: Networking &amp; Wireless
---

### Post by grizdog on 2011-03-28
Hello,

I have scoured the net and found a lot of information about this, but it is all not quite there - slight differences in setup, out of date, or something.  So direction to existing help would be appreciated, but it may not work.

I am running Ubuntu 10.04, with lots of updates.  My computer has two ethernet cards  - one (eth1) connects to the cable modem and the world, and is probably not relevant.  The other (eth0) I would like to attach to my wireless access point (Linksys WAP 54g) so I can have wireless at home.  I plan to use the private network 192.168.1 for everything that eth0 connects to, including itself.  eth1 gets its inet address from my ISP.

I think I have the DHCP sever set up properly, although I have not been able to test it.  For the moment, let's look elsewhere for problems if we can.  Although wireless devices that connect through the access point will be given whatever address the server chooses for them, I would like the access point itself to have a static address, so it would be easy to find if I had to reconfigure something.  I connected the access point to my laptop and connected to it according to the directions, and gave it the static address 192.168.1.20  I unplugged it and tried it again with my laptop, and it worked - it knew it's address.  THen I unplugged the access point and plugged it into eth0 on my server, and tried to connect to it.  No joy.

I used ifconfig to give eth0 the address 192.168.1.240 - the same one my laptop was using.  I may not have the gateway set up properly, and that's why my browser wasn't finding the access point - it woas looking for it on eth1, where it looks for everything else.  But even if I get that fixed, is that really all I have to do?  Isn't there someplace on my computer I have to tell it that the access point has a static address, and what it is?  And if not, what should I do to fix the gateway problem?

I tried to include enough information - thanks for any help.

---

### Post by grizdog on 2011-03-29
Followup to my own message:  The routing table looks good - here is the relevant line in the output from [I]route :

[/I]```
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     *               255.255.255.0   U     0      0        0 eth0

```So why doesn't my browser find the access point?Thanks

---

### Post by Cheesehead on 2011-03-29
What package are you using to serve DHCP?
How did you configure it?
In the server's /var/log/syslog, do you see the AP requesting and receiving an IP?

What does your /etc/network/interfaces look like?

What do your IPtables rules look like?

Did you change the IPForwarding kernel flag?

---

### Post by grizdog on 2011-03-29
> **Cheesehead said:**
> What package are you using to serve DHCP?
How did you configure it?
In the server's /var/log/syslog, do you see the AP requesting and receiving an IP?


I'm using DHCP3, but I'm not sure any of this is relevant yet - I'm not even getting to the AP at all - ping, or a browser or anything.  I gave it a route command, even before that route with no arguments showed the right route, but nothing seems to want to go out eth0 -everything goes out eth1. 


> What does your /etc/network/interfaces look like?Here is all of it:

auto lo
iface lo inet loopback

iface eth0 inet static
address 192.168.1.240
netmask 255.255.255.0
gateway 192.168.1.240

> What do your IPtables rules look like?For the moment it is turned off

> Did you change the IPForwarding kernel flag?No, never

Thanks for thinking about it.

---

### Post by grizdog on 2011-03-30
Solved.  Bad cable.

Thanks.

---

