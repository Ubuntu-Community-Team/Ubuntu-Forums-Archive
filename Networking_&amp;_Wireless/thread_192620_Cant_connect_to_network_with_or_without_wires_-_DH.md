---
title: "Cant connect to network with or without wires - DHCP issue?"
date: 2006-06-08
forum: Networking &amp; Wireless
---

### Post by Joehome on 2006-06-08
Hey folks, I have Thinkpad that was working with a dlink DWL-650 under Breezey but wonk connect under Dapper. Originally I thought it was the card so I switched it out for a Linksys WPC11. That had the same result. Full signal, but no DHCP. So I swapped in a Xircom Realport 10/100 card. That installed ok but still no DHCP. What am I doing wrong? Please keep it simple. I am trying to be a convert. thanks!
-Joe

(PS - I ended up formatting and reinstalling from a new iso in an attempt to fix this, so this is a clean install now, not an upgrade. )

---

### Post by mindwarp on 2006-06-09
Post screenshots of your network configuration dialogs, that should help.  Also, on many routers there can be MAC address filtering implemented, make sure either that your card is on the list, or that it is disabled

---

### Post by DougC on 2006-06-09
Hi,

Bit of a long shot maybe, but try the following command in a terminal.

sudo /etc/init.d/networking restart

Then see if you are connected. This is vaguely similar to a problem me and several others have with DHCP. The problem I'm having is more to do with the nVidia network cards built  into my motherboard, but you never know it might be related to the same dhcp bug thats been filed.

---

### Post by Joehome on 2006-06-10
I tried that command , but it diddnt work. it just said that the device was not found. I cant see how it couldnt see it. On the wireless cards, I show 90%-100% signal strength, but cant get an ip address. Anyone got anything else? please help.
thanks
-Joe

---

### Post by Joehome on 2006-06-10
[QUOTE=DougC]Hi,

Bit of a long shot maybe, but try the following command in a terminal.

sudo /etc/init.d/networking restart

Then see if you are connected. This is vaguely similar to a problem me and several others have with DHCP. The problem I'm having is more to do with the nVidia network cards built  into my motherboard, but you never know it might be related to the same dhcp bug thats been filed.[/QUOTE]

To be specific, The error (or output) was DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 3
This repeated with intercals 5,13,15 and 12. Then It stated:
No DHCPOFFERS received.
No working leases in persistent database - sleeping. 

I get an ip address on all my other network machines (non Ubuntu) so what is different? Any help is appreciated. Thanks
-Joe

---

### Post by ns2048 on 2006-06-11
What kind of DHCP server are you using (i.e., router, Linux PC)? Also, could you post the output of 'lspci -vv', 'lsmod', 'cat -b /var/log/dmesg'.

--ns2048

---

### Post by Joehome on 2006-06-11
[QUOTE=ns2048]What kind of DHCP server are you using (i.e., router, Linux PC)? Also, could you post the output of 'lspci -vv', 'lsmod', 'cat -b /var/log/dmesg'.

--ns2048[/QUOTE]
I am using a linksys router BEFW11S4. very common. and is working fine. Looks like the ubuntu machine does not even get out to try to touch it.
-Joe

---

### Post by jvictor on 2006-06-11
There are mainly 3 reasons 

1) IPV6 is enabled, soln: Disable IPv6
2) DHCP is flimsy soln: use static IP
3) Use ur ISPs DNS server add in the /etc/resolv.conf


If the three of these dont work after a reboot, please post the o/p of the following commands

less /etc/hosts
route -n
less /etc/resolv.conf

---

### Post by ns2048 on 2006-06-12
Are you using ndiswrapper for your DWL-650 adapter? Also, I agree with 'jvictor', using static IPs is better if you don't absolutely need DHCP.

--ns2048

---

