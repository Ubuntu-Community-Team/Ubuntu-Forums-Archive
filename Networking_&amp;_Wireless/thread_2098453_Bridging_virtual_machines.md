---
title: "Bridging virtual machines"
date: 2012-12-26
forum: Networking &amp; Wireless
---

### Post by MadsRC on 2012-12-26
I got a small ubuntu server, with a small xserver running.

I'd like to virtualize my pfSense firewall, but I've hit a dead end...

My network looks like this:

```
Internet -> DD-WRT router/firewall -> Switch ---
                                               |
                                 Ubuntu Server -
                                               |
                                 DHCP client 1 -
                                               |
                                 DHCP client 2 -
```
And I want the network too look like this:
```
Internet -> Virtual pfSense -> Switch ---
                                       |
                  Ubuntu Server/VM host-
                                       |
                 wireless Access Point -
                                       |
                         DHCP client 1 -
```

Now, the Ubuntu server as 2 physical network interfaces, eth0 and eth1, and from what I could gather using my google-fu, I need to bridge the traffic from the interface my WAN is in (say eth1) to an interface for virtualbox, without the host OS giving eth1 and adress (Since I only want to expose the host system to the LAN).

Could anyone point me in right direction towards bridging eth1 to a virtual interface for VirtualBox to use, without my host OS giving it an IP address? 

Also, would I be right to presume that when this is done, all I would need is to assign 2 NIC's to my virtual machine. NIC1 being set to bridge to eth0 and NIC2 be set to bridge to the virtual interface created before and the in the firewall set NIC1 to be LAN and NIC2 to be WAN?

---

