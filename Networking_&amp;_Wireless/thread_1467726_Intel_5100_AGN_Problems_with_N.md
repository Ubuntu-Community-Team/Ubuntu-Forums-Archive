---
title: "Intel 5100 A/G/N Problems with N"
date: 2010-05-01
forum: Networking &amp; Wireless
---

### Post by Ayukawa on 2010-05-01
Connected to two Wireless-G routers just fine, now connecting to my Wireless-N router, my connection is EXTREMELY slow and unreliable.  Pages I load via browser often take several seconds to resolve and connect (if they connect at all) and updates via apt seem to only give me about 30kb/s or lower.

I was establishing much faster connections w/ the same configuration with other (non-N) wireless routers.

  

Laptop is an ASUS G50vt-X5

lspci:
03:00.0 Network controller [0280]: Intel Corporation Wireless WiFi Link 5100 [8086:4232]

ifconfig:
wlan0     Link encap:Ethernet  HWaddr 00:21:5d:59:00:e6  
          inet addr:192.168.1.198  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::221:5dff:fe59:e6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:20270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:13665 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:21354920 (21.3 MB)  TX bytes:2223157 (2.2 MB)

iwconfig:
wlan0     IEEE 802.11abgn  ESSID:"Ellenzar"  
          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:21:91:F7:09:37   
          Bit Rate=0 kb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=66/70  Signal level=-44 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

lsmod | grep iwlagn:
iwlagn                105566  0 
iwlcore               105922  1 iwlagn
mac80211              204922  2 iwlagn,iwlcore
cfg80211              126485  3 iwlagn,iwlcore,mac80211

sudo lshw -C network
  *-network               
       description: Wireless interface
       product: Wireless WiFi Link 5100
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:5d:59:00:e6
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn ip=192.168.1.198 latency=0 multicast=yes wireless=IEEE 802.11abgn
       resources: irq:31 memory:fdffe000-fdffffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 00:23:54:ef:d8:b7
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:30 ioport:e800(size=256) memory:f8fff000-f8ffffff(prefetchable) memory:f8fe0000-f8feffff(prefetchable) memory:feaf0000-feafffff(prefetchable)

iwlist scan:
wlan0     Scan completed :
          Cell 01 - Address: 00:21:91:F7:09:37
                    Channel:10
                    Frequency:2.457 GHz (Channel 10)
                    Quality=70/70  Signal level=-38 dBm  
                    Encryption key:on
                    ESSID:"Ellenzar"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Bit Rates:6 Mb/s; 9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s
                              36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master
                    Extra:tsf=00000016ac53bb34
                    Extra: Last beacon: 98216ms ago
                    IE: Unknown: 0008456C6C656E7A6172
                    IE: Unknown: 010482848B96
                    IE: Unknown: 03010A
                    IE: Unknown: 2A0100
                    IE: Unknown: 32088C129824B048606C
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (2) : TKIP CCMP
                        Authentication Suites (1) : PSK
                    IE: Unknown: DD180050F2020101000003A4000027A4000042435E0062322F00
                    IE: Unknown: 2D1A4E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: 3D160A071B0000000F000000000000000000000000000000
                    IE: Unknown: DD1E00904C336E101BFFFF000000000000000000000000000000000000000000
                    IE: Unknown: DD1A00904C340A07030000000F000000000000000000000000000000

lsb_release -d:
Description:	Ubuntu 10.04 LTS

uname -mr:
2.6.32-21-generic i686

sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                                                                                                                  Ignoring unknown interface wlan0=wlan0.

---

### Post by rockyjones on 2010-05-01
If you look in the system error log you are probably getting IWLAGN Micrcode SW Errors.This has been going on for a long time and make wireless N useless for the 5000 series intel cards on some machines.  I have a 5300 and have to run wireless G only or I have no connectivity.  Many reports for this over the months (maybe years now) but it never gets fixed.

---

### Post by seenthelite on 2010-05-01
I do not have a solution for you but it is possible to use 10.04 and Intel 5100 A/G/N on N wireless as I do. I have been using Intel 5100 A/G/N on 5 GHz N with 9.10 and 10.04. I have not had to do any tweaking it just works.

---

### Post by rockyjones on 2010-05-01
Yes, as I said, "on some machines" it won't work; some machines seem to work fine.  It appears to be something associated with wpa2 encryption because turning encryption off results in the wireless working fine at "N" speeds.  Not too many people want to run with no encryption however.  Connecting to encrypted wireless G seems to work fine but you obviously take a big speed hit.

If you search the web, you'll see the problem has been going on for a while and seems to affect 3945 and 5000 series Intel wireless cards.  These same cards/machines work fine under Windows.

---

### Post by Ayukawa on 2010-05-01
If I forced WPA rather than allowing WPA/WPA2, would that resolve the problem?  I set my router to only do 802.11g and it does seem to work a lot better.  I still notice some slowness at times, but that could just be my imagination.

I'd rather not leave my router set to force 802.11g, because I have other devices (and operating systems) that are capable of using N.

---

### Post by rockyjones on 2010-05-01
I don't think forcing N will solve the problem.  WEP may work but I didn't try it.  What I did to work around the problem for a while was to turn off router security and just limit the machines that can connect through DHCP and MAC specific addresses.  I had four machines that connected to the router so I set DHCP to only allow four addresses and then made DHCP reservations for each of the four machines MAC addresses.  This works and gives some security but is less secure than WPA2.  I don't live in an apartment/condo environment so don't have anyone really close that would have much of a chance to get into my network anyway unless they parked in front of the house or driveway!

I finally gave up on Linux for my laptops.  I was just spending too much time trying to overcome the various problems that would be fixed then pop up again with a new update.  I still run it on two desktops (HTPC and media server) but I have more control over the hardware for these machines and simply pick hardware that works best for Ubuntu/Mint.

---

