---
title: "DWL-122 Problem (It works but connection falls)"
date: 2006-06-28
forum: Networking &amp; Wireless
---

### Post by Davidios on 2006-06-28
I'm now using a Wi-Fi connection through a DWL-122 (prism2_usb). I'm having troubles with my connection, because it falls from time to time and I have to re run with "ifdown wlan0" and "ifup wlan0". 

That's my /etc/network/interfaces:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
address 192.168.1.39
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ADSL-WIRELESS
wireless_mode managed
wireless_enc on
wlan_ng_key0 1A:00:68:FA:45:18:7A:BC:13:XX:XX:XX:XX

```

And iwconfig:

```
davids@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"ADSL-WIRELESS"  Nickname:"ADSL-WIRELESS"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:A0:C5:DC:1C:38
          Bit Rate:11 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=39/92  Signal level=-53 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Do you have any idea of what's going on?

EDIT: It has been fallen now.
Ifdown...

```
davids@ubuntu:~$ ifdown wlan0
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
davids@ubuntu:~$ sudo ifdown wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:11:95:da:43:4a
Sending on   LPF/wlan0/00:11:95:da:43:4a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
```

Ifup...

```
davids@ubuntu:~$ sudo ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:11:95:da:43:4a
Sending on   LPF/wlan0/00:11:95:da:43:4a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.36 -- renewal in 105508 seconds.

```

---

### Post by Davidios on 2006-06-29
Nobody?

---

### Post by damagedspline on 2006-07-28
> **Davidios said:**
> I'm now using a Wi-Fi connection through a DWL-122 (prism2_usb). I'm having troubles with my connection, because it falls from time to time and I have to re run with "ifdown wlan0" and "ifup wlan0". 

That's my /etc/network/interfaces:

```
auto lo
iface lo inet loopback


iface eth0 inet dhcp


iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp
address 192.168.1.39
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ADSL-WIRELESS
wireless_mode managed
wireless_enc on
wlan_ng_key0 1A:00:68:FA:45:18:7A:BC:13:XX:XX:XX:XX

```

And iwconfig:

```
davids@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     IEEE 802.11-b  ESSID:"ADSL-WIRELESS"  Nickname:"ADSL-WIRELESS"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:A0:C5:DC:1C:38
          Bit Rate:11 Mb/s   Tx-Power:18 dBm
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality=39/92  Signal level=-53 dBm  Noise level=-93 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

Do you have any idea of what's going on?

EDIT: It has been fallen now.
Ifdown...

```
davids@ubuntu:~$ ifdown wlan0
ifdown: failed to open statefile /var/run/network/ifstate: Permission denied
davids@ubuntu:~$ sudo ifdown wlan0
Password:
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:11:95:da:43:4a
Sending on   LPF/wlan0/00:11:95:da:43:4a
Sending on   Socket/fallback
DHCPRELEASE on wlan0 to 192.168.1.1 port 67
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
```

Ifup...

```
davids@ubuntu:~$ sudo ifup wlan0
Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set Encode" (8B2A) :
    SET failed on device wlan0 ; Operation not supported.
Error for wireless request "Set ESSID" (8B1A) :
    SET failed on device wlan0 ; Operation not supported.
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

Listening on LPF/wlan0/00:11:95:da:43:4a
Sending on   LPF/wlan0/00:11:95:da:43:4a
Sending on   Socket/fallback
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 7
DHCPOFFER from 192.168.1.1
DHCPREQUEST on wlan0 to 255.255.255.255 port 67
DHCPACK from 192.168.1.1
bound to 192.168.1.36 -- renewal in 105508 seconds.

```
I have the same problem:
 change the wlan0 section to (i've written comments on the changes - leave those out)
```

auto wlan0
iface wlan0 inet dhcp
address 192.168.1.39
netmask 255.255.255.0
gateway 192.168.1.1
wireless-essid ADSL-WIRELESS
wireless-mode managed ;changed from _ to -
wireless-enc on ;changed from _ to -
wlan-ng-key0 1A:00:68:FA:45:18:7A:BC:13:XX:XX:XX:XX ;changed from _ to -  

```

EDIT: 
[https://launchpad.net/distros/ubuntu/+source/linux-wlan-ng/+bug/37451](https://launchpad.net/distros/ubuntu/+source/linux-wlan-ng/+bug/37451)
there is a patch to make the gnome networking applet "behave" on this card - so manual editing will not be required

---

### Post by Davidios on 2006-07-28
Thank you VERY MUCH!:D I will try it.

---

