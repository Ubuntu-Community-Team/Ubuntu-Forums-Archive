---
title: "Connect two ubuntu PCs with crossover cable"
date: 2013-08-29
forum: Networking &amp; Wireless
---

### Post by Suresh_Rajachar on 2013-08-29
[COLOR=#333333][FONT=UbuntuRegular]Hello,
 I am trying to connect two ubnutu boxes with crossover cable. Below are the configurations in interfaces file in both the boxes[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]In PC1: 
auto lo
iface lo inet loopback

#auto eth0
allow-hotplug eth0
iface eth0 inet dhcp
   pre-up   ifconfig $IFACE up
   pre-down ifconfig $IFACE down

auto eth1
allow-hotplug eth1
iface eth1 inet dhcp
   pre-up   ifconfig $IFACE up
   pre-down ifconfig $IFACE down

auto br100
iface br100 inet dhcp
    bridge_ports      eth0 eth1
 
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]The above configuration is working fine and I can access internet with this configuration.[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]
[/FONT][/COLOR][COLOR=#333333][FONT=UbuntuRegular]

In PC2:
 auto lo 
iface lo inet loopback[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]auto eth1 
iface eth1 inet static 
address 192.168.x.x
network 192.168.0.0
 netmask 255.255.0.0
gateway <IP address of PC1>[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I have connected PC1 and PC2 with crossover cable.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]I cannot access internet from PC2 with this configuration. But, when eth1 is configured with dhcp, i can access to internet. But, with dhcp it is not picking up PC1 as gateway.[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Can you anyone suggest me what else i need to configure ?[/FONT][/COLOR]
[COLOR=#333333][FONT=UbuntuRegular]Regards,
 -Suresh[/FONT][/COLOR]

---

### Post by tgalati4 on 2013-08-29
So you want PC1 to share its internet connection with PC2?  It's a little more involved than simply setting network configuration settings:  [https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

Bridging network cards has some limitations:  [https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge) and [https://help.ubuntu.com/community/BridgingNetworkInterfaces](https://help.ubuntu.com/community/BridgingNetworkInterfaces)

Some of these guides are old, but the basic procedure is the same.  The bridging utilities are still available in 12.10:

tgalati4@Mint14-Extensa ~/Desktop $ apt-cache search bridge-utils
bridge-utils - Utilities for configuring the Linux Ethernet bridge

---

### Post by Rsxhawk on 2013-08-29
If you're just connecting the two PC's together with a crossover cable for a fast direct file transfer setup, just manually configure each computer with an IP in the same subnet, and to make it fool proof, make the default gateway for each of them, the opposite computer.  No DHCP.  The default gateway part shouldn't be needed as both PC's have IP's in the same subnet (192.168.1.x) where 192.168.1 is the subnet, and the last octect is for the individual host.

---

