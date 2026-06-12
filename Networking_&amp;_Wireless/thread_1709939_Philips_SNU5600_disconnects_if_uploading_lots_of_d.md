---
title: "Philips SNU5600 disconnects if uploading lots of data to NAS"
date: 2011-03-19
forum: Networking &amp; Wireless
---

### Post by richiethom on 2011-03-19
Hi

I have a Philips SNU5600 wifi dongle. My wifi network isn't particularly strong, but it has always been reliable, even when downloading and uploading large files such as ISOs to the internet.

I recently bought a NAS, and when I run rsync or try and copy a large file (eg 6 gigs) to the NAS, the connection will eventually fail.

The error message in /var/log/debug is:
```
No probe response from AP 00:0d:54:9e:71:b8 after 500ms, disconnecting.
```

I have read elsewhere that this is a problem with the Minstrel algorithm, so I have tried disabling that by creating /etc/modprobe.d/80211.conf with the following line in it:

```
options mac80211 ieee80211_default_rc_algo=pid
```

And when I reboot, I am able to run "cat /sys/module/mac80211/parameters/ieee80211_default_rc_algo" and the output is "pid".

However, in my /var/log/debug, there is still the line:

```
phy0: Selected rate control algorithm 'minstrel'
```

Here is the output from a few other commands for extra information:

```

rich@rich-pc:~$ lsusb | grep Philips
Bus 001 Device 002: ID 0471:1236 Philips (or NXP) SNU5600 802.11bg

```

```

rich@rich-pc:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:06:4f:81:23:81  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0x1100 

eth1      Link encap:Ethernet  HWaddr 00:0f:fe:e5:7d:f4  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 Memory:f3000000-f3020000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:429 errors:0 dropped:0 overruns:0 frame:0
          TX packets:429 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:73477 (73.4 KB)  TX bytes:73477 (73.4 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1d:19:4a:1e:0f  
          inet addr:192.168.0.174  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21d:19ff:fe4a:1e0f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:5330 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5592 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:3572270 (3.5 MB)  TX bytes:1214221 (1.2 MB)

```

```

rich@rich-pc:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"3Com"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:0D:54:9E:71:B8   
          Bit Rate=54 Mb/s   Tx-Power=27 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=35/100  Signal level=35/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

```

rich@rich-pc:~$ lsmod | grep -i zd1211rw
zd1211rw               49928  0 
mac80211              267099  3 zd1211rw,ath9k_htc,ath9k_common
cfg80211              170485  5 zd1211rw,ath9k_htc,ath9k_common,mac80211,ath

```

```

rich@rich-pc:~$ sudo lshw -C network
[sudo] password for rich: 
  *-network               
       description: Ethernet interface
       product: 82566DM-2 Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth1
       version: 02
       serial: 00:0f:fe:e5:7d:f4
       capacity: 1GB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=1.0.2-k4 firmware=1.3-1 latency=0 link=no multicast=yes port=twisted pair
       resources: irq:43 memory:f3000000-f301ffff memory:f3025000-f3025fff ioport:3100(size=32)
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 9
       bus info: pci@0000:07:09.0
       logical name: eth0
       version: 10
       serial: 00:06:4f:81:23:81
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:21 ioport:1100(size=256) memory:f3100000-f31000ff
  *-network:0
       description: Wireless interface
       physical id: 1
       bus info: usb@1:3
       logical name: wlan0
       serial: 00:1d:19:4a:1e:0f
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=zd1211rw driverversion=2.6.35-27-generic firmware=N/A ip=192.168.0.174 link=yes multicast=yes wireless=IEEE 802.11bg
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

```

```

rich@rich-pc:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:0D:54:9E:71:B8
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=35/100  Signal level=35/100  
                    Encryption key:on
                    ESSID:"3Com"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=0000001bd6b0d820
                    Extra: Last beacon: 24000ms ago
                    IE: Unknown: 000433436F6D
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010B
                    IE: Unknown: 2A0100
                    IE: Unknown: 32080C1218243048606C
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK

vboxnet0  Interface doesn't support scanning.

```

```

rich@rich-pc:~$ lsb_release -d
Description:	Ubuntu 10.10

```

```

rich@rich-pc:~$ uname -rm
2.6.35-27-generic x86_64

```

A few other bits and pieces:

 - the problem has only been around since I got the NAS, and only happens when copying files TO the NAS. Downloading/uploading to internet doesn't cause the same problem
 - this problem happens on two machines both with the same wifi dongle
 - this problem doesn't happen on a laptop running the Intel iwl3945 driver, nor with machines connected via cables, so it is not the NAS which is at fault

I think I've included everything.

Any ideas how to get a stable connection when backing up?

Thanks in advance

Rich

---

### Post by richiethom on 2011-03-26
Bounce :)

A bit more information - running the latest Natty daily on another machine with the same dongle plugged in causes exactly the same problem. This machine is a laptop and its internal driver gets on absolutely fine.

---

