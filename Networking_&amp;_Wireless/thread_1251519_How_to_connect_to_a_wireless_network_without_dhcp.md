---
title: "How to connect to a wireless network without dhcp"
date: 2009-08-27
forum: Networking &amp; Wireless
---

### Post by fernandoc1 on 2009-08-27
I'm using Ubuntu Jaunty and I'm trying to connect to a wireless network that there is no dhcp server on it.
The problem that I'm facing is that it seems that Ubuntu do not establish a connection, using the network manager, that there is no dhcp service on it.
Then I wanna know how can I connect to this network, by providing a static manual ip?
I've already tried to edit the network properties in the network manager, but it seems not to work.

---

### Post by dbalascak on 2009-08-27
These are two parts that do not depend on each other.  First is wireless authentication.  Do you get a wireless connection established?  Does the network manager connection information show the connection as being active?  
What do you see with the following command?

```
iwconfig
``` 

should be something like 
```

wlan0     IEEE 802.11g  ESSID:"A-wireless-network"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:12:17:1A:4D:EB   
          Bit Rate=54 Mb/s   Sensitivity=-200 dBm  
          RTS thr=2346 B   Fragment thr=2346 B   
          Power Management:off
          Link Quality:43/100  Signal level:-68 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```

---

### Post by wareagle on 2009-08-27
Right click on the network manager icon and click on edit connections.

Click on wireless, click add, and you can enter all of the details for the wireless network there (including a static ip).

---

### Post by Charly85551 on 2009-08-28
Hi,
just make sure you understand the basics behind: If there is no dhcp then you need to set up your own network settings by using an IP-address which is unique (i.e. not yet used), in the same netmask (mostly 255.255.255.0) and pointing to the right gateway _and_ name/DNS-server. The easiest way for that is manipulating */etc/network/interfaces* and */etc/resolv.conf* in a terminal mode with* gedit* or something similar.
cheers

---

### Post by Charly85551 on 2009-08-28
Hi,
just forgot one thing: after manipulating /etc/network/interfaces you need to restart network settings by using *sudo /etc/init.d/networking restart* in terminal mode.
cheers

---

