---
title: "wireless connection to a tp-link router"
date: 2009-04-24
forum: Networking &amp; Wireless
---

### Post by operry5 on 2009-04-24
hi y'all, 

i'm trying to connect (unsuccesfuly so far) to a tp-link router (model#: TP-WR641G)
which has a "wep" protection-level key (ASCII key).

i know i'm typing the right key... i've tried almost every possible definition in my wireless interface...(my "NetworkManager Applet" version is 0.7.0)

i'm not sure about my ubuntu version but it's quite new...

can anyone help me?

---

### Post by rlzyoner on 2009-04-24
Try to connect manually from a shell

sudo iwconfig wlan0 essid YOUR_ESSID
sudo iwconfig wlan0 mode managed
sudo iwconfig wlan0 key YOUR_WEP_KEY
dhclient3

---

### Post by operry5 on 2009-04-25
hi, 
thanks for replying!

i tried to type these commands (at first the last line without sudo- and got all sorts of "no permission" ananouncements, and then as su) and got this:

root@George:/home/operry5# iwconfig wlan0 essid perry
root@George:/home/operry5# iwconfig wlan0 mode managed
root@George:/home/operry5# iwconfig wlan0 key <the key>
root@George:/home/operry5# dhclient3
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

wmaster0: unknown hardware address type 801
wmaster0: unknown hardware address type 801
Listening on LPF/pan0/7a:67:63:5c:a8:d5
Sending on   LPF/pan0/7a:67:63:5c:a8:d5
Listening on LPF/wlan0/00:1b:77:04:2e:02
Sending on   LPF/wlan0/00:1b:77:04:2e:02
Listening on LPF/wmaster0/
Sending on   LPF/wmaster0/
Listening on LPF/eth0/00:0f:b0:d3:8c:b2
Sending on   LPF/eth0/00:0f:b0:d3:8c:b2
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on pan0 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wmaster0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 1
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

(my router's subnet mask is 255.255.255.0 - maybe that the problem?)

---

### Post by operry5 on 2009-04-25
ok, 
now my network interface is connecting!

i have no idea how or why - but it works!

so thanks for your help- problem solved!

---

