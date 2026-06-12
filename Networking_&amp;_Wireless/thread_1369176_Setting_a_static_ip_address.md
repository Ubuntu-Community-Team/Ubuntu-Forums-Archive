---
title: "Setting a static ip address"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by XZero450 on 2009-12-30
Reviving an old thread because the title applies.

With 9.04 my situation was as stated before.

With 9.10 I have been unable to define a static ip. Network Manager wasn't capable of doing so, /etc/network/interfaces wouldn't always setup the ip, and if it did, that adapter was unable to do anything(everything was unreachable).

Currently: WICD has replaced Network Manager, /etc/network/interfaces is seemingly ignored.

The only thing that has worked in both situations was defining everything through ifconfig. This sets up my adapter(s) to the address other machines were expecting.

---

### Post by cariboo on 2009-12-31
There are several ways to do what you need. Network-Manager will let you set a static ip address. I've been using it for the last 3 releases to set a static ip address.

[list]
[*] Right click on the network manger icon in the top panel
[*] Select Edit Connections
[*] Highlight your network device
[*] Click Edit
[*] Click the IPv4 Settings tab
[*] Select Manual from the Method drop down
[*] Click the Add button and enter your ip address, netmask and gateway, pressing enter after each address.
[*] Add your DNS Servers
[*] Click apply and enter your password when asked.
[*] right click the network icon and  remove the check mark, they enable it again
[/list]

---

