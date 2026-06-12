---
title: "Wireless problem - no IP address"
date: 2006-07-06
forum: Networking &amp; Wireless
---

### Post by chris_m on 2006-07-06
Hi,

I've been using the previous version of Ubuntu on my Toughbook CF-72 with a Cisco 340 PCMCIA wireless card for months. I even downloaded the Dapper Drake update by wireless!

Since then I've had no working wireless and can only connect by eth0 by direct cable to the D-Link DSL-604+ wireless router. The hardware works because I can connect via Windows.
The wireless seems to work but there's no IP address when I try to connect through System/Administration/Networking.

I would welcome any advice as it's driving me mad being tied to a desk!

**iwconfig gives:**


lo        no wireless extensions.

eth0      no wireless extensions.

eth2      IEEE 802.11-DS  ESSID:"CCRS_01204387770"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0D:88:E2:B8:78
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=93/100  Signal level=-49 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:17   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"CCRS_01204387770"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:0D:88:E2:B8:78
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=93/100  Signal level=-49 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:3  Invalid misc:17   Missed beacon:0

sit0      no wireless extensions.

[B]
ifconfig gives:[/B]

eth0      Link encap:Ethernet  HWaddr 00:D0:59:68:03:91
          inet addr:192.168.0.7  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2d0:59ff:fe68:391/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:386 errors:0 dropped:0 overruns:0 frame:0
          TX packets:322 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:390840 (381.6 KiB)  TX bytes:35385 (34.5 KiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16284 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16284 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:5547992 (5.2 MiB)  TX bytes:5547992 (5.2 MiB)

wifi0     Link encap:UNSPEC  HWaddr 00-40-96-43-C1-2C-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:58 errors:6 dropped:0 overruns:0 frame:6
          TX packets:0 errors:3 dropped:0 overruns:0 carrier:0
          collisions:94 txqueuelen:100
          RX bytes:19960 (19.4 KiB)  TX bytes:954 (954.0 b)
          Interrupt:3 Base address:0x100

[B]
iwlist scan gives:[/B]

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth2      Scan completed :
          Cell 01 - Address: 00:0D:88:E2:B8:78
                    ESSID:"CCRS_01204387770"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=84/100  Signal level=-53 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

wifi0     Scan completed :
          Cell 01 - Address: 00:0D:88:E2:B8:78
                    ESSID:"CCRS_01204387770"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=84/100  Signal level=-53 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s

sit0      Interface doesn't support scanning.


**lsmod gives:**

airo_cs                 7940  1
airo                   72352  1 airo_cs
tsdev                   8000  0
pcc_acpi               12416  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcmcia                 40508  1 airo_cs

---

### Post by ubercat on 2006-07-06
From cursory research, this appears to be a kernel/backporting issue. There are bug reports galore popping up on the net re dropping connections, failed connections, and basically wireless setups FUBAR in all corners and with various distros.

I've given up trying to get wifi to work with Dapper. One laptop works but drops the connection constantly, the other (xubuntu) won't load the atmel_cs module for the card to have a chance. Breezy ID'd the card on install, as well as let me setup WEP,  but after an upgrade the dropping connection problem started on that system as well. I don't think Linux is WiFi prime time yet. Soon, perhaps -- I hope!

Cisco's Aironet 350 card and FreeBDS are looking good about now!

---

### Post by chris_m on 2006-07-06
Hi ubercat,

I would agree with you apart from the fact that wi-fi setups seemed to be reliable on the previous versions of Ubuntu (or maybe it worked OK for me). This latest version does appears to come with a lot of problems for wireless users!

---

### Post by chris_m on 2006-07-09
I'm out of ideas on this problem. 

Does anyone know if anybody is working on a fix to Dapper Drake so that everyone gets their wireless working again?

Is there anyway to go back to the earlier version of Ubuntu?

---

