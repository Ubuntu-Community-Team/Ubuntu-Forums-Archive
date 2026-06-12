---
title: "setting up DSL connection"
date: 2009-10-10
forum: Networking &amp; Wireless
---

### Post by stijnob on 2009-10-10
Hello,

I'm trying to set a DSL connection in Ubuntu 9.04. Since I cannot get it working I have some questions:


[LIST]
[*]Using the Network Manager I can add a DSL connection and set username and password. There is also a field 'service'. What values can this field take? Is it necesarry?
[*]When I edit the DSL connection I can fill in a MAC address. Is this the MAC addres from the ethernet card or from the DSL modem? When I plug in a cable to a cable modem I don't have to configure anything to get connected. In this case the MAC address is the same as the one from the ethernet card
[*]There are two other tabs "PPP" setting and "ipv4 settings". Many thing can be set here.Do I need to bother looking at these settings?
[*]Is there a manual that describes these settings?
[/LIST]
thanks in advance

Stijn

---

### Post by Iowan on 2009-10-10
If your DSL modem is like mine, you may need to set up a configuration via Auto eth0. My modem looks like a router to my network - in fact, it can serve DHCP addresses (although I have that feature disabled) and act as firewall.

---

### Post by pagingmrherman on 2010-01-15
Uhh, ok, what's the 'service' field for though?

---

### Post by dmizer on 2010-01-15
> **pagingmrherman said:**
> Uhh, ok, what's the 'service' field for though?

What kind of configuration does your ISP tell you to use? Does your documentation indicate that you need to enter a username and password. If you tell us what settings your ISP requires, we can tell you how to configure your connection. If you've configured your connection on a Windows computer, how did you accomplish this?

In some case, you will need to use a PPP connection, in some cases you will not need to configure any DSL connection at all, only click on your wired connection (usually eth0) and tell it to connect automatically.

---

