---
title: "Wireless/Wired Bridge"
date: 2010-01-03
forum: Networking &amp; Wireless
---

### Post by taing on 2010-01-03
I have looked through the forums and Googled a bit but can't find my exact situation and the similar situations are murky at best.

I have a DSL internet connection connected to a Wireless Access Point/Router. There are several PCs that have wired connections from the Router.

Due to the construction of my house, the wireless coverage is weak upstairs. I have a wired link to a PC upstairs(running Karmic) that also has a wireless card on board.

I would like to use the wireless card on this PC to extend the wireless coverage. The goal would be a for an upstairs laptop to connect to this PC wirelessly(WPA-PSK hopefully) and be on the same network as the other PCs in the house and be able to reach the internet.

Hopefully the Access Point/Router would still be responsible for all DHCP.... The goal is to have only one network - for all computers in the house to be able to see each other.

In a complete solution the client laptop would be able to seamlessly transfer from upstairs to downstairs using the "access point" which provides the best signal.

---

### Post by johnson.d on 2010-01-04
This can be done in two steps:

1) Change the wireless adapter in the PC and Laptop to adhoc mode. The wireless adapter in the ubuntu PC can be changed to adhoc mode using the following commands.

**sudo /etc/dbus-1/event.d/25NetworkManager stop** - To stop the GUI network manager

**sudo ifconfig eth1 down** - To bring down the wireless adapter ( In this case eth1 is the wireless interface)

**sudo iwconfig eth1 mode ad-hoc** - To change the adapter to ad-hoc mode

**sudo iwconfig eth1 channel 4** ( Both the PC and the laptop's adapter should be working in the same channel)

**sudo iwconfig eth1 essid 'name'** - To add the name (ssid) for the network you want to create/join. Use single quotes if there is a space in the name

**sudo iwconfig eth1 key 1234567890** - To add a WEP encryption key

**sudo ifconfig eth1 up** - To bring up the wireless interface

Similarly the Laptop should be configured to adhoc mode and given the same name and encryption key as given to the PC

Once this is found working, You can make it permanent by adding some lines to the /etc/network/interfaces file with appropriate details

auto lo
iface lo inet loopback

auto eth1
iface eth1 inet static
wireless-mode ad-hoc
wireless-channel 4
wireless-essid 'name'
wireless-key 1234567890
address 192.168.0.2
netmask 255.255.255.0
gateway 192.168.0.1

2) The second step is to create a Bridge between the PC's NIC and the wireless NIC

To create the bridge the following link would be useful

[https://help.ubuntu.com/community/NetworkConnectionBridge](https://help.ubuntu.com/community/NetworkConnectionBridge)

---

