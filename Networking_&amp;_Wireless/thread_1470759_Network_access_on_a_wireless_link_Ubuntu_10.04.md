---
title: "Network access on a wireless link Ubuntu 10.04"
date: 2010-05-03
forum: Networking &amp; Wireless
---

### Post by antonfh on 2010-05-03
I have an issue also with Wireless networking.

Seems that although it picks up my device and scans for available wireless AP, and connects to my wireless router and assigns the correct IP and netmask and gateway (DHCP and even tried fixed manual config), I cannot ping anything on the network and therefor cant browse etc.

What  I have noticed is, that once I am connected to the wireless access point a ping of the router 10.0.0.2 returns a response ... but then after about a minute or so .. it suddenly starts saying "Destination Host Unreachable"

I have stopped Firestarter, started it, flushed my IPtables etc ... but still cannot ping any host or the router


A full list of configuration/results below, also note that If i connect via ethernet then all works fine (I can browse, ping host on network etc, its only on a wireless link that I get these issue?)



[FONT="Courier New"][COLOR="DarkGreen"]eth0      Link encap:Ethernet  HWaddr 00:90:f5:9d:e9:a4 
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:35

lo        Link encap:Local Loopback 
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4551 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4551 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:581109 (581.1 KB)  TX bytes:581109 (581.1 KB)

wlan0     Link encap:Ethernet  HWaddr e0:91:53:11:70:99 
          inet addr:10.0.0.209  Bcast:10.255.255.255  Mask:255.0.0.0
          inet6 addr: fe80::e291:53ff:fe11:7099/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:135 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:38697 (38.6 KB)  TX bytes:15193 (15.1 KB)
          Interrupt:18 Memory:ffffc90011ff8000-ffffc90011ff8100
[/COLOR][/FONT]

root@antonubuntu10:~# ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=254 time=3.90 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=254 time=1.93 ms
64 bytes from 10.0.0.2: icmp_seq=3 ttl=254 time=1.75 ms
64 bytes from 10.0.0.2: icmp_seq=4 ttl=254 time=13.0 ms
64 bytes from 10.0.0.2: icmp_seq=5 ttl=254 time=1.80 ms
64 bytes from 10.0.0.2: icmp_seq=6 ttl=254 time=2.14 ms
64 bytes from 10.0.0.2: icmp_seq=7 ttl=254 time=1.80 ms

... and then it will start saying this :

From 10.0.0.209 icmp_seq=1 Destination Host Unreachable
From 10.0.0.209 icmp_seq=2 Destination Host Unreachable
From 10.0.0.209 icmp_seq=3 Destination Host Unreachable
From 10.0.0.209 icmp_seq=5 Destination Host Unreachable
From 10.0.0.209 icmp_seq=6 Destination Host Unreachable
From 10.0.0.209 icmp_seq=7 Destination Host Unreachable
From 10.0.0.209 icmp_seq=10 Destination Host Unreachable
From 10.0.0.209 icmp_seq=11 Destination Host Unreachable


root@antonubuntu10:~# netstat -r
Kernel IP routing table
Destination     Gateway         Genmask         Flags   MSS Window  irtt Iface
link-local      *               255.255.0.0     U         0 0          0 wlan0
10.0.0.0        *               255.0.0.0       U         0 0          0 wlan0
default         10.0.0.2        0.0.0.0         UG        0 0          0 wlan0


Below some entries of the Syslog

```
May  1 22:26:04 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 2 of 5 (Device Configure) complete.
May  1 22:26:04 antonubuntu10 NetworkManager: <info>  Config: set interface ap_scan to 1
May  1 22:26:04 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> disconnected
May  1 22:26:04 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> scanning
May  1 22:26:11 antonubuntu10 kernel: [ 3968.689479] ----------->rtl8192se_check_hw_scan()
May  1 22:26:11 antonubuntu10 kernel: [ 3968.689486] FW Scan long time without stop, stop hw scan
May  1 22:26:11 antonubuntu10 kernel: [ 3968.690503] <-----------rtl8192se_check_hw_scan()
May  1 22:26:18 antonubuntu10 kernel: [ 3975.683696] ----------->rtl8192se_check_hw_scan()
May  1 22:26:18 antonubuntu10 kernel: [ 3975.683702] FW Scan long time without stop, stop hw scan
May  1 22:26:18 antonubuntu10 kernel: [ 3975.684717] <-----------rtl8192se_check_hw_scan()
May  1 22:26:18 antonubuntu10 wpa_supplicant[1297]: Trying to associate with 00:04:ed:5d:4b:93 (SSID='WlanAFH' freq=2412 MHz)
May  1 22:26:18 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  scanning -> associating
May  1 22:26:18 antonubuntu10 kernel: [ 3975.686134] ===>rtllib_start_scan()
May  1 22:26:20 antonubuntu10 NetworkManager: <info>  wlan0: link timed out.
May  1 22:26:25 antonubuntu10 netlogond[1562]: [LWNetDnsQueryWithBuffer() lwnet-dns.c:1185] DNS lookup for '_ldap._tcp.dc._msdcs.corp.net' failed with errno 111, h_errno = 2
May  1 22:26:25 antonubuntu10 kernel: [ 3982.678864] ----------->rtl8192se_check_hw_scan()
May  1 22:26:25 antonubuntu10 kernel: [ 3982.678870] FW Scan long time without stop, stop hw scan
May  1 22:26:25 antonubuntu10 kernel: [ 3982.679883] <-----------rtl8192se_check_hw_scan()
May  1 22:26:25 antonubuntu10 kernel: [ 3982.680117] Linking with WlanAFH,channel:1, qos:0, myHT:0, networkHT:0, mode:6 cur_net.flags:0x406
May  1 22:26:25 antonubuntu10 kernel: [ 3982.680146] ===>rtllib_associate_procedure_wq(), chan:1
May  1 22:26:25 antonubuntu10 kernel: [ 3982.680151] HTSetConnectBwMode():pHTInfo->bCurBW40MHz:0
May  1 22:26:25 antonubuntu10 wpa_supplicant[1297]: Association request to the driver failed
May  1 22:26:25 antonubuntu10 kernel: [ 3982.690256] rtllib_authentication_req():auth->algorithm is OPEN
May  1 22:26:25 antonubuntu10 kernel: [ 3982.691770] rtl8192_SetWirelessMode(), wireless_mode:4, bEnableHT = 0
May  1 22:26:25 antonubuntu10 kernel: [ 3982.695292] Associated successfully
May  1 22:26:25 antonubuntu10 kernel: [ 3982.695297] normal associate
May  1 22:26:25 antonubuntu10 kernel: [ 3982.695312] Using G rates:108
May  1 22:26:25 antonubuntu10 kernel: [ 3982.695315] Successfully associated, ht not enabled(0, 0)
May  1 22:26:25 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> 4-way handshake
May  1 22:26:25 antonubuntu10 kernel: [ 3982.697864] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
May  1 22:26:25 antonubuntu10 wpa_supplicant[1297]: Associated with 00:04:ed:5d:4b:93
May  1 22:26:25 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> associated
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  associated -> 4-way handshake
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  4-way handshake -> group handshake
May  1 22:26:26 antonubuntu10 kernel: [ 3983.701021] alg name:TKIP
May  1 22:26:26 antonubuntu10 wpa_supplicant[1297]: WPA: Key negotiation completed with 00:04:ed:5d:4b:93 [PTK=TKIP GTK=TKIP]
May  1 22:26:26 antonubuntu10 wpa_supplicant[1297]: CTRL-EVENT-CONNECTED - Connection to 00:04:ed:5d:4b:93 completed (auth) [id=0 id_str=]
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  (wlan0): supplicant connection state:  group handshake -> completed
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0/wireless) Stage 2 of 5 (Device Configure) successful.  Connected to wireless network 'WlanAFH'.
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) scheduled.
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) started...
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  (wlan0): device state change: 5 -> 7 (reason 0)
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) scheduled...
May  1 22:26:26 antonubuntu10 kernel: [ 3983.704270] alg name:TKIP
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) scheduled...
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 3 of 5 (IP Configure Start) complete.
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) started...
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP4 Configure Get) complete.
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) started...
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) scheduled...
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 4 of 5 (IP6 Configure Get) complete.
May  1 22:26:26 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) started...
May  1 22:26:26 antonubuntu10 avahi-daemon[1145]: Joining mDNS multicast group on interface wlan0.IPv4 with address 10.0.0.209.
May  1 22:26:26 antonubuntu10 avahi-daemon[1145]: New relevant interface wlan0.IPv4 for mDNS.
May  1 22:26:26 antonubuntu10 avahi-daemon[1145]: Registering new address record for 10.0.0.209 on wlan0.IPv4.
May  1 22:26:27 antonubuntu10 avahi-daemon[1145]: Registering new address record for fe80::e291:53ff:fe11:7099 on wlan0.*.
May  1 22:26:27 antonubuntu10 NetworkManager: <info>  (wlan0): device state change: 7 -> 8 (reason 0)
May  1 22:26:27 antonubuntu10 NetworkManager: <info>  Policy set 'Auto WlanAFH' (wlan0) as default for routing and DNS.
May  1 22:26:27 antonubuntu10 NetworkManager: <info>  Activation (wlan0) successful, device activated.
May  1 22:26:27 antonubuntu10 NetworkManager: <info>  Activation (wlan0) Stage 5 of 5 (IP Configure Commit) complete.
May  1 22:26:29 antonubuntu10 ntpdate[13536]: adjust time server 91.189.94.4 offset -0.010567 sec
May  1 22:26:36 antonubuntu10 kernel: [ 3993.392438] wlan0: no IPv6 routers present
May  1 22:26:55 antonubuntu10 kernel: [ 4012.138083] LPS leave: notify AP we are awaked ++++++++++ SendNullFunctionData
May  1 22:27:02 antonubuntu10 kernel: [ 4019.184347] ----------->rtl8192se_check_hw_scan()
May  1 22:27:02 antonubuntu10 kernel: [ 4019.184352] FW Scan long time without stop, stop hw scan
May  1 22:27:02 antonubuntu10 kernel: [ 4019.185368] <-----------rtl8192se_check_hw_scan()
May  1 22:27:42 antonubuntu10 kernel: [ 4059.096615] ----------->rtl8192se_check_hw_scan()
May  1 22:27:42 antonubuntu10 kernel: [ 4059.096621] FW Scan long time without stop, stop hw scan
May  1 22:27:42 antonubuntu10 kernel: [ 4059.097635] <-----------rtl8192se_check_hw_scan()
```

---

