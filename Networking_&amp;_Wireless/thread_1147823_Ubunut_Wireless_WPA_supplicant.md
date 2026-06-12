---
title: "Ubunut Wireless WPA supplicant"
date: 2009-05-03
forum: Networking &amp; Wireless
---

### Post by justin23 on 2009-05-03
Im having some issues getting my wireless connection work with Ubuntu 9.4.  I have tried following the instructions on configuring the wpa supplicant but I'm still new to Linux and I'm not configuring some setting or another correctly.  Running 32 bit on a dell inspiron 1501.  Non broadcasting wireless signal.

justin@justin:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:19:b9:6d:39:99  
          inet addr:192.168.2.4  Bcast:192.168.2.255  Mask:255.255.255.0
          inet6 addr: fe80::219:b9ff:fe6d:3999/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1087 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1453324 (1.4 MB)  TX bytes:162269 (162.2 KB)
          Interrupt:21 

eth1      Link encap:Ethernet  HWaddr 00:1a:92:b1:6c:24  
          inet6 addr: fe80::21a:92ff:feb1:6c24/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

lspci
05:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 01)
08:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
08:01.0 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
08:01.1 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 01)

iwconfig
lo        no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:0
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0

eth0      no wireless extensions.

pan0      no wireless extensions.


justin@justin:~$ iwlist scan
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.

Tried configuring the /etc/network/interfaces with vi the way it was explained in some of the posts and got an error message.  

root@justin:/etc/wpa_supplicant# gedit /etc/network/interfaces

GConf Error: Failed to contact configuration server; some possible causes are that you need to enable TCP/IP networking for ORBit, or you have stale NFS locks due to a system crash. See [http://projects.gnome.org/gconf/](http://projects.gnome.org/gconf/) for information. (Details -  1: Failed to get connection to session: Did not receive a reply. Possible causes include: the remote application did not send a reply, the message bus security policy blocked the reply, the reply timeout expired, or the network connection was broken.)
root@justin:/etc/wpa_supplicant# /etc/init.d/networking restart 
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.


This is how I configured the /etc/network/interfaces file:

auto lo
iface lo inet loopback
address 192.168.2.4
netmask 255.255.255.0
wireless-essid Zeus
gateway 192.168.2.1
pre-up wpa_supplicant -Bw -Dwext -ieth0 -c/etc/wpa_supplicant.conf
post-down killall -q wpa_supplicant

Any ideas?

---

