---
title: "Static adress on eth0 dissapearing"
date: 2006-01-02
forum: Networking &amp; Wireless
---

### Post by Zeroedout on 2006-01-02
Hello, I'm am having the strangest problem. On my laptop, I set eth0, my built in netowrk card to dhcp and it'll work flawlessly with the net. I can also set eth1, a network card on my pcmcia bus to dhcp and it'll work flawlessly. For a certain app, I need to set one of the cards to a static address, 192.168.1.100 and i do this with network-admin, and it works with eth1, however, when I do this with eth0, the adress dissapears! ifconfig shows eth0 with the adress after I run network-admin, however, once I start the app, ifconfig shows no adress on eth0. It works okay with eth1, however, i need it to run on eth0. 

On my main box, I have two NICs as well, and eth0 has the static adress and it works fine. On my main box though, eth0 is the pci bus, and eth1 is the card built into the mobo.

---

### Post by Zeroedout on 2006-01-03
No one has any ideas?

---

### Post by Lambert on 2006-01-03
the network-admin gui has some known bugs by users where it doesn't do what they set. Post your /etc/network/interfaces file here minus any personal data.

---

### Post by Zeroedout on 2006-01-03
[quote=Lambert]the network-admin gui has some known bugs by users where it doesn't do what they set. Post your /etc/network/interfaces file here minus any personal data.[/quote]

yea, I checked that, it all looked okay, but maybe I missed something.

```
 cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
        script grep
        map eth0

# The primary network interface



iface eth0 inet static
address 192.168.1.100
netmask 255.255.255.0



auto eth0

iface eth1 inet dhcp

auto eth1



```

---

### Post by fonva on 2006-01-05
Try deleting the last line, it could probably help.

---

