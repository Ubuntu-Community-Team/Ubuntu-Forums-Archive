---
title: "Crazy IP address -- need help!"
date: 2010-09-01
forum: Networking &amp; Wireless
---

### Post by mptorr on 2010-09-01
I'm running a fresh install of Ubuntu 10.4.1 on a Dell Dimension 4700 desktop.

When connected to the network (jack in wall, no router), I normally navigate my intranet and the internet.

But here's the issue: this particular Dell machine has an IP addresses that is radically different from all other machines connected to the same network.

For example:
**Dell PC: 270.17.142.200**
Other PC #1: 130.180.26.22
Other PC #2: 130.180.26.75
Other PC #3: 130.180.26.43
etc...

The ifconfig shows:
inet addr:270.17.142.200  Bcast:270.17.142.255  Mask:255.255.255.0

The etc/network/interfaces shows the default:
auto lo
iface lo inet loopback

Ping is sucessfull.

I have tried to edit etc/network/interfaces to force a different IP, but then I lose connectivity. I need this to follow the IP scheme of my intranet so I can set up a server that resolves by hostname. 

Is there anything wrong with the NIC or is this something that can be resolved via command line?

Any help will be greatly appreciated!

Thx

---

### Post by scorp123 on 2010-09-01
> **mptorr said:**
>  For example:
**Dell PC: 270.17.142.200**

The ifconfig shows:
inet addr:270.17.142.200  Bcast:270.17.142.255  Mask:255.255.255.0
 Foto please?? :D

IPv4 address space ends at 255.255.255.255 .... so I really wonder how you got that 270 into your first octet?? :)

---

### Post by mptorr on 2010-09-01
oh, those are dummy numbers for privacy of my network. just an example of how different the IP addresses are between PCs...

---

### Post by scorp123 on 2010-09-01
> **mptorr said:**
> oh, those are dummy numbers for privacy of my network. Aaaaah, LOL :D

Sorry, I really really thought ... ](*,) .... oh well. :oops:

OK, back to topic: Can you check the routing table of that system? e.g. what does this command say:
```
sudo netstat -r
```

Or this one (should be the same):
```
sudo route -v
```

You can use "netstat" to check if and who this router is talking to:
```
sudo netstat -planut
```

Another thing might be to check e.g. the contens of these files:
```
/etc/resolv.conf
```

Also check this file: **/var/log/syslog**  ... In there you should see from which DHCP server you got that address from. Example from my laptop here:

```
...
Sep  1 20:48:23 serenity dhclient: Internet Systems Consortium DHCP Client V3.1.3
Sep  1 20:48:23 serenity dhclient: Copyright 2004-2009 Internet Systems Consortium.
Sep  1 20:48:23 serenity dhclient: All rights reserved.
Sep  1 20:48:23 serenity dhclient: For info, please visit https://www.isc.org/software/dhcp/
Sep  1 20:48:23 serenity dhclient:
Sep  1 20:48:23 serenity NetworkManager: <info>  DHCP: device eth0 state changed normal exit -> preinit
Sep  1 20:48:23 serenity dhclient: Listening on LPF/eth0/00:16:d3:0d:94:5f
Sep  1 20:48:23 serenity dhclient: Sending on   LPF/eth0/00:16:d3:0d:94:5f
Sep  1 20:48:23 serenity dhclient: Sending on   Socket/fallback
Sep  1 20:48:32 serenity dhclient: DHCPREQUEST of 192.168.1.210 on eth0 to 255.255.255.255 port 67
Sep  1 20:48:42 serenity dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Sep  1 20:48:48 serenity dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
Sep  1 20:48:48 serenity dhclient: DHCPOFFER of 192.168.1.210 from 192.168.1.1
Sep  1 20:48:48 serenity dhclient: DHCPREQUEST of 192.168.1.210 on eth0 to 255.255.255.255 port 67
Sep  1 20:48:48 serenity dhclient: DHCPACK of 192.168.1.210 from 192.168.1.1
Sep  1 20:48:48 serenity dhclient: bound to 192.168.1.210 -- renewal in 864116719 seconds.
...

```

I suggest you check that log as there might be clues to which DHCP server your system was talking to when it received that address.

---

### Post by endotherm on 2010-09-01
that odd ip address.... does it start with 169.254.x.y?

---

### Post by scorp123 on 2010-09-01
> **endotherm said:**
> that odd ip address.... does it start with 169.254.x.y? Aaah ... good ol' Avahi service? Yeap, that could be a candidate too. :)

---

### Post by mptorr on 2010-09-01
When running the syslog I see it has DHCP request for and joins the crazy IP address.

The odd ip address.... does NOT start with 169.254.x.y.

sudo netstat -r and sudo route -v return the crazy ip in 'destination' as xxx.yyy.[www.0](www.0)

Is it possible the sys admin (who cannot/won't help me because this workstation was not bought by my employer) tied my MAC address to this crazy IP?

---

### Post by endotherm on 2010-09-01
> **mptorr said:**
> When running the syslog I see it has DHCP request for and joins the crazy IP address.

The odd ip address.... does NOT start with 169.254.x.y.

sudo netstat -r and sudo route -v return the crazy ip in 'destination' as xxx.yyy.[www.0]("http://www.0")

Is it possible the sys admin (who cannot/won't help me because this workstation was not bought by my employer) tied my MAC address to this crazy IP?
that is a feature of some modern network equipment. I would probably pull out wireshark and examine the dhcp renewal process to make sure I'm hitting the right server.

---

### Post by scorp123 on 2010-09-01
> **mptorr said:**
>  who cannot/won't help me because this workstation was not bought by my employer) tied my MAC address to this crazy IP? Or the other way around. I have been to such places. Unknown MAC addresses get a crazy IP's and get routed into crazy VLAN's ... usually they do that to keep intruders out. Only known MAC addresses will get the right IP's and connected to the real LAN.

It could very well be that you are looking at something like that. Are you allowed to bring your own computer into their network? I know places where they call the security guards if you do that ... :D

---

### Post by mptorr on 2010-09-01
Yes we can use outside computers but they do not suport them.
Let's say it's the MAC issue: is there anyway of changing this?
I have already contacted the folks from networking to see if they have any records of this PC being assigned to a specific fixed IP via MAC. But I'm not even sure this procedure makes sense.
BTW, other PCs I have with Ubuntu don't have this issue.
This machine is the only one and seems to be doomed by hardware.

---

