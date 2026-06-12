---
title: "Unstable Wireless Connection in Atheros Communications Inc. AR2413 802.11bg NIC (rev"
date: 2010-07-06
forum: Networking &amp; Wireless
---

### Post by lordamit on 2010-07-06
Hi.
When I installed Ubuntu wubi 10.04 inside windows, I was very happy. the internet was fast. very fast.
Anyway, later I decided to format my windows and Ubuntu both and I installed Windows, and Ubuntu at a seperate partition(outside windows)


now i am horrified to realize that the internet is very very slow. I face trouble connecting in the first place right after booting inside Ubuntu. When I connect, it disconnects after  a while. I tried,

sudo rmmod -f ath5k
sudo modprobe ath5k nohwcrypt=1

  And it stopped disconnecting, but only to give me a connection with almost no speed.
here is the ping statistics after i tried pinging google.com

64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=954 ttl=50 time=296 ms
64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=955 ttl=50 time=227 ms
64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=956 ttl=50 time=208 ms
64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=957 ttl=50 time=581 ms
64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=958 ttl=50 time=238 ms
64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=959 ttl=50 time=635 ms
64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=960 ttl=50 time=239 ms
^C64 bytes from ew-in-f147.1e100.net (74.125.77.147): icmp_seq=961 ttl=50 time=734 ms

--- google.com ping statistics ---
961 packets transmitted, 615 received, +1 errors, 36% packet loss, time 1641621ms
rtt min/avg/max/mdev = 207.155/2882.221/34558.801/5370.422 ms, pipe 12

I tried downloading something, and it seems it is around 0Bytes at most of the time, and suddenly increases to give me around 50KBps, and then it is back to 0Bytes again.

I tried selecting best server, and I was given a no internet connection found error :( this is driving me crazy. I have gone through many pages, but I am totally confused.

Anyway, here are the details:

Desktop PC
[B]
Wireless Brand, Model and Wireless Chipset:

[/B]04:05.0 Ethernet controller: Atheros Communications Inc. AR2413 802.11bg NIC (rev 01)

**check interface:**
iwconfig wlan0 gives:
```

wlan0     IEEE 802.11bg  ESSID:"swordfish" 
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:1F:33:BB:54:FE  
          Bit Rate=54 Mb/s   Tx-Power=20 dBm  
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/70  Signal level=-50 dBm 
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
```ifconfig wlan0 gives:

```
wlan0     Link encap:Ethernet  HWaddr 00:21:27:f0:ba:62 
          inet addr:192.168.3.81  Bcast:192.168.3.255  Mask:255.255.255.0
          inet6 addr: fe80::221:27ff:fef0:ba62/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27939 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32443 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:27578599 (27.5 MB)  TX bytes:4549203 (4.5 MB)

```**Check for modules:**

lsmod | grep "ath" gives:
```

ath5k                 121792  0
mac80211              204922  1 ath5k
ath                     7611  1 ath5k
cfg80211              126485  4 ath5k,rndis_wlan,mac80211,ath
led_class               2864  1 ath5k
```[B]Kernel boot messages: 
[/B]it gives a loooong output:
```
[   11.112937] ath5k 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   11.112964] ath5k 0000:04:05.0: registered as 'phy0'
[   11.715226] ath5k phy0: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
```lots of lots of noise floor calibration failed....

```
[ 1249.214671] ath5k 0000:04:05.0: PCI INT A disabled
[ 1251.993815] ath5k 0000:04:05.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[ 1251.993853] ath5k 0000:04:05.0: registered as 'phy2'
[ 1252.598022] ath5k phy2: Atheros AR2413 chip found (MAC: 0x78, PHY: 0x45)
[ 1259.694064] ath5k phy2: noise floor calibration failed (2437MHz)
[ 1266.239400] ath5k phy2: noise floor calibration failed (2437MHz)
[ 1275.227845] ath5k phy2: noise floor calibration failed (2437MHz)
[ 1314.881025] ath5k phy2: noise floor calibration failed (2432MHz)
[ 1315.365757] ath5k phy2: noise floor calibration failed (2437MHz)
[ 1455.257557] ath5k phy2: noise floor calibration failed (2437MHz)
[ 1555.250022] ath5k phy2: noise floor calibration failed (2437MHz)
[ 1627.244576] ath5k phy2: no further txbuf available, dropping packet
```lots of lots of noise floor calibration failed....
[B]
Network configuration[/B]:
sudo lshw -C network gives: 

    ```
  
*-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 01
       serial: 00:1c:c0:a7:90:4a
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:27 ioport:d000(size=256) memory:fea20000-fea20fff memory:fea00000-fea1ffff(prefetchable)


*-network
       description: Wireless interface
       product: AR2413 802.11bg NIC
       vendor: Atheros Communications Inc.
       physical id: 5
       bus info: pci@0000:04:05.0
       logical name: wlan0
       version: 01
       serial: 00:21:27:f0:ba:62
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k ip=192.168.3.81 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
       resources: irq:20 memory:fe900000-fe90ffff
```[B]Scan for networks:
[/B]iwlist wlan0 scan gives:```
wlan0     Scan completed :
          Cell 01 - Address: 00:1F:33:BB:54:FE
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=58/70  Signal level=-52 dBm  
                    Encryption key:off
                    ESSID:"swordfish"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 48 Mb/s
                    Mode:Master
                    Extra:tsf=000000015a59d618
                    Extra: Last beacon: 37516ms ago
                    IE: Unknown: 000973776F726466697368
                    IE: Unknown: 010882848B962430486C
                    IE: Unknown: 030101
                    IE: Unknown: 2A0100
                    IE: Unknown: 2F0100
                    IE: Unknown: 32040C121860
                    IE: Unknown: DD09001018020010000000
                    IE: Unknown: DD180050F2020101800003A4000027A4000042435E0062322F00
```[B]

Ubuntu version: Ubuntu 10.04 LTS

Kernel Version:2.6.32-21-generic i686

restarting the network:

 sudo /etc/init.d/networking restart gives: 
[/B]```
 * Reconfiguring network interfaces...                                                                     
   Ignoring unknown interface wlan0=wlan0.

```Someone please help me :(i am tired of this problem :(I can barely even browse now.  I don't want to use windows just because it doesn't create problem in maintaining the wireless connection :(

---

### Post by ryebread1974 on 2010-12-26
Did you ever get this resolved?  I am having the exact same problem with the same hardware.  I am running 10.10

---

