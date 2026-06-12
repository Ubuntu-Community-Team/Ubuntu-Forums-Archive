---
title: "Access to a network behind static IP"
date: 2011-10-16
forum: Networking &amp; Wireless
---

### Post by aliov_85 on 2011-10-16
Hello
I've asked my ISP for a static IP address.I can't figure out how set the network so from outside I can access the server. I've configured interfaces as

```
auto eth0
iface eth0 inet static
        address 45.45.136.34
        netmask 255.255.255.0
        gateway 46.14.187.1

```
Can you please tell me how can I configure my computer and network so I can localise the server from the outside?

Thanks
Ali

---

### Post by haqking on 2011-10-16
> **aliov_85 said:**
> Hello
I've asked my ISP for a static IP address.I can't figure out how set the network so from outside I can access the server. I've configured interfaces as

```
auto eth0
iface eth0 inet static
        address 45.45.136.34
        netmask 255.255.255.0
        gateway 46.14.187.1

```
Can you please tell me how can I configure my computer and network so I can localise the server from the outside?

Thanks
Ali

your static IP address is not for inside your network, you apply it to your Internet facing interface, probably your router ?

Then you access your WAN static IP and have your router forward to your internal machine LAN IP.

depending on your setup

---

### Post by papibe on 2011-10-16
First, for security reasons I would advice you to **NOT** post your real static IP. Just use something like xx.xx.xx.xx if you need to put an example.

As for the configuration: as haqking is pointing out, if you are behind a router (not a modem), the settings have to be done in the router.

You really need to get support from your ISP to learn how to set things up. You may not need to do anything (in case they use some sort of a DHCP reservation).

After you have that sorted out, in order to access your server you need to:
[LIST]
[*]Set a LAN static IP for the server (like 192.168.1.2).
[*]Forward the ports of the services you want to access in your router to your server.
[*]Open the necessary ports in your firewall/iptables (in case you are running them).
[/LIST]
Does that help?
Regards.

---

