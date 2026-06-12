---
title: "[SOLVED] E169 shows connect, but no internet ?"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by oygle on 2008-12-23
Recently upgraded to 8.10 as I was having problems getting the E169 USB wireless modem working on 8.04

The new network manager with 8.10 has auto setup the connection, and the icon says it is connected, but I can't get out to the internet, can ping across eth0, but can't ping out to any sites either.

Here is some info from the sys logs ..

> 
Dec 24 10:53:44 ******* NetworkManager: <info>  Activation (ttyUSB0) starting connection 'Optus 3G' 
Dec 24 10:53:44 ******* NetworkManager: <info>  (ttyUSB0): device state change: 3 -> 4 
Dec 24 10:53:44 ******* NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 10:53:44 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) scheduled... 
Dec 24 10:53:44 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) started... 
Dec 24 10:53:44 ******* NetworkManager: <debug> [1230076424.931065] nm_serial_device_open(): (ttyUSB0) opening device... 
Dec 24 10:53:44 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 1 of 5 (Device Prepare) complete. 
Dec 24 10:53:45 ******* NetworkManager: <info>  (ttyUSB0): powering up... 
Dec 24 10:53:45 ******* NetworkManager: <info>  Registered on Home network 
Dec 24 10:53:45 ******* NetworkManager: <info>  Associated with network: +COPS: 0,2,"50502",2 
Dec 24 10:53:45 ******* NetworkManager: <info>  Connected, Woo! 
Dec 24 10:53:45 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) scheduled... 
Dec 24 10:53:45 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) starting... 
Dec 24 10:53:45 ******* NetworkManager: <info>  (ttyUSB0): device state change: 4 -> 5 
Dec 24 10:53:45 ******* NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 10:53:45 ******* NetworkManager: <info>  Starting pppd connection 
Dec 24 10:53:45 ******* NetworkManager: <debug> [1230076425.233329] nm_ppp_manager_start(): Command line: /usr/sbin/pppd nodetach lock nodefaultroute ttyUSB0 noipdefault usepeerdns lcp-echo-failure 0 lcp-echo-interval 0 ipparam /org/freedesktop/NetworkManager/PPP/1 plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so 
Dec 24 10:53:45 ******* NetworkManager: <debug> [1230076425.234425] nm_ppp_manager_start(): ppp started with pid 10282 
Dec 24 10:53:45 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 2 of 5 (Device Configure) complete. 
Dec 24 10:53:45 ******* pppd[10282]: Plugin /usr/lib/pppd/2.4.4/nm-pppd-plugin.so loaded.
Dec 24 10:53:45 ******* pppd[10282]: pppd 2.4.4 started by root, uid 0
Dec 24 10:53:45 ******* pppd[10282]: Using interface ppp0
Dec 24 10:53:45 ******* pppd[10282]: Connect: ppp0 <--> /dev/ttyUSB0
Dec 24 10:53:45 ******* NetworkManager: <info>  (ttyUSB0): device state change: 5 -> 6 
Dec 24 10:53:45 ******* NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 10:53:48 ******* pppd[10282]: CHAP authentication succeeded
Dec 24 10:53:48 ******* pppd[10282]: CHAP authentication succeeded
Dec 24 10:53:48 ******* NetworkManager: <info>  (ttyUSB0): device state change: 6 -> 7 
Dec 24 10:53:48 ******* NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 10:53:54 ******* pppd[10282]: Could not determine remote IP address: defaulting to 10.64.64.64
Dec 24 10:53:54 ******* pppd[10282]: Cannot determine ethernet address for proxy ARP
Dec 24 10:53:54 ******* pppd[10282]: local  IP address 220.233.***.***
Dec 24 10:53:54 ******* pppd[10282]: remote IP address 10.64.64.64
Dec 24 10:53:54 ******* NetworkManager: <info>  PPP manager(IP Config Get) reply received. 
Dec 24 10:53:54 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) scheduled... 
Dec 24 10:53:54 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) started... 
Dec 24 10:53:54 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) scheduled... 
Dec 24 10:53:54 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 4 of 5 (IP Configure Get) complete. 
Dec 24 10:53:54 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) started... 
Dec 24 10:53:55 ******* NetworkManager: <info>  (ttyUSB0): device state change: 7 -> 8 
Dec 24 10:53:55 ******* NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see [http://bugs.launchpad.net/bugs/191889](http://bugs.launchpad.net/bugs/191889)) 
Dec 24 10:53:55 ******* NetworkManager: <info>  Policy set 'Optus 3G' (ppp0) as default for routing and DNS. 
Dec 24 10:53:55 ******* NetworkManager: <info>  Activation (ttyUSB0) successful, device activated. 
Dec 24 10:53:55 ******* NetworkManager: <info>  Activation (ttyUSB0) Stage 5 of 5 (IP Configure Commit) complete. 
Dec 24 10:53:56 ******* ntpdate[10753]: can't find host ntp.ubuntu.com 
Dec 24 10:53:56 ******* ntpdate[10753]: no servers can be used, exiting

I see that bug is a Firefox one. Package manager tells me the vers of network manager I'm using is 0.7~~svn20081018tl05859-0ubuntu1.8.10.1

With the USB dongle attached directly to the computer (i.e. NOT to a router), I assume Ubuntu treats it as ppp0 .

Do I have to run wvdial  ??

Oygle

---

### Post by oygle on 2008-12-24
Results from lsusb ..

> $ lsusb
Bus 005 Device 003: ID 12d1:1001 Huawei Technologies Co., Ltd. E620 USB Modem
Bus 005 Device 002: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
$


Ubuntu thinks it is an E620 ?  Any clues please ?

Oygle

---

### Post by superprash2003 on 2008-12-24
post output of
1)ifconfig
2)cat /etc/resolv.conf


merry christmas..

---

### Post by oygle on 2008-12-24
> **superprash2003 said:**
> post output of
1)ifconfig



```
$ ifconfig
eth0 Link encap:Ethernet HWaddr **:**:**:**:**:**
inet addr:192.168.1.*** Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: ****::****:****:****:****/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:9 errors:0 dropped:0 overruns:0 frame:0
TX packets:7 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:702 (702.0 B) TX bytes:556 (556.0 B)
Interrupt:17

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:114 errors:0 dropped:0 overruns:0 frame:0
TX packets:114 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:7784 (7.7 KB) TX bytes:7784 (7.7 KB)

```

> **superprash2003 said:**
> 
2)cat /etc/resolv.conf


```
  Generated by NetworkManager
```

Oygle

---

### Post by oygle on 2008-12-26
See [this thread]("http://ubuntuforums.org/showthread.php?t=1020418") , for the continuing saga.  :)

This is 'solved' to some degree, have got the wireless connection going okay, but have 'lost' etho, see [here]("http://ubuntuforums.org/showthread.php?t=1022569")

---

