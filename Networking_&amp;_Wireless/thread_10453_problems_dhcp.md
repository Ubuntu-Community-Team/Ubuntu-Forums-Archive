---
title: "problems dhcp"
date: 2005-01-07
forum: Networking &amp; Wireless
---

### Post by alucard on 2005-01-07
i tried to switch off the ipv6 module by editing /etc/modutils/aliases, and screwed up the network interface. Now I cannot seem to get any dhcp address from the server. I am able to obtain the a dhcp address when I log on in Windows.

I can get the interface to work by manually setting the ip address using 
ifconfig eth1 ipaddress netmask some_net_mask
route add default gw gw_address

How can I get the dhcp to work again? 

thanks

---

### Post by wallijonn on 2005-01-07
Open a Root Terminal -> [COLOR=Red]gnome nettool[/COLOR] -> Network device: [COLOR=Blue]etho[/COLOR] <pull-down> -> Connection settings configuration -> [COLOR=Blue]Automatic DHCP[/COLOR], <[COLOR=DarkOrange]check[/COLOR]-[COLOR=DarkOrange]on[/COLOR]> Activate when the computer starts -> [COLOR=Blue]OK[/COLOR] <Close nettool> Reboot. 

That may work.

---

### Post by alucard on 2005-01-08
not working :(

---

