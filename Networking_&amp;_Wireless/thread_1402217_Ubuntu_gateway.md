---
title: "Ubuntu gateway"
date: 2010-02-08
forum: Networking &amp; Wireless
---

### Post by IntelMiner on 2010-02-08
(Apologies if this is in the wrong section, tis my first time posting a question)

G'day ubuntuforums, my question is the following

Ive got a Dell Lattitude D610 sitting here that Im about to install Karmic onto, its specs are 1.7Ghz Pentium M, 1Gb RAM, 80GB IDE drive and a Broadcom BC43 something Wi-Fi card, it works flawlessly in ubuntu though I have to reinstall it (hard drive failed)

Now, Im wondering since I wanna wire up my room with network connectivity but Im not allowed to run a network cable to the router, instead of buying wireless cards for each and every device I own, would it be possible to set up this laptop to connect to the router wirelessly then act as a proxy/gateway for the devices on the LAN, preferably running its own DHCP, NAT and DNS so my devices are segregated from the 'regular' network

Are there any guides on doing such and or what packages would I need to do it with?

---

### Post by dvn1129 on 2010-02-08
Just google "internet connection sharing ubuntu" and find a guide. I've never done this, but I asume you have to bridge your wirless connection and your ethernet one.

---

### Post by IntelMiner on 2010-02-08
> **dvn1129 said:**
> Just google "internet connection sharing ubuntu" and find a guide. I've never done this, but I asume you have to bridge your wirless connection and your ethernet one.

As I said, Id rather set it up as my own private separated LAN to the main one, plus ICS on any OS seems to be rather glitchy for the most part

---

### Post by dmizer on 2010-02-08
You are better off using prebuilt gateway distributions: [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

These are built to do what you want to do, they have nice web based configuration interfaces, and they are supported by communities rather than you having to support everything yourself.

They are also very lightweight, and can be run in a virtual machine if so desired.

---

### Post by IntelMiner on 2010-02-08
> **dmizer said:**
> You are better off using prebuilt gateway distributions: [http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions](http://en.wikipedia.org/wiki/List_of_router_or_firewall_distributions)

These are built to do what you want to do, they have nice web based configuration interfaces, and they are supported by communities rather than you having to support everything yourself.

They are also very lightweight, and can be run in a virtual machine if so desired.

The problem with those is I doubt any of them would work in this specific case, that being going Wi-Fi to Ethernet, from personal experience fiddling with those kinds of distributions (mostly Smoothwall, Clarkconnect, Untangle etc) they generally require two network cards, they can provide a Wi-Fi access point, but cant connect to one and feed a connection back through that

---

### Post by dmizer on 2010-02-09
> **IntelMiner said:**
> The problem with those is I doubt any of them would work in this specific case, that being going Wi-Fi to Ethernet, from personal experience fiddling with those kinds of distributions (mostly Smoothwall, Clarkconnect, Untangle etc) they generally require two network cards, they can provide a Wi-Fi access point, but cant connect to one and feed a connection back through that

Actually it would be perfect. The laptop (installed with Karmic) could connect wirelessly. Then install [Virtualbox](https://help.ubuntu.com/community/VirtualBox) (you must install the closed-source version for this to work). Install the gateway distro as a virtual machine and bridge the wireless and wired interfaces to the gateway. The wireless interface should be configured as a pass through for external traffic. Then configure the wired interface as a subnet with dhcp and dns server.

---

### Post by IntelMiner on 2010-02-09
> **dmizer said:**
> Actually it would be perfect. The laptop (installed with Karmic) could connect wirelessly. Then install [Virtualbox]("https://help.ubuntu.com/community/VirtualBox") (you must install the closed-source version for this to work). Install the gateway distro as a virtual machine and bridge the wireless and wired interfaces to the gateway. The wireless interface should be configured as a pass through for external traffic. Then configure the wired interface as a subnet with dhcp and dns server.

The problem with that is the laptops only a 1.7Ghz Pentium M single core with no visualization extensions, itd be far too slow to be practical

---

### Post by dargaud on 2010-02-09
I know I'm not answering your question, but a solution that's often forgotten when you can't run CAT5 lines is to use PLC (Power Line Current) adapters. And there's no driver problem.

---

### Post by IntelMiner on 2010-02-09
> **dargaud said:**
> I know I'm not answering your question, but a solution that's often forgotten when you can't run CAT5 lines is to use PLC (Power Line Current) adapters. And there's no driver problem.

If I had the money to do that, Id probably get an access point, Im trying to do it free if at all possible =P

---

### Post by dmizer on 2010-02-09
> **IntelMiner said:**
> The problem with that is the laptops only a 1.7Ghz Pentium M single core with no visualization extensions, itd be far too slow to be practical
Point taken. My bad for not following up on system specs.

---

