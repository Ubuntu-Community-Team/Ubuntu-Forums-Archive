---
title: "Wifi with dhcp works not so much"
date: 2009-04-18
forum: Networking &amp; Wireless
---

### Post by gulivieri on 2009-04-18
Hi folks.
I've a problem with wifi connection. With wired conn (eth0) works fine. Usually got 2.0.1.65 from Dhcp server. With wifi conn (3 different pcmcia devices same behavior: last one is wlan2, a DWL-g630) I got usually 2.0.1.67 but I can't go anywhere. Try ping to default gw (2.0.1.1) and no response, try dhcp server and no response. So, siloed. Tracert doesn't work, nslookup the same and so on, but ... I'm connected to AP, because I have new ip. Event routing tables is set up in the same way (wired and wireless) but I can't go ut (wit wireless!). Furthermore, Access Point AP_a8a7ee where I connect is the same I use with other 2 windows PC, and works fine. It's open without wpa or mac filtering.
DO you have ideas for me?
Below some screenshot
Thanks in advance

iwconfig say
-------------------------------------------------
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan2     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=18 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
-------------------------------------------------
then I Do
$ ifconfig wlan2 up
$ iwconfig wlan2 mode Managed
$ iwconfig wlan2 channel 1
$ iwconfig wlan2 essid AP_a8a7ee

Now I'm going to connect
-------------------------------------------------
root@betelgeuse:/home/gennaro# dhclient wlan2
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/wlan2/00:1c:f0:1b:0d:5d
Sending on   LPF/wlan2/00:1c:f0:1b:0d:5d
Sending on   Socket/fallback
DHCPDISCOVER on wlan2 to 255.255.255.255 port 67 interval 8
DHCPOFFER of 2.0.1.67 from 2.0.1.64
DHCPREQUEST of 2.0.1.67 on wlan2 to 255.255.255.255 port 67
DHCPACK of 2.0.1.67 from 2.0.1.64
**bound to 2.0.1.67** -- renewal in 1746 seconds.
-------------------------------------------------
As you can see, I got an Ip address, but if I try ping 2.0.1.1
--- 2.0.1.1 ping statistics ---
6 packets transmitted, 0 received, 100% packet loss, time 999ms
Further
root@betelgeuse:/home/gennaro# route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
2.0.1.0         0.0.0.0         255.255.255.0   U     0      0        0 wlan2
0.0.0.0         2.0.1.1         0.0.0.0         UG    0      0        0 wlan2


If I do the same with wired (eth0) I everything works fine
root@betelgeuse:/home/gennaro# ifconfig wlan2 down
root@betelgeuse:/home/gennaro# ifconfig eth0 up
root@betelgeuse:/home/gennaro# dhclient eth0
There is already a pid file /var/run/dhclient.pid with pid 6757
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:0b:db:da:66:ff
Sending on   LPF/eth0/00:0b:db:da:66:ff
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
DHCPOFFER of 2.0.1.66 from 2.0.1.64
DHCPREQUEST of 2.0.1.66 on eth0 to 255.255.255.255 port 67
DHCPACK of 2.0.1.66 from 2.0.1.64
bound to 2.0.1.66 -- renewal in 1661 seconds.

Now I got 2.0.1.66, but I can go everywhere
root@betelgeuse:/home/gennaro# ping 2.0.1.1
PING 2.0.1.1 (2.0.1.1) 56(84) bytes of data.
64 bytes from 2.0.1.1: icmp_seq=1 ttl=255 time=5.56 ms
64 bytes from 2.0.1.1: icmp_seq=2 ttl=255 time=1.62 ms
64 bytes from 2.0.1.1: icmp_seq=3 ttl=255 time=1.62 ms

root@betelgeuse:/home/gennaro# nslookup [www.hp.com](www.hp.com)
Server:		62.101.93.101
Address:	62.101.93.101#53

Non-authoritative answer:
[www.hp.com](www.hp.com)	canonical name = [www.hpgtm.nsatc.net](www.hpgtm.nsatc.net).
Name:	[www.hpgtm.nsatc.net](www.hpgtm.nsatc.net)
Address: 15.192.45.27
Name:	[www.hpgtm.nsatc.net](www.hpgtm.nsatc.net)
Address: 15.192.45.22

root@betelgeuse:/home/gennaro# route -n
Tabella di routing IP del kernel
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
2.0.1.0         0.0.0.0         255.255.255.0   U     0      0        0 eth0
0.0.0.0         2.0.1.1         0.0.0.0         UG    0      0        0 eth0

What can I do?
Bye

---

