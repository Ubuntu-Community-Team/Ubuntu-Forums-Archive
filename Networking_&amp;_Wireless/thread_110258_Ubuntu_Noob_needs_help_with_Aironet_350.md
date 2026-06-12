---
title: "Ubuntu Noob needs help with Aironet 350"
date: 2005-12-30
forum: Networking &amp; Wireless
---

### Post by Danno74 on 2005-12-30
Hi, I'm new to the world of Linux but seemed to have developed a problem. My Cisco Aironet 350 card has stopped recieving dhcp requests from my internet provider when I boot to Ubuntu. I've followed the wireless guide to the best of my abilities and determined that this is the case.
This problem only manifested itself after the initial boot and subsequent upgrade of the kernel. I recorded my findings from the terminal and will report them shortly (I left them on the Ubuntu partition).
I'm pretty good at cracking Win98, but sick and tired of dealing with an OS thats close to being a decade old. It might help to translate things into M$ lingo. I've surfed most of the threads on the subject and have thoughly confused myself.

Setup info:
Ubuntu 5.10/Win98se Dual boot
HP Pavillion P3 800mhz
What else ya need to know?

---

### Post by Danno74 on 2005-12-30
Ok, here is my info, sorry the list is so long. I edited out some information, and all my goofs.

        [PHP]   *-network
             description: Wireless interface
             product: PC4800
             vendor: AIRONET Wireless Communications
             physical id: a
             bus info: pci@00:0a.0
             logical name: eth0
             version: 01
             serial: 00:0a:8a:fa:73:b5
             width: 32 bits
             clock: 33MHz
             capabilities: ethernet physical wireless
             configuration: broadcast=yes driver=airo multicast=yes wireless=IEE E 802.11-DS
             resources: iomemory:df800000-df80007f ioport:d000-d07f ioport:b800- b83f irq:5
        *-communication UNCLAIMED
             description: Communication controller
             product: HCF 56k Data/Fax/Voice/Spkp (w/Handset) Modem
             vendor: Conexant
             physical id: b
             bus info: pci@00:0b.0
             version: 08
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             resources: iomemory:df000000-df00ffff ioport:b400-b407 irq:10
        
dan@Pavillion:~$ sudo lshw -businfo
Bus info      Device    Class          Description
==================================================
                   
pci@00:0a.0   eth0      network        PC4800

dan@Pavillion:~$ sudo lshw -C network
  *-network
       description: Wireless interface
       product: PC4800
       vendor: AIRONET Wireless Communications
       physical id: a
       bus info: pci@00:0a.0
       logical name: eth0
       version: 01
       serial: 00:0a:8a:fa:73:b5
       width: 32 bits
       clock: 33MHz
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=airo multicast=yes wireless=IEEE 802.11-DS
       resources: iomemory:df800000-df80007f ioport:d000-d07f ioport:b800-b83f irq:5
dan@Pavillion:~$ sudo lspci -v
0000:00:0a.0 Network controller: AIRONET Wireless Communications PC4800 (rev 01)
        Flags: medium devsel, IRQ 5
        Memory at df800000 (32-bit, non-prefetchable) [size=128]
        I/O ports at d000 [size=128]
        I/O ports at b800 [size=64]

dan@Pavillion:~$ sudo lspci -n
0000:00:00.0 0600: 1106:0691 (rev 42)
0000:00:01.0 0604: 1106:8598
0000:00:07.0 0601: 1106:0596 (rev 12)
0000:00:07.1 0101: 1106:0571 (rev 06)
0000:00:07.2 0c03: 1106:3038 (rev 08)
0000:00:07.3 0600: 1106:3050 (rev 20)
0000:00:0a.0 0280: 14b9:0350 (rev 01)
0000:00:0b.0 0780: 14f1:1035 (rev 08)
0000:00:0c.0 0401: 1274:1371 (rev 06)
0000:01:00.0 0300: 10de:0028 (rev 15)

dan@Pavillion:~$ sudo lsmod | grep airo
airo                   63776  0

dan@Pavillion:~$ sudo iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11-DS  ESSID:"PI"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:10:E7:F5:E7:47
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/100  Signal level=-62 dBm  Noise level=-96 dBm
          Rx invalid nwid:5280  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9249   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"PI"
          Mode:Managed  Frequency:2.442 GHz  Access Point: 00:10:E7:F5:E7:47
          Bit Rate:11 Mb/s   Tx-Power=20 dBm   Sensitivity=0/65535
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=68/100  Signal level=-62 dBm  Noise level=-96 dBm
          Rx invalid nwid:5280  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:9249   Missed beacon:0

sit0      no wireless extensions.
dan@Pavillion:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:0A:8A:FA:73:B5
          inet6 addr: fe80::20a:8aff:fefa:73b5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27266 errors:2860 dropped:0 overruns:0 frame:2860
          TX packets:22 errors:3 dropped:0 overruns:0 carrier:3
          collisions:2 txqueuelen:1000
          RX bytes:1732221 (1.6 MiB)  TX bytes:6882 (6.7 KiB)
          Interrupt:5 Base address:0xb800
lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:7177 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7177 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:556926 (543.8 KiB)  TX bytes:556926 (543.8 KiB)
wifi0     Link encap:UNSPEC  HWaddr 00-0A-8A-FA-73-B5-00-00-00-00-00-00-00-00-00-00
          UP BROADCAST RUNNING MULTICAST  MTU:2312  Metric:1
          RX packets:27266 errors:2860 dropped:0 overruns:0 frame:2860
          TX packets:22 errors:3 dropped:0 overruns:0 carrier:3
          collisions:2 txqueuelen:100
          RX bytes:1732221 (1.6 MiB)  TX bytes:6882 (6.7 KiB)
          Interrupt:5 Base address:0xb800
dan@Pavillion:~$ sudo dhclient eth0
Internet Systems Consortium DHCP Client V3.0.2
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)
sit0: unknown hardware address type 776
wifi0: unknown hardware address type 801
sit0: unknown hardware address type 776
wifi0: unknown hardware address type 801
Listening on LPF/eth0/00:0a:8a:fa:73:b5
Sending on   LPF/eth0/00:0a:8a:fa:73:b5
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.[/PHP]

---

