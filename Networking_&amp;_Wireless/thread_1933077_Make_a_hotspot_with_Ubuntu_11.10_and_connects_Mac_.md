---
title: "Make a hotspot with Ubuntu 11.10 and connects Mac mini/leopard/airport to it."
date: 2012-02-28
forum: Networking &amp; Wireless
---

### Post by marietto2008 on 2012-02-28
Hello.

I'm trying to configure a hotspot with my Ubuntu 11.10 X64 using hostapd and following this guide : [http://linuxalfi.wordpress.com/2011/11/06/connectifylinux/](http://linuxalfi.wordpress.com/2011/11/06/connectifylinux/)

This is what I did :

root@ziomario:/home/mario# lsusb

Bus 001 Device 004: ID 148f:2573 Ralink Technology, Corp. RT2501/RT2573 Wireless Adapter

root@ziomario:/home/mario# lsmod | grep rt
scsi_transport_iscsi    46321  4 ib_iser,iscsi_tcp,libiscsi
parport_pc             36962  1 
rt73usb                31242  0 
crc_itu_t              12707  1 rt73usb
rt2x00usb              20686  1 rt73usb
rt2x00lib              50497  2 rt73usb,rt2x00usb
mac80211              492265  2 rt2x00usb,rt2x00lib
cfg80211              204021  2 rt2x00lib,mac80211
parport                46562  3 ppdev,parport_pc,lp

root@ziomario:/home/mario# nano /etc/hostapd.conf

#change wlan0 to your wireless device
interface=wlan0
driver=nl80211
ssid=marietto
channel=7
hw_mode=g
wme_enabled=1
macaddr_acl=0
auth_algs=1
ignore_broadcast_ssid=0
wpa=0
wpa_passphrase=********
wpa_key_mgmt=WPA-PSK
wpa_pairwise=TKIP
rsn_pairwise=CCMP

root@ziomario:/etc# hostapd /etc/hostapd.conf

Configuration file: /etc/hostapd.conf
Using interface wlan0 with hwaddr ... and ssid 'marietto'
wlan0: STA 00:23:6c:7a:5a:56 IEEE 802.11: authenticated
wlan0: STA 00:23:6c:7a:5a:56 IEEE 802.11: associated (aid 1)
AP-STA-CONNECTED 
wlan0: STA RADIUS: starting accounting session 4F4D365B-00000000

and then I have started another shell :

root@ziomario:/home/mario# ifconfig wlan0 192.168.27.1 up
root@ziomario:/home/mario# ifconfig

eth1      Link encap:Ethernet  HWaddr   
          indirizzo inet:192.168.2.3  Bcast:192.168.2.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::2e1:a7ff:fe76:7681/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:333562 errors:0 dropped:0 overruns:0 frame:0
          TX packets:190798 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:424062427 (424.0 MB)  Byte TX:19303155 (19.3 MB)

lo        Link encap:Loopback locale  
          indirizzo inet:127.0.0.1  Maschera:255.0.0.0
          indirizzo inet6: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:120 errors:0 dropped:0 overruns:0 frame:0
          TX packets:120 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:0 
          Byte RX:35422 (35.4 KB)  Byte TX:35422 (35.4 KB)

mon.wlan0 Link encap:UNSPEC  HWaddr   
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:280 (280.0 B)  Byte TX:0 (0.0 B)

vmnet1    Link encap:Ethernet  HWaddr 00:50:56:c0:00:01  
          indirizzo inet:192.168.30.1  Bcast:192.168.30.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:1/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

vmnet8    Link encap:Ethernet  HWaddr 00:50:56:c0:00:08  
          indirizzo inet:192.168.111.1  Bcast:192.168.111.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::250:56ff:fec0:8/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:66 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr   
          indirizzo inet:192.168.27.1  Bcast:192.168.27.255  Maschera:255.255.255.0
          indirizzo inet6: fe80::20e:8eff:fe19:8c4b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:57 errors:0 dropped:0 overruns:0 carrier:0
          collisioni:0 txqueuelen:1000 
          Byte RX:0 (0.0 B)  Byte TX:12570 (12.5 KB)

root@ziomario:/home/mario# nano /etc/default/udhcpd

#DHCPD_ENABLED="no"
comment this line to enable the server,

root@ziomario:/home/mario# nano /etc/udhcpd.conf

start 192.168.27.2
end 192.168.27.254 
opt dns 192.168.2.1
option subnet 255.255.255.0
opt router 192.168.2.1
option  domain  urorgonizaion.edu

root@ziomario:/home/mario# service udhcpd start

Starting very small Busybox based DHCP server: Starting /usr/sbin/udhcpd...
udhcpd.

root@ziomario:/home/mario# echo "1" > /proc/sys/net/ipv4/ip_forward

root@ziomario:/home/mario# iptables --table nat --append POSTROUTING --out-interface eth1 -j MASQUERADE

root@ziomario:/home/mario# iptables --append FORWARD --in-interface wlan0 -j ACCEPT

Do you see some mistake ? The problem is that I can't connect through my Mac Mini / Leopard. It is connected,but unable to surf the net. After some tries,it says : you are not connected to internet.

---

