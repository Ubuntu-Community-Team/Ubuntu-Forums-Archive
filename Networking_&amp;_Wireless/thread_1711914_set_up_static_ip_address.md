---
title: "set up static ip address"
date: 2011-03-21
forum: Networking &amp; Wireless
---

### Post by brad1138 on 2011-03-21
I am trying to set up a static ip address. I have followed the directions here [http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/](http://www.liberiangeek.net/2010/09/setup-permanent-static-ip-address-ubuntu-10-0410-10-maverick-meerkat/)
But it doesn't work. I use dd wrt firmware on a linksys WRT54GL. 

I am using the visual interface. The problem may be that I don't know what they mean by "DNS servers" the linksys says it is 0.0.0.0 but entering that doesn't help. It says "connected" on the "notification area" icon, but I have no internet. I have rebooted the computer and the router.

I deleted Auto eth0 and when I added a new connection it is now "Wired connection 1". If I change it to "automatic DHCP" instead of manual, it works fine.

What am I missing, I have easily been able to set static IPs on WinXP machines, I would think Ubuntu would be easier.

Thanks,
Brad

---

### Post by perspectoff on 2011-03-21
A WRT is a wireless card, right?

I use Wicd instead of Network Manager for Static IPs with wireless cards.

Ubuntuguide:
[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Set_a_static_IP_address](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Set_a_static_IP_address)

Kubuntuguide:
[http://www.kubuntuguide.info/index.php/Maverick#Set_a_static_IP_address](http://www.kubuntuguide.info/index.php/Maverick#Set_a_static_IP_address)

---

### Post by brad1138 on 2011-03-21
> **perspectoff said:**
> A WRT is a wireless card, right?

Sorry, no that is the router Linksys WRT54GL with DD-WRT firmware. this is a wire connection.

Thanks

---

### Post by oldfred on 2011-03-21
My router handles the DNS settings. In Network manager I put the router. You cannot use any of the numbers in the range auto assigned for DNS. Often 50 or 100 numbers starting at 100 are already allocated and not available.

---

### Post by brad1138 on 2011-03-21
I figured it out, it was the missing DNS server info, which was just the same as the Default Gateway (192.168.1.1) I actually figured it out by running ipconfig /all on one of my XP machines and it told me the DNS server address. 

It is working fine.

Thanks

---

