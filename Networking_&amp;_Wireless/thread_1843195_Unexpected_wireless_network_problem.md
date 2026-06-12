---
title: "Unexpected wireless network problem"
date: 2011-09-13
forum: Networking &amp; Wireless
---

### Post by sabotatore on 2011-09-13
Hello, now I live in hotel in LA. Few weeks everything was good with wi-fi network. But in saturday something was happened and I don't have internet access after that. My android phone works fine through this wi-fi.

But my Ubuntu don't has access to dns. I get errors like this: "Error 105 (net::ERR_NAME_NOT_RESOLVED): Unable to resolve the server's DNS address."

Syslog looks good:

Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0) starting connection 'Auto Goesh'
Sep 12 22:31:38 sab NetworkManager[1144]: <info> (wlan0): device state change: 3 -> 4 (reason 0)
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) scheduled...
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) started...
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) scheduled...
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 1 of 5 (Device Prepare) complete.
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) starting...
Sep 12 22:31:38 sab NetworkManager[1144]: <info> (wlan0): device state change: 4 -> 5 (reason 0)
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0/wireless): connection 'Auto Goesh' requires no security.  No secrets needed.
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Config: added 'ssid' value 'Goesh'
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Config: added 'scan_ssid' value '1'
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Config: added 'key_mgmt' value 'NONE'
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
Sep 12 22:31:38 sab NetworkManager[1144]: <info> Config: set interface ap_scan to 1
Sep 12 22:31:38 sab NetworkManager[1144]: <info> (wlan0): supplicant connection state:  disconnected -> scanning
Sep 12 22:31:40 sab wpa_supplicant[1325]: Trying to associate with 00:03:52:aa:e9:00 (SSID='Goesh' freq=2412 MHz)
Sep 12 22:31:40 sab NetworkManager[1144]: <info> (wlan0): supplicant connection state:  scanning -> associating
Sep 12 22:31:40 sab kernel: [50714.000041] wlan0: authenticate with 00:03:52:aa:e9:00 (try 1)
Sep 12 22:31:40 sab kernel: [50714.002374] wlan0: authenticated
Sep 12 22:31:40 sab kernel: [50714.002449] wlan0: associate with 00:03:52:aa:e9:00 (try 1)
Sep 12 22:31:40 sab kernel: [50714.004442] wlan0: RX AssocResp from 00:03:52:aa:e9:00 (capab=0x21 status=0 aid=2)
Sep 12 22:31:40 sab kernel: [50714.004445] wlan0: associated
Sep 12 22:31:40 sab wpa_supplicant[1325]: Associated with 00:03:52:aa:e9:00
Sep 12 22:31:40 sab wpa_supplicant[1325]: CTRL-EVENT-CONNECTED - Connection to 00:03:52:aa:e9:00 completed (reauth) [id=0 id_str=]
Sep 12 22:31:40 sab NetworkManager[1144]: <info> (wlan0): supplicant connection state:  associating -> associated
Sep 12 22:31:40 sab NetworkManager[1144]: <info> (wlan0): supplicant connection state:  associated -> completed
Sep 12 22:31:40 sab NetworkManager[1144]: <info> Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'Goesh'.
Sep 12 22:31:40 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
Sep 12 22:31:40 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
Sep 12 22:31:40 sab NetworkManager[1144]: <info> (wlan0): device state change: 5 -> 7 (reason 0)
Sep 12 22:31:40 sab NetworkManager[1144]: <info> Activation (wlan0) Beginning DHCPv4 transaction (timeout in 45 seconds)
Sep 12 22:31:40 sab NetworkManager[1144]: <info> dhclient started with pid 25965
Sep 12 22:31:40 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
Sep 12 22:31:40 sab dhclient: Internet Systems Consortium DHCP Client 4.1.1-P1
Sep 12 22:31:40 sab dhclient: Copyright 2004-2010 Internet Systems Consortium.
Sep 12 22:31:40 sab dhclient: All rights reserved.
Sep 12 22:31:40 sab dhclient: For info, please visit [https://www.isc.org/software/dhcp/](https://www.isc.org/software/dhcp/)
Sep 12 22:31:40 sab dhclient:
Sep 12 22:31:40 sab NetworkManager[1144]: <info> (wlan0): DHCPv4 state changed nbi -> preinit
Sep 12 22:31:40 sab dhclient: Listening on LPF/wlan0/00:24:d7:d7:d7:b4
Sep 12 22:31:40 sab dhclient: Sending on   LPF/wlan0/00:24:d7:d7:d7:b4
Sep 12 22:31:40 sab dhclient: Sending on   Socket/fallback
Sep 12 22:31:40 sab dhclient: DHCPREQUEST of 172.17.106.210 on wlan0 to 255.255.255.255 port 67
Sep 12 22:31:42 sab dhclient: DHCPACK of 172.17.106.210 from 172.17.1.1
Sep 12 22:31:42 sab dhclient: bound to 172.17.106.210 -- renewal in 37013 seconds.
Sep 12 22:31:42 sab NetworkManager[1144]: <info> (wlan0): DHCPv4 state changed preinit -> reboot
Sep 12 22:31:42 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
Sep 12 22:31:42 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
Sep 12 22:31:42 sab NetworkManager[1144]: <info>   address 172.17.106.210
Sep 12 22:31:42 sab NetworkManager[1144]: <info>   prefix 16 (255.255.0.0)
Sep 12 22:31:42 sab NetworkManager[1144]: <info>   gateway 172.17.1.1
Sep 12 22:31:42 sab NetworkManager[1144]: <info>   nameserver '4.2.2.1'
Sep 12 22:31:42 sab NetworkManager[1144]: <info>   domain name 'globalsuite.net'
Sep 12 22:31:42 sab NetworkManager[1144]: <info> Scheduling stage 5
Sep 12 22:31:42 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
Sep 12 22:31:42 sab NetworkManager[1144]: <info> Done scheduling stage 5
Sep 12 22:31:42 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
Sep 12 22:31:42 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
Sep 12 22:31:42 sab avahi-daemon[1235]: Joining mDNS multicast group on interface wlan0.IPv4 with address 172.17.106.210.
Sep 12 22:31:42 sab avahi-daemon[1235]: New relevant interface wlan0.IPv4 for mDNS.
Sep 12 22:31:42 sab avahi-daemon[1235]: Registering new address record for 172.17.106.210 on wlan0.IPv4.
Sep 12 22:31:43 sab NetworkManager[1144]: <info> (wlan0): device state change: 7 -> 8 (reason 0)
Sep 12 22:31:43 sab NetworkManager[1144]: <info> (wlan0): roamed from BSSID 00:03:52:A9:E5:90 (Goesh) to 00:03:52:AA:E9:00 (Goesh)
Sep 12 22:31:43 sab NetworkManager[1144]: <info> Policy set 'Auto Goesh' (wlan0) as default for IPv4 routing and DNS.
Sep 12 22:31:43 sab NetworkManager[1144]: <info> Activation (wlan0) successful, device activated.
Sep 12 22:31:43 sab NetworkManager[1144]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.

But I can't ping anything:

#nameserver
$ ping -c 5 4.2.2.1
PING 4.2.2.1 (4.2.2.1) 56(84) bytes of data.

--- 4.2.2.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms

# gateway

$ ping -c 5 172.17.1.1
PING 172.17.1.1 (172.17.1.1) 56(84) bytes of data.

--- 172.17.1.1 ping statistics ---
5 packets transmitted, 0 received, 100% packet loss, time 4031ms


What could it be?

---

### Post by psrdotcom on 2011-09-13
Try to ping the localhost and ping your ip address. Let us know the result.

There might be limit in the number of addresses assignment in the DHCP (Router)?

Not Sure, just check with the network manager.

---

### Post by sabotatore on 2011-09-13
$ ping -c 5 172.17.106.210
PING 172.17.106.210 (172.17.106.210) 56(84) bytes of data.
64 bytes from 172.17.106.210: icmp_req=1 ttl=64 time=0.058 ms
64 bytes from 172.17.106.210: icmp_req=2 ttl=64 time=0.044 ms
64 bytes from 172.17.106.210: icmp_req=3 ttl=64 time=0.041 ms
64 bytes from 172.17.106.210: icmp_req=4 ttl=64 time=0.048 ms
64 bytes from 172.17.106.210: icmp_req=5 ttl=64 time=0.054 ms

--- 172.17.106.210 ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3997ms
rtt min/avg/max/mdev = 0.041/0.049/0.058/0.006 ms


$ ping -c 5 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_req=1 ttl=64 time=0.051 ms
64 bytes from localhost (127.0.0.1): icmp_req=2 ttl=64 time=0.045 ms
64 bytes from localhost (127.0.0.1): icmp_req=3 ttl=64 time=0.045 ms
64 bytes from localhost (127.0.0.1): icmp_req=4 ttl=64 time=0.017 ms
64 bytes from localhost (127.0.0.1): icmp_req=5 ttl=64 time=0.044 ms

--- localhost ping statistics ---
5 packets transmitted, 5 received, 0% packet loss, time 3996ms
rtt min/avg/max/mdev = 0.017/0.040/0.051/0.013 ms

It continues during last 2 days...

---

### Post by fdrake on 2011-09-13
try please these commands:
```

sudo /etc/init.d/network-manager stop
sudo ifconfig wlan0 down
sudo ifconfig wlan0 up
sudo /etc/init.d/network-manager start

```
if that does not work please post results for:
```

less /etc/NetworkManager/nm-system-settings.conf
less /etc/network/interfaces

```

---

### Post by sabotatore on 2011-09-13
$ cat /etc/NetworkManager/nm-system-settings.conf
cat: /etc/NetworkManager/nm-system-settings.conf: No such file or directory


$ cat /etc/NetworkManager/NetworkManager.conf 
# This file is installed into /etc/NetworkManager, and is loaded by 
# NetworkManager by default.  To override, specify: '--config file' 
# during NM startup.  This can be done by appending to DAEMON_OPTS in 
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false


$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

---

### Post by sabotatore on 2011-09-13
Forgot to add: everything works fine with another wi-fi networks..

---

### Post by fdrake on 2011-09-13
try to change the files to
```

$ sudo gedit /etc/NetworkManager/NetworkManager.conf
```
> # This file is installed into /etc/NetworkManager, and is loaded by
# NetworkManager by default. To override, specify: '--config file'
# during NM startup. This can be done by appending to DAEMON_OPTS in
# the file:
#
# /etc/default/NetworkManager
#

[main]
plugins=ifupdown,keyfile

[ifupdown]
[COLOR="Red"]_**managed=true**_[/COLOR]

```

$ sudo gedit /etc/network/interfaces
```
> auto lo
iface lo inet loopback

[COLOR="Red"][B][U]auto wlan0
iface wlan0 inet dhcp[/U][/B][/COLOR]

edit: is the network that your have problems with using any encryption/password or it's open? can you possibly ask the managment to restart/reset the router.

---

### Post by sabotatore on 2011-09-13
Nothing changed..

---

### Post by sabotatore on 2011-09-13
I repeate..  everything works fine with another wi-fi networks..
latest syslog in attach..

---

### Post by fdrake on 2011-09-13
from your log , it looks like that there is no encryption problem adn you are even able to connect to the DCHP until something happens:

> 
Sep 13 00:12:14 sab NetworkManager[1047]: <info> Activation (wlan0) successful, device activated.
Sep 13 00:12:14 sab NetworkManager[1047]: <info> Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
[COLOR="Red"][B][U]Sep 13 00:12:17 sab init: plymouth-stop pre-start process (1869) terminated with status 1
Sep 13 00:12:18 sab ntpd[1342]: ntpd exiting on signal 15[/U][/B][/COLOR]
Sep 13 00:12:19 sab ntpd_intres[1346]: parent died before we finished, exiting
Sep 13 00:12:23 sab kernel: [   90.161147] wlan0: no IPv6 routers present
 
it's not very clear what it may be the problem. I'll try to do a research in the meantime.

can you please post the result of a scan of the network. Tell us which network are you able to connect with no issues:
i assume the network you have problems is "Goesh".
```

sudo iwlist scan

```

---

### Post by sabotatore on 2011-09-13
I can use at&t wi-fi in starbucks and wi-fi in my work..

$sudo iwlist scan: 

wlan0     Scan completed :
          Cell 01 - Address: 00:03:52:AA:E9:00
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=57/70  Signal level=-53 dBm  
                    Encryption key:off
                    ESSID:"Goesh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=0000000969632181
                    Extra: Last beacon: 148ms ago
                    IE: Unknown: 0005476F657368
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
          Cell 02 - Address: 00:03:52:CF:68:70
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=41/70  Signal level=-69 dBm  
                    Encryption key:off
                    ESSID:"Goesh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000075bcd21be
                    Extra: Last beacon: 5912ms ago
                    IE: Unknown: 0005476F657368
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101
          Cell 03 - Address: 00:03:52:A9:E5:90
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=54/70  Signal level=-56 dBm  
                    Encryption key:off
                    ESSID:"Goesh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000096a9cf773
                    Extra: Last beacon: 5552ms ago
                    IE: Unknown: 0005476F657368
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030106
          Cell 04 - Address: 00:03:52:A8:6A:E0
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=28/70  Signal level=-82 dBm  
                    Encryption key:off
                    ESSID:"Goesh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000096ab4a181
                    Extra: Last beacon: 4916ms ago
                    IE: Unknown: 0005476F657368
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
          Cell 05 - Address: 00:03:52:AA:47:70
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=31/70  Signal level=-79 dBm  
                    Encryption key:off
                    ESSID:"Goesh"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Mode:Master
                    Extra:tsf=000000096a7ad181
                    Extra: Last beacon: 5928ms ago
                    IE: Unknown: 0005476F657368
                    IE: Unknown: 010482848B96
                    IE: Unknown: 030101

---

### Post by praseodym on 2011-09-13
Hi,

there are 5 networks with the same ESSID, even some on the same channel. Put the hardware address of the access point you want to connect to into the field [COLOR="Red"]B[/COLOR]SSID in the network-manager applet.

Example:

```
wlan0 Scan completed :
Cell 01 - Address: [COLOR="Red"]00:03:52:AA:E9:00[/COLOR]
```

---

### Post by sabotatore on 2011-09-13
> **praseodym said:**
> Hi,

there are 5 networks with the same ESSID, even some on the same channel. Put the hardware address of the access point you want to connect to into the field [COLOR="Red"]B[/COLOR]SSID in the network-manager applet.

Example:

```
wlan0 Scan completed :
Cell 01 - Address: [COLOR="Red"]00:03:52:AA:E9:00[/COLOR]
```

After I did that something had to change?

---

### Post by praseodym on 2011-09-14
The network-manager cannot decide which access point to use with 5 same ESSIDs

---

### Post by sabotatore on 2011-09-20
Problem solved.. My mac address was banned..

---

