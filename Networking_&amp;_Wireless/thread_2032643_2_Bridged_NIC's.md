---
title: "2 Bridged NIC's"
date: 2012-07-24
forum: Networking &amp; Wireless
---

### Post by Louis McIntyre on 2012-07-24
I have a PC that I installed Ubuntu 11.10 Desktop onto, Installed 2 ASUS NX1101 NIC's and created a bridge across those two NIC's.  I also installed Wireshark and tshark to be able to run packet captures across the bridge.  The purpose is to put this box between our firewall and modem to track and monitor all packets coming and going to our network.

The issue I am having is that the interface facing away from the switch (eth2) is being disabled or turned off at night, while (eth0) on the switch is still on. (eth1 is the onboard NIC)

I have modified the GRUB to turn off acpi, but that did not fix the issue.  I have changed the power settings to never turn off, left the monitor to turn off after 30 mins and screen saver to start at 15 mins.

I am currently testing the bridge with my VoIP phone and laptop.  The VoIP phone is set to send out a packet to our host every 60 secs, across the bridged NIC's and is captured by tshark.  I can't have the NIC's being turned off or disabled if this machine in line with our Internet connection.

Here is the entries for /etc/network/interfaces

auto lo eth0 eth1 bridge0 eth2

iface lo inet loopback

iface eth0 inet manual

iface eth1 inet manual

iface eth2 inet manual

iface bridge0 inet static
address 10.1.3.13
netmask 255.255.255.0
network 10.1.3.0
broadcast 10.1.3.255
gateway 10.1.3.3
bridge_ports eth0 eth1 eth2
pre-up ip link set eth0 promisc on
pre-up ip link set eth1 promisc on
pre-up ip link set eth2 promisc on
post-up ip link set bridge0 promisc on


I apologize if someone has already posted/fixed this issue.  I couldn't find anything that has fixed my issue.

---

### Post by Louis McIntyre on 2012-07-25
Which logs can I look at to tell me what the NIC's are doing and why they stop passing packets?  The system had about 30 hours of uptime but when I came in this morning my VoIP phone was not working until I restarted /etc/init.d/networking.

---

