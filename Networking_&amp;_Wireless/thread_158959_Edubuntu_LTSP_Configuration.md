---
title: "Edubuntu LTSP Configuration"
date: 2006-04-12
forum: Networking &amp; Wireless
---

### Post by mbainrot on 2006-04-12
I have setup a Edubuntu terminal server up at school.
At the moment its setup on a mini network away from the main network

How would i link the Thin client network with the main network with no risk of the Thin client server's DHCP from having a fight with the school's main DHCP server which is based off Novell?

I was thinking using a NAT setup with two network interfaces but i am worried that when i setup the second NIC (the server has only 1 NIC at the moment) linux will automaticly configure eth1 for DHCP...

How would i make sure that eth0 (the existing card) stays as the DHCP card for PXE boot/LTSP server and that eth1 (new card which will connect to the school network) does'nt start dishing out new IPs to entire network as that could really upset the network administrator.

*Server Info:*
PIII 750Mhz
192mb ram
3x 8.2 Gb IDE Hdds
HDD #1 = 8.2
HDD #2 + #3 = Software Raid = 17.2gb ~ 
Edubuntu 5.10

Edit: Also is there a way that i could setup the server so if the network link was interupted that it would disable the affected card

---

### Post by alamba on 2006-04-12
You can enable DHCP only on eth0 buddy. I'd suggest you read up on dhcp server configuration over at google. Not sure about disabling the ethernet card automatically incase the link is interupted...from what I recall this would require a protocol like BGP or MPLS.

A

---

### Post by mbainrot on 2006-04-12
Is there a way of disabling the card when a loop is detected?

---

