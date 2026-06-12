---
title: "Switch between two wired network connections"
date: 2009-04-27
forum: Networking &amp; Wireless
---

### Post by nanogeek on 2009-04-27
I am running Intrepid. I have two wired network adapters; each one is connected to separate network, one for Internet and one for a VPN. How can I easily selectively enable and disable the individual adaptors? Clicking in Network Manager shows me the two network cards, Auto eth0 and Auto eth1, but they both appear to be active. There is a radio button next to each one, but there odes not seem to be a way to deselect one or the other. I can only check or uncheck the enable network connections box.

Is there a way to easily enable and disable the individual network connections?

Alternatively, is there a way to specify that some IP addresses like 172. and 192. use eth1 while everything else uses eth0? Or, is there a way to specify that Terminal Server Client use eth1 and all other programs use eth0?

TIA
nanogeek

---

### Post by version7x on 2009-05-01
I'm not sure about network manager, but you can turn each interface off on the command line...


ifconfig eth0 down
ifconfig eth1 up

etc...

As far as sending traffic through each interface, you can specify static routes 

I like the "route" command - but it's not persistent across reboots
```
route add -net 172.0.0.0 netmask 255.0.0.0 -dev eth1
```

I'm not sure if I've got the syntax exactly correct.  You may have to play around with it a bit, check the man pages, etc...

Hope that helps!

---

### Post by DGortze380 on 2009-05-01
You'll want to add static routes to /etc/network/interfaces to specify that 192.xxx and 172.xxx get directed to a specific interface.

---

### Post by version7x on 2009-05-01
> **DGortze380 said:**
> You'll want to add static routes to /etc/network/interfaces to specify that 192.xxx and 172.xxx get directed to a specific interface.

Ah!  I wasn't sure where ubuntu put the static stuff...  I'm used to the Redhat locations.

Good info!

---

### Post by DGortze380 on 2009-05-02
> **version7x said:**
> Ah!  I wasn't sure where ubuntu put the static stuff...  I'm used to the Redhat locations.

Good info!

It was really weird when I did it. There is no default location for static route if I remember correctly. I think they can be added to fstab with the correct syntax. I'm pretty sure I just wrote a start up script.

---

