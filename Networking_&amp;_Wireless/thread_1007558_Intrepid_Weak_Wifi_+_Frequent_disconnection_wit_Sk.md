---
title: "Intrepid Weak Wifi + Frequent disconnection wit Skype"
date: 2008-12-10
forum: Networking &amp; Wireless
---

### Post by ubuser_7 on 2008-12-10
Hi Everyone

I am using Intrepid and my wifi works just fine. Ever since I upgraded from 8.04 I have been having some signal problems. I will be sitting on the same table with my Wifi router and I will still be having like half a signal.

Going into the next room, the speed goes down and I get frequent disconnections from my wireless network. I tried this with nearly 3-4 routers.

Now going one step further, sitting a couple of feet from my wifi router, and using skype I get disconnected like every 3 minutes or so.


Here is some basic information:


```

name -a
Linux zeppelin 2.6.27-9-generic #1 SMP Thu Nov 20 22:15:32 UTC 2008 x86_64 GNU/Linux

```


```

lshw -C network
  *-network
       description: Wireless interface
       product: AR5212 802.11abg NIC
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wifi0
       version: 01
       serial: 00:1c:26:8b:70:b9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=128.101.145.124 latency=0 module=ath_pci multicast=yes wireless=IEEE 802.11g

```


Last time I was running skype and had this problem, this is what turned up in the logs:

```
Dec  8 22:10:01 zeppelin /USR/SBIN/CRON[11514]: (daemon) CMD (test -x /usr/bin/debsecan && /usr/bin/debsecan --cron)
[B]Dec  8 22:10:26 zeppelin kernel: [46180.709056] wifi0: rx FIFO overrun; resetting
Dec  8 22:10:27 zeppelin kernel: [46181.476040] wifi0: rx FIFO overrun; resetting[/B]
Dec  8 22:10:39 zeppelin NetworkManager: <info>  (ath0): supplicant connection state change: 7 -> 0
Dec  8 22:10:39 zeppelin NetworkManager: <info>  (ath0): supplicant connection state change: 0 -> 2
Dec  8 22:10:54 zeppelin NetworkManager: <info>  (ath0): device state change: 8 -> 3
Dec  8 22:10:54 zeppelin NetworkManager: <info>  (ath0): deactivating device (reason: 11).
Dec  8 22:10:54 zeppelin NetworkManager: <info>  ath0: canceled DHCP transaction, dhcp client pid 11288
Dec  8 22:10:54 zeppelin NetworkManager: <WARN>  check_one_route(): (ath0) error -34 returned from rtnl_route_del(): Sucess
Dec  9 04:10:54 zeppelin avahi-daemon[6330]: Withdrawing address record for 192.168.0.100 on ath0.
Dec  9 04:10:54 zeppelin avahi-daemon[6330]: Leaving mDNS multicast group on interface ath0.IPv4 with address 192.168.0.100.
Dec  9 04:10:54 zeppelin avahi-daemon[6330]: Interface ath0.IPv4 no longer relevant for mDNS.
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Activation (ath0) starting connection 'Home'
Dec  8 22:10:54 zeppelin NetworkManager: <info>  (ath0): device state change: 3 -> 4
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) scheduled...
Dec  8 22:10:54 zeppelin NetworkManager: <info>  (ath0): supplicant connection state change: 2 -> 0
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) started...
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) scheduled...
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Activation (ath0) Stage 1 of 5 (Device Prepare) complete.
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Activation (ath0) Stage 2 of 5 (Device Configure) starting...
Dec  8 22:10:54 zeppelin NetworkManager: <info>  (ath0): device state change: 4 -> 5
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Unmanaged Device found; state CONNECTED forced. (see 
http://bugs.launchpad.net/bugs/191889)
Dec  8 22:10:54 zeppelin NetworkManager: <info>  Activation (ath0/wireless): connection 'Home' has security, and secrets exist.  No new 
secrets needed.

```


Do the things in bold are something concerning? A couple of times, when I was in the other room, I did see it complaining that it roamed out of the access point. 


```
iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

vmnet1    no wireless extensions.

vmnet8    no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11a  ESSID:"<SOMESSID>"  Nickname:""
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:0B:0E:94:D4:00   
          Bit Rate:54 Mb/s   Tx-Power:8 dBm   Sensitivity=1/1  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=42/70  Signal level=-47 dBm  Noise level=-89 dBm
          Rx invalid nwid:24709  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


```


Now typically when I am sitting next to the router my Link Quality is ~ 55-60 and in the other room varies between 30-50.

I have noticed that nearly 40 is my threshold, after which my network typically starts disconnecting every so often. 

```

ifconfig 
ath0      Link encap:Ethernet  HWaddr 00:1c:26:8b:70:b9  
          inet addr:XXXX  Bcast:XXXX  Mask:255.255.255.0
          inet6 addr: XXXX Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:4353 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1931 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1696921 (1.6 MB)  TX bytes:390875 (390.8 KB)

```

My hardware is a Thinkpad T61. I have been on Ubuntu for over an year now, but wifi has always been a slight concern. However with Intrepid things are getting worse for me :( (However I must say that earlier I had tough time on WPA2 Enterprise networks, which has now gone away) 


Any help/suggestions would be welcome.

---

### Post by ubuser_7 on 2008-12-13
A new error this time:

> Dec 13 12:40:49 zeppelin kernel: [ 9593.183174] rix 514 (0) bad ratekbps 0 mode 1

Any suggestions?

---

