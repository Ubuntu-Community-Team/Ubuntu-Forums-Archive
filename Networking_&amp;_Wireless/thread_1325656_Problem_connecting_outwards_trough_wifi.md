---
title: "Problem connecting outwards trough wifi"
date: 2009-11-13
forum: Networking &amp; Wireless
---

### Post by stefangr1 on 2009-11-13
I want to connect a command line system (Ubuntu 9.10) to the home system using a WUSB54GR usb wifi dongle. The problem is that, when using wifi, I can't reach the internet or even other systems in the home network. I can only ping to the wifi accesspoint. The opposite way around, however, everything seems to work just perfectly. I can ssh, ping, whatever, to the wireless cmd system. Off course I tried turning off eth0 as one of the first things, but it doesn't help. 

It seems as if the computer just doesn't know what to do with an outgoing connection when using wifi...

A hint in the right direction would be appreciated a lot :) .


I have configured my /etc/network/interfaces like this:

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
#auto eth0
#iface eth0 inet dhcp

# The wireless network interface
auto wlan0
iface wlan0 inet static
address 192.168.1.110
netmask 255.255.255.0
network 192.168.1.0
broadcast 192.168.1.255
gateway 192.168.1.1

wpa-conf /etc/wpa_supplicant.conf


And my wpa-supplicant configuration file like this:

network={
       	ssid="my ssid"
	key_mgmt=WPA-PSK
       	psk=my psk key
}



This is the output of ifconfig wlan0:

wlan0     Link encap:Ethernet  HWaddr 00:18:39:0d:df:ee  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::218:39ff:fe0d:dfee/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:627 errors:0 dropped:0 overruns:0 frame:0
          TX packets:258 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:112372 (112.3 KB)  TX bytes:42486 (42.4 KB)


This is the output of iptables -L:

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination

---

