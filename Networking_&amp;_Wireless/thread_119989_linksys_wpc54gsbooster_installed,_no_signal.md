---
title: "linksys wpc54gs/booster installed, no signal"
date: 2006-01-20
forum: Networking &amp; Wireless
---

### Post by elp on 2006-01-20
I am new-b with Linux, I installed linksys wpc54gs/booster according to the instruction on google search but no connection, see my snap shots as attachment and advise me[COLOR="black"][ATTACH]5464[/ATTACH]

[ATTACH]5465[/ATTACH]

[ATTACH]5466[/ATTACH]

[ATTACH]5467[/ATTACH]

[ATTACH]5468[/ATTACH]........[/COLOR]..........thanks

elp7@ubuntu:~$ sudo iwconfig
Password:
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:00:00:00:00:00
          Bit Rate:54 Mb/s   Tx-Power:25 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:100/100  Signal level:-10 dBm  Noise level:-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

elp7@ubuntu:~$ sudo ifwpriv
sudo: ifwpriv: command not found
elp7@ubuntu:~$ sudo iwpriv
lo        no private ioctls.

eth0      no private ioctls.

wlan0     Available private ioctls :
          setwpa           (8BE1) : set   1 int   & get   0
          setkey           (8BE2) : set   1 int   & get   0
          associate        (8BE3) : set   1 int   & get   0
          disassociate     (8BE4) : set   1 int   & get   0
          drop_unencrypted (8BE5) : set   1 int   & get   0
          countermeasures  (8BE6) : set   1 int   & get   0
          deauthenticate   (8BE7) : set   1 int   & get   0
          auth_alg         (8BE8) : set   1 int   & get   0
          ndis_reset       (8BF0) : set   0       & get   0
          power_profile    (8BF1) : set   1 int   & get   0
          network_type     (8BF2) : set   1 char  & get   0

sit0      no private ioctls.

elp7@ubuntu:~$ sudo ifup wlan0
There is already a pid file /var/run/dhclient.wlan0.pid with pid 0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/wlan0/00:90:4b:5f:77:47
Sending on   LPF/wlan0/00:90:4b:5f:77:47
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 18
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 2
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
thnaks again

---

