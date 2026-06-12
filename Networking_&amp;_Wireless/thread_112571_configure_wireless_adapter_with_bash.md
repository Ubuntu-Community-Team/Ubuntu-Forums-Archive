---
title: "configure wireless adapter with bash"
date: 2006-01-04
forum: Networking &amp; Wireless
---

### Post by ernie on 2006-01-04
i have just installed a new wireless adapter and because i can not get ubuntu to work right i am stuck using the bash command prommpt it is a netgear wg311t

---

### Post by odin on 2006-01-05
the commands you need for this are ifconfig and iwconfig

If,as you say,you installed the network interface and ubuntu detects it the rest is easy.

**ifconfig "network_interface" up** (activate the interface)
**iwlist "network_interface" scan **(scan for available networks)
**iwconfig "network_interface" essid "essid_of_your network" **(the essid is the name of the network guess you know)

and now if you get your ip and everything via dhcp just:

**dhclient "network_interface"**

and if you want static settings then:

**ifconfig "network_interface" "ip_address" netmask "netmask"**  
**route add default gw "gateway"**

well hope all this may help you somehow

---

