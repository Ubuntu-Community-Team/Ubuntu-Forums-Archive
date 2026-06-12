---
title: "Wireless problem"
date: 2010-05-15
forum: Networking &amp; Wireless
---

### Post by loki993 on 2010-05-15
Ok I have this narrowed down, but I still cant figure out how to fix it. What happens is my wireless signal fluctuates quite a bit. Im my bedroom its around 30-45%. 40 seems to be arunf the magic number, if it drops below that I take a significant speed hit, down from 5mbps to 1. What happenbd is the latency goe up. good latency is around 152 and that will yelt 5mbps speeds, but then it will go to around 169 and then I cant get over 1.2. 

any idea on how I can fix this its really annoying.

---

### Post by Crafty Kisses on 2010-05-15
Hey there,

Do you think you can provide me some more information? Can you give me the results of the following commands?

```
lspci
lsusb
lshw -C network
```

---

### Post by loki993 on 2010-05-15
Sure

lspci

00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
00:1f.5 IDE interface: Intel Corporation ICH9M/M-E 2 port SATA IDE Controller (rev 03)
00:1f.6 Signal processing controller: Intel Corporation 82801I (ICH9 Family) Thermal Subsystem (rev 03)
04:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

lsusb

Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 002: ID 046d:c51b Logitech, Inc. V220 Cordless Optical Mouse for Notebooks
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 064e:a103 Suyin Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

lshw -C network

*-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wifi0
       version: 01
       serial: 00:23:4d:4f:0c:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.125 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:56600000-5660ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:c8:dc:7d
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:2000(size=256) memory:52410000-52410fff(prefetchable) memory:52400000-5240ffff(prefetchable) memory:52420000-5242ffff(prefetchable)


There it is. Does it matter where I'm at when I do this because right now I'm in the living room and my connections fine here, its only in my bedroom it gets bad.

---

### Post by loki993 on 2010-05-16
Hmm no one wants to take a stab at this?

---

### Post by NUboon2Age on 2010-05-16
Some more helpful info requsted: [HOWTO post a Wireless issue (ticket).]("http://ubuntuforums.org/showthread.php?p=6183681")

---

### Post by NUboon2Age on 2010-05-16
I see looking at the bug database there are some possibly related [speed issues with Atheros controllers]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=atheros%2Cspeed&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=").

---

### Post by Zorael on 2010-05-17
As a small sidenote, the terminal program **wavemon** is pretty handy if you want to get detailed real-time information about your signal strength and quality.

If you have a laptop, you could start the program and then walk around carrying it, to identify radio shadows.

---

### Post by loki993 on 2010-05-17
> **NUboon2Age said:**
> Some more helpful info requsted: [HOWTO post a Wireless issue (ticket).]("http://ubuntuforums.org/showthread.php?p=6183681")

I didnt see that, Ill get the rest of the info in here.

> **NUboon2Age said:**
> I see looking at the bug database there are some possibly related [speed issues with Atheros controllers]("https://bugs.launchpad.net/bugs/+bugs?field.searchtext=atheros%2Cspeed&orderby=-importance&search=Search&field.status%3Alist=NEW&field.status%3Alist=INCOMPLETE_WITH_RESPONSE&field.status%3Alist=INCOMPLETE_WITHOUT_RESPONSE&field.status%3Alist=CONFIRMED&field.status%3Alist=TRIAGED&field.status%3Alist=INPROGRESS&field.status%3Alist=FIXCOMMITTED&field.assignee=&field.bug_reporter=&field.omit_dupes=on&field.has_patch=&field.has_no_package=").

Ill take a look at those. 

> **Zorael said:**
> As a small sidenote, the terminal program **wavemon** is pretty handy if you want to get detailed real-time information about your signal strength and quality.

If you have a laptop, you could start the program and then walk around carrying it, to identify radio shadows.

Il give that a try too

---

### Post by loki993 on 2010-05-18
ifconfig

ath0      Link encap:Ethernet  HWaddr 00:23:4d:4f:0c:de  
          inet addr:192.168.1.125  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:4dff:fe4f:cde/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1106 errors:0 dropped:0 overruns:0 frame:0
          TX packets:571 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1198018 (1.1 MB)  TX bytes:99455 (99.4 KB)

eth0      Link encap:Ethernet  HWaddr 00:1e:ec:c8:dc:7d  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:80 errors:0 dropped:0 overruns:0 frame:0
          TX packets:80 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4760 (4.7 KB)  TX bytes:4760 (4.7 KB)

wifi0     Link encap:UNSPEC  HWaddr 00-23-4D-4F-0C-DE-30-30-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2818 errors:0 dropped:0 overruns:0 frame:14
          TX packets:838 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:280 
          RX bytes:933224 (933.2 KB)  TX bytes:136394 (136.3 KB)
          Interrupt:17 

iwconfig
lo        no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11g  ESSID:"dd-wrt"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:1A:70:FD:A0:89   
          Bit Rate:48 Mb/s   Tx-Power:16 dBm   Sensitivity=1/1  
          Retry: off   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality=60/70  Signal level=-36 dBm  Noise level=-96 dBm
          Rx invalid nwid:232  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

lsmod
ath_rate_sample        11476  1 
ath_pci               193197  0 
wlan                  222892  5 wlan_ccmp,wlan_scan_sta,ath_rate_sample,ath_pci
ath_hal               398604  3 ath_rate_sample,ath_pci

sudo lshw -C network

[sudo] password for ryan: 
  *-network               
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: wifi0
       version: 01
       serial: 00:23:4d:4f:0c:de
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath_pci ip=192.168.1.125 latency=0 multicast=yes wireless=IEEE 802.11g
       resources: irq:17 memory:56600000-5660ffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:ec:c8:dc:7d
       size: 10MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 link=no multicast=yes port=MII speed=10MB/s
       resources: irq:28 ioport:2000(size=256) memory:52410000-52410fff(prefetchable) memory:52400000-5240ffff(prefetchable) memory:52420000-5242ffff(prefetchable)

iwlist scan
lo        Interface doesn't support scanning.

wifi0     Interface doesn't support scanning.

ath0      Scan completed :
          Cell 01 - Address: 00:1A:70:FD:A0:89
                    ESSID:"dd-wrt"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=67/70  Signal level=-28 dBm  Noise level=-95 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00
          Cell 02 - Address: 00:1A:70:FD:A0:89
                    ESSID:"\x00\x00\x00\x00\x00\x00"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=68/70  Signal level=-27 dBm  Noise level=-95 dBm
                    Encryption key: on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    IE: IEEE 802.11i/WPA2 Version 1
                        Group Cipher : CCMP
                        Pairwise Ciphers (1) : CCMP
                        Authentication Suites (1) : PSK
                    Extra:wme_ie=dd180050f2020101800003a4000027a4000042435e0062322f00
          Cell 03 - Address: 02:26:A3: DD:0E: DB
                    ESSID:"print server 196222"
                    Mode:Ad-Hoc
                    Frequency:2.462 GHz (Channel 11)
                    Quality=39/70  Signal level=-56 dBm  Noise level=-95 dBm
                    Encryption key: off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100

eth0      Interface doesn't support scanning.

 lsb_release -d
Description:    Ubuntu 10.04 LTS

name -mr
2.6.32-22-generic i686

Heres what I could get.

---

### Post by JohnDoe365 on 2010-05-19
Take a look at:
[http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

Does it help to stop WiFi and re-assiciate? Based on the problems 10.04 has in regard to WiFi I assume it is not hardware driver related but probably a kernel issue ...

---

### Post by loki993 on 2010-05-19
> **JohnDoe365 said:**
> Take a look at:
[http://ubuntuforums.org/showthread.php?t=1487039](http://ubuntuforums.org/showthread.php?t=1487039)

Does it help to stop WiFi and re-assiciate? Based on the problems 10.04 has in regard to WiFi I assume it is not hardware driver related but probably a kernel issue ...

Not really, yeah I can disconnect and reconnect and I may get a good speedtest, but then the next one will be bad. 

Also I had the same problem with 9.10 so its a 10.04 issue that I know of. 

It has to do with how the driver deals with signal strength. I can literally walk out the door from my bedroom and the signal will hit full speed again. 

I checked in windows and it get the same signal strength, but I get good speed with that.

---

### Post by JohnDoe365 on 2010-05-19
By no means did I claim this to be permanent hack, I try to narrow down the problem. If you perform a search dozens people describe the same problem: Awful slow WiFi speed and after a reconnect speed is better but soon drops to unaceptable.

I would guess this is a WiFi issue / kernel isssue and not related to one specific hardware.

I have not seen any official hack / blog post / bug report, but you may consider supporting [https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936](https://bugs.launchpad.net/ubuntu/+source/bcmwl/+bug/581936) to raise awareness.

And as manually deactivating signal strength sensing does not help I am also pretty sure it is not directly realted to signal strenght, but you may try

 **sudo iwconfig ath0 rate 54M**

---

