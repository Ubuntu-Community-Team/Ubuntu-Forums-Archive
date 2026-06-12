---
title: "network card config and routing"
date: 2011-04-05
forum: Networking &amp; Wireless
---

### Post by penguinvitamins2 on 2011-04-05
Strange issue on Ubuntu desktop 10.10's (64bit) network settings and routing

Hi All

I'm using a static IP on a single interface desktop machine,no static routes; just a default gateway to the WAN router which handles all routing decisions. This Ubuntu desktop is used to monitor network remote routers up/down state using Nagios 3(we only use passive pings so it is  very low network overhead).

Sporadically monitored devices are declared unreachable on Nagios. e.g. all of a sudden 4 out of the 20 devices monitored is unreachable. Doing a manual ping from the machine console also states these routers unreachable. However a different Windows machine within the same LAN subnet can ping these so-called remote device just fine. Further investigation showed that the ping packet from the Ubuntu machine reach the default gateway router but then the default gateway sends it to its next hop's default gateway instead of the right route. (as if this router does not understand the destination address against its own routing tables)

Initially it was though the default gateway router has a problem but it does not since all other machines using the same routes and router works without these issues. 

I found that a ping from this ubuntu machine using a forced interface works parameter i.e. ping 172.25.3.1 -I eth0 works vs just doing a ping 172.25.3.1

Ubuntu also after the machines is up for a few hours, adds an additional address in the routing table of 169.154.0.0 (normally an address when the machine cannot get a dhcp address). But I'm using a fixed IP address??? This 169.154.0.0 address is not visible using ifconfig but only when using the command route -n

By re-entering and applyng the static IP to the interface I get the machine working properly again. Other times I can only fixed it by restarting the network services or rebooting (ugh)

What gives? I just cannot figure it out. Hardware is a standard HP desktop and I'm using the onboard network card. There is also no pattern to this. out of 20 devices it is not always the same IP's that goes "down". It basically breaks routing to the whole remote subnet, not just the device we are monitoring within that subnet.

All the latest patches is loaded, kernel is up to date and stock standard Ubuntu drivers and packages is used (even Nagios is a ubuntu installed version, not a source compiled one)

Any advice appreciated. 

Stefan

---

### Post by penguinvitamins2 on 2011-04-22
I manage to replicate this problem in Fedora 14 64bit, which means it is not Ubuntu specific but something eg kernel or Network services (Network Manager is used in Ubuntu and Fedora)

Tried the following as well but with no luck

Cleared the default iptables (and use Shorewall as the firewall)
Swopped the network card from the onboard to an external Intel pro

But as stated above if the remote host cannot be ping'ed with a normal ping xxx.xxx.xxx.xxx doing a ping -I eth0 xxx.xxx.xxx.xxx (where xxx is the host ip) works 100% (-I means you force the ping source via the specific interface card) 

Doing a service network restart via a cron job every now and then works and the "lost" remote hosts is pingable again but doing this is not ideal.

Any help appreciated

---

