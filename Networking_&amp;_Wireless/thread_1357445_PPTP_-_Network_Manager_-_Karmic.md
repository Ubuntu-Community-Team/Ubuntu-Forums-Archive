---
title: "PPTP - Network Manager - Karmic"
date: 2009-12-17
forum: Networking &amp; Wireless
---

### Post by Sniffer on 2009-12-17
Here we go again....

After installing on Karmic X64 network manager pptp, i have configured a simple pptp connection, IP username and password...

Try to connect and failed, 

i have tried this

[http://ubuntuforums.org/showthread.php?t=1189343](http://ubuntuforums.org/showthread.php?t=1189343)

and this

[https://wiki.ubuntu.com/VPN](https://wiki.ubuntu.com/VPN)

i went to gconf editor and my connection was there, the refuse-eap string as well with yes on the value....and connection failed.

So here we go again with another problem on Karmic...any help or someone that is happening tha same is helpfull.

Thanks.

---

### Post by Sniffer on 2009-12-17
Thanks for the ones that read this.

But i tried by cli and it works, something with network manager and the WTF keyring....

Solved this one in the old way of Red Hat 6.0 and pppd call.

---

### Post by raheelsuleman on 2009-12-17
hi there here is how my interface file looks like

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 192.168.20.224
netmask 255.255.255.0
network 192.168.20.0
broadcast 192.168.20.255
gateway 192.168.20.99

auto eth0:0
iface eth0:0 inet static
name Ethernet alias LAN card
address 10.0.0.32
netmask 255.255.0.0
network 10.0.0.0
broadcast 10.0.255.255
gateway 10.0.0.19


but after logging in i notice that the network manager icon does not show the usual connected icon but shows as if it is disconnected. also when i click on "edit connections" two connections show up
ifupdown(eth0)
ifupdown(eth0:0)
i just want to see the network icon to be connected. can any one explain to me. thanks.

---

