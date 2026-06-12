---
title: "Simple NAT / router setup (ICS-like)?"
date: 2006-04-17
forum: Networking &amp; Wireless
---

### Post by oliver123 on 2006-04-17
Hello,

I have a PC with Ubuntu Breezy which is connected to the Internet (with ISDN) and which also has a network adapter. Now it would be nice if I could just take  my laptop, connect it with the first one via a crossover cable, and then go online with the laptop.

Is there a _simple_ way to set this up? Usually I'd write some iptables rules into a script and start it... then set up dnsmasq so the laptop gets an IP via DHCP and can use the first PC for DNS queries... Or just use zeroconf on both machines to configure IP addresses and then let the laptop ask some Internet DNS server...

But it would be really cool if there'd be just a dialog under System -> Settings (or whatever) like this:

```
===== Share internet connection ======

LAN interface: [ Realtek 8139C  v]

[X] Enable connection sharing on boot
[X] Enable DHCP server

[   Start connection sharing   ]

================================
```

Is there something like this available, or is it possible at least? I think it would be a cool feature.

Regards,
Oliver

---

### Post by mips on 2006-04-17
Tried Firestarter ?

---

### Post by djgenesis on 2006-04-19
Or [Shorewall]("http://www.shorewall.net/")

---

### Post by oliver123 on 2006-04-30
Hello,
sorry for the delay... This thing is needed for my mom's computer, where I am only every two weeks :)

@djgenesis: Thanks, but Shorewall isn't quite that easy to set up... I use it for my home router, but it doesn't quite fit my idea of "hassle-free ICS" :D

@mips: Thanks for that suggestion! Tried firestarter, as it says it does what I want... So far it didn't work quite well (needs a seperate DHCP server installed, though this isn't even listed as "Recommends:" or "Suggests"... Also it doesn't recognize an installed dhcp or dhcp3 server, so I have to configure NAT and DHCP seperately... Maybe I'll try to integrate Firestarter a bit more with Ubuntu :-)

Thanks for your help,
Oliver

---

