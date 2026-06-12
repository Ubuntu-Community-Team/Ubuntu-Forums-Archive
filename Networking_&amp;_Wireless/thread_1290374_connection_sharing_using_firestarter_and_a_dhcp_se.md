---
title: "connection sharing using firestarter and a dhcp server"
date: 2009-10-13
forum: Networking &amp; Wireless
---

### Post by shredder12 on 2009-10-13
Currently I use the wireless network of my laptop to provide internet connection to my desktop using a small wired network.

my laptop has a dhcp server and using firestarter I can share internet with the desktop..

My question is can I do the same without firestarter? Do I really need firestarter to share the connection. Since i have a dhcp server installed shouldn't every machine connecting get assigned an IP address and be able to access Internet.

---

### Post by Iowan on 2009-10-13
The DHCP server will only get the machines an IP address. *Something* must take care of forwarding the packets between interfaces.

---

### Post by shredder12 on 2009-10-14
Can I do that without using firestarter. By manually configuring my firewall. Using firestarter is easy but I need to do that in a server and so I need a commandline way to do so. Will ufw ?

---

### Post by Neill_R on 2009-10-14
Firestater is a GUI front end to the service iptables. One start firestarter to configure the firewall (including ICS ) and to monitor events and connections. I have just rebotoed and have not started firestarter yet I have ICS working and my windows PCs have internet acces. The only diffenence is I have a USB mobile broadband modem and my eth0 is connected to WAN port on my Wireless (wired) router which serves (wired) my 4 PC.

---

### Post by kixome on 2009-10-14
go to the system>preferences>network
open the tab for interface you are sharing (network carD or other listed under the tabs at the top) select shared to other computers, or something very similar. restart your Linux PC and it should work, if not in terminal do an ifconfig -a, and use the host address(10.42.43.1) as the gateway,and 10.42.43.(2-254) as the ip of the client, and all should work/

---

### Post by shredder12 on 2009-10-14
ya i have noticed that too..
but since I don't have a gui on server installation..
i was looking to do the same from some commandline tool..
Can you suggest some commandline tools to configure my firewall??

---

