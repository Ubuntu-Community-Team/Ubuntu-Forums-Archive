---
title: "No network on command prompt if x windows is not running"
date: 2010-06-06
forum: Networking &amp; Wireless
---

### Post by kcn_viper on 2010-06-06
Hi,

I am using ubuntu lucid 10.04. The problem is network is not up when I boot to the command prompt. After I do a startx to start x windows and I enter the keyring password, only then the wireless network comes up.

How do I ensure that the wireless network is connected during boot itself and it is available even when x windows are not running.

This problem has happened after moving from the gnome network-admin to the new network manager. I had this problem in ubuntu 9 but solved it by going back to the gnome network-admin. Is it possible to solve this in lucid without going back to network-admin ?

Thanks,
 kcn

---

### Post by kerry_s on 2010-06-06
put the commands in /etc/rc.local

example:
iwconfig wlan0 essid some-name &
dhclient wlan0 &

---

### Post by kcn_viper on 2010-06-08
Thanks for the response, Kerry.

I tried as you said but the dhcp connection didn't happen.
iwconfig wlan0 essid RT256_6 &
-> This command worked fine.
dhclient wlan0 &
-> This didn't connect to the wireless network.
Output:
There is already a pid file /var/run/dhclient.pid with pid 3680
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)

Listening on LPF/wlan0/00:1d:e0:59:5e:0f
Sending on   LPF/wlan0/00:1d:e0:59:5e:0f
Sending on   Socket/fallback
DHCPREQUEST of 192.168.1.31 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.31 on wlan0 to 255.255.255.255 port 67
DHCPREQUEST of 192.168.1.31 on wlan0 to 255.255.255.255 port 67
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on wlan0 to 255.255.255.255 port 67 interval 3
No DHCPOFFERS received.
Trying recorded lease 192.168.1.31
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.

--- 192.168.1.1 ping statistics ---
1 packets transmitted, 0 received, +1 errors, 100% packet loss, time 0ms

No working leases in persistent database - sleeping.

Thanks,
 kcn

---

### Post by kerry_s on 2010-06-08
did you try putting the command to bring it up?

**ifconfig wlan0 up**

do you need to use a key?
wep:
**iwconfig wlan0 essid "MyEssid" key 1234567890**

ascii:
**iwconfig wlan0 essid "MyEssid" key s:asciikey**

i've never done wpa, so you'll have to look that up.

---

### Post by kcn_viper on 2010-06-09
Hi Kerry, thanks again for the response.

I tried the commands as you suggested. Sorry that I forgot to mention the key to you.
I use a "WEP 40/128 bit key".
I tried these commands:
[B]ifconfig wlan0 up
iwconfig wlan0 essid RT256 key s:2053111111122[/B]
**dhclient wlan0**

But the third command is failing with same output as before.

I have the wireless network correctly configured in '/etc/network/interfaces' but that file is not used anymore. Still there is one interesting thing, when I run '/etc/init.d/networking restart'. It seems the file is used and tried to connect to the wireless network with the local ip mentioned in the file, though it fails to connect that way as well.

Is there no simple way by which I can use the same wireless configuration as saved with the network manager, for this purpose rather than duplicating the configuration in /etc/rc.local ?
Can I go back to gnome network-admin ?
Thanks.

---

