---
title: "Configuring wireless using interfaces config file"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by usafahpng on 2012-03-27
[SIZE=3]Dell Intel core 2 duo laptop; Ubuntu 10.10[/SIZE]
I inherited this old Dell laptop...
I am new to Linux networking and is trying to get Wifif
on this laptop to work.
 
I spend time researching my problems as shown in comments below, but got little progress....
My current objective is to get it to work and use tcpdump to
read signal strengths of surrounding WiFis.
Here is what I understand the “interfaces” config file for network.
Note that “interfaces” file is found in /etc/network/interfaces
I inserted comment ( many from man page) above each stanza (line) 
to show what I understand.
I will also show what iwconfig display on the screen later.
NOTe: When I ran iwconfig, wlan0 shows up instead of wlan1.
So I changed all wlan1 to wlan0.
Below is the entire interfaces file with comments (preeeded by "#") above each command line.
 
# On boot-up, Linux automatically runs interface “lo” (virtual loopback?)
auto lo
 
# iface defines logical interfaces “lo” above as assigned as to
#inet (IPV4 [SIZE=3]TCP/IP networking[/SIZE]) type address with loopback
 
iface lo inet loopback
 
# on boot-up, Linux starts wlan1auto wlan0
# defines wlan0 with inet (IPv4 addressing) and a address of type “static”
 
iface wlan0 inet static
 
#Run “pre-up” _command_ before bringing the “interface” up. 
# Does “interface” refer to hardware, software, or firmware interface of or to wifi?
# Set the mode of this laptop Wifi to managed, channel 1, and 
# its ESSID to MyEssid 
 
pre-up iwconfig wlan1 mode Managed channel 1 essid MyEssid
 
# Run “post-up” _commands_ after bringing the interface up
# Here I do not understand why we have phy phy1? Why not phy phy0?
# How do we find what is “phy” from command line terminal? 
#(“whatis phy” does not work!) 
# Is phy wlan0, ad if so, should we replace iphy1 with wlan0?
# In line below, we are adding a monitor interface (mon0) to physical device phy1 
 
post-up iw phy phy1 interface add mon0 type monitor ; ifconfig mon0 up
 
# On Linux shutdown remove mon0 (monitor) 
 
pre-down iw dev mon0 del
 
# Address 192.168.1.21 would be this laptop's IP address 
address 192.168.1.21
 
# Is this *Network Card Address/Physical Address/MAC Address* ?
# obtained from ANDing “address” and “netmask” below: 
network 192.168.1.0
 
# Using a 24-bit netmask the network would be capable of 
# 2,097,150 networks or 254 different hosts with an IP range 
# of 192.168.1.21 to (192.168.1.21 AND 255.255.255.x + 254)?
 
netmask 255.255.255.0# 
 
#[http://www.computerhope.com/jargon/b/broadcas.htm](http://www.computerhope.com/jargon/b/broadcas.htm)
#The **broadcast address** is used to distribute a signal across 
# a network, commonly used to declare to other devices on a 
#network that a new device has connected to the network and 
#to give those other devices information about the newly 
#connected device. The broadcast address on a network is 
#commonly an address that ends with **255**
# Below is the broadcast address used by this laptop to
# broadcast itself to other devices on a network 
 
broadcast 192.168.1.255
 
#When I run iwconfig, I got this:
lo no wireless extensions.
eth0 no wireless extensions.
Wlan0 IEEEn802.11g ESSID: MyEssid Mode : managed Frequency:2.412GHz Access Point: Not-Associated 
Tx-Power = 0 dBm Retry Long Limit:7 RTS: thrff Fragment thr: off 
Power Management: off
 
Immediate goal:
How to get wireless up and running....with proper interfaces config file... so I can see packets using tcpdump to read WiFi strength of surrounding WiFis?

---

