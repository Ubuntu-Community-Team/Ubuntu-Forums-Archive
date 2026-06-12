---
title: "ipv6 setup help"
date: 2012-05-22
forum: Networking &amp; Wireless
---

### Post by neuman1812 on 2012-05-22
Hey all, Im looking to setup my computer with ipv6 but Im not sure what goes where...

My ISP Charter..does offer some information but I dont know where to plug in the numbers.

```
    6rd Prefix = 2602:100::/32
    Border Relay Address = 68.114.165.1
    6rd prefix length = 32
    IPv4 mask length = 0

Primary DNS Address = 2607:f428:1::5353:1
Secondary DNS Address = 2607:f428:2::5353:1 
```

what goes where in the ipv6 tab of network setttings?

Running ubuntu 12.04.

---

### Post by lemming465 on 2012-05-22
What to do varies depending on your LAN topology.  In a typical scenario one has

  ISP -> cable modem -> wifi/ethernet router -> ubuntu computer

You need to figure out which device is acting as the 6rd relay.  In the second best of all possible worlds (the best being full native dual-stack public v4+v6), the cable modem is the 6rd relay and is provisioned automatically by your ISP.  In this case the cable modem would be emitting ICMPv6 router advertisements and if your wifi router was dual-stack and passed those through, your ubuntu box would Just Work.  This is, alas, rather unlikely with Charter still being in their R&D phase on v6 deployment.

If you are running 3rd party open firmware on the wifi router, you might be able to provision 6rd there, and your computer would Just Work. 

Otherwise, and what we're guessing is most likely, you are looking to configure 6rd directly on your ubuntu box.  Step one:  use 6rd directions from e.g. [litech]("http://www.litech.org/6rd") and configure it by hand.  Make sure you have any other tunnels such as 6to4 or miredo (teredo) turned off first.

Once you have 6rd relaying successfully, write back for help on making it happen automatically.

---

### Post by lemming465 on 2012-05-22
Sorry, forgot to mention that whichever device is acting as your firewall, e.g. the wifi router, has to be passing IPv4 protocol 41 (IP in IP, i.e. slap an IPv4 header on the front of an IPv6 packet).  That's the encapsulation used between your local 6rd relay and Charter's upstream device.  Merely passing IPv4 protocols 1,17,6 (ICMP,UDP,TCP) won't cut it.

---

### Post by lemming465 on 2012-05-22
PPS: the network settings tab for IPv6 is not smart enough to cope with a 6rd relay.  You have to muck about "under the hood" for this one ...

---

### Post by lemming465 on 2012-05-22
PPPS: on the bright side, the 12.04 ubuntu does have new enough kernels and ip commands that the 6rd support is available, and it's on by default.  So the directions in the "6rd howto" should work fairly well out of the box, without installing any extra stuff.

---

### Post by neuman1812 on 2012-05-23
Currently running modem->desktop 

No Router 
Modem is SB6121


I'll read up on the 6rd stuff

---

