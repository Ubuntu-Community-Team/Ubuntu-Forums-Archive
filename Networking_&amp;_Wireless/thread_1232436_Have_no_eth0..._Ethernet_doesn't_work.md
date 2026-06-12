---
title: "Have no eth0... Ethernet doesn't work"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by brandondiederich on 2009-08-05
I have an Acer Aspire One that I installed the netbook distro of 9.04. The wireless network works but the ethernet does not.

root@alice:/home/brandon# lshw -C Network
  *-network               
       description: Wireless interface
       product: AR242x 802.11abg Wireless PCI Express Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wmaster0
       version: 01
       serial: 00:24:2c:18:4d:61
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless
       configuration: broadcast=yes driver=ath5k_pci ip=192.168.1.4 latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg
  *-network UNCLAIMED
       description: Ethernet controller
       product: Attansic Technology Corp.
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: c0
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list
       configuration: latency=0
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 2e:7f:69:d8:40:4a
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

The second to last is the Ethernet controller and it is listed as Unclaimed... I know the pci address I just don't know how to claim it... Any suggestions would be appreciated.

---

### Post by Friendless on 2009-09-03
I am aware of someone in the same situation, I am curious if you found a solution or if you could post the dmesg output that may display information on the wireless.

---

### Post by r.osmanov on 2009-09-03
Driver for the controller is missing. At least UNCLAIMED message informs just about that state.
What exactly your network card is? Likely you have to install special driver.
Please paste here what the command
```
sudo lspci -vk
```
shows.

By the way, actually it needn't necessarily be eth0. I have eth1 configured to Ethernet controller in office.

---

### Post by brandondiederich on 2009-09-20
brandon@alice:~$ sudo lspci -vk
[sudo] password for brandon: 
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 56280000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 50c0 [size=8]
    Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Memory at 56300000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: [90] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [d0] Power Management version 2
    Kernel modules: intelfb

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0
    Memory at 56200000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: [d0] Power Management version 2

00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 56340000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: [50] Power Management version 2
    Capabilities: [60] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [70] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [130] Root Complex Link <?>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 55100000-561fffff
    Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 022f
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: 54100000-550fffff
    Prefetchable memory behind bridge: 0000000051000000-0000000051ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 022f
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00001000-00002fff
    Memory behind bridge: 53000000-540fffff
    Prefetchable memory behind bridge: 0000000052000000-0000000052ffffff
    Capabilities: [40] Express Root Port (Slot+), MSI 00
    Capabilities: [80] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable+
    Capabilities: [90] Subsystem: Acer Incorporated [ALI] Device 022f
    Capabilities: [a0] Power Management version 2
    Capabilities: [100] Virtual Channel <?>
    Capabilities: [180] Root Complex Link <?>
    Kernel driver in use: pcieport-driver
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 5080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 5060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #3 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 5040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 5020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 56344400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: [50] Power Management version 2
    Capabilities: [58] Debug port: BAR=1 offset=00a0
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
    Capabilities: [50] Subsystem: Acer Incorporated [ALI] Device 022f

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, medium devsel, latency 0
    Capabilities: [e0] Vendor Specific Information <?>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 50a0 [size=16]
    Capabilities: [70] Power Management version 2
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: medium devsel, IRQ 11
    I/O ports at 5000 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e00d
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 55100000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [40] Power Management version 2
    Capabilities: [50] Message Signalled Interrupts: Mask- 64bit- Queue=0/0 Enable-
    Capabilities: [60] Express Legacy Endpoint, MSI 00
    Capabilities: [90] MSI-X: Enable- Mask- TabSize=1
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [140] Virtual Channel <?>
    Kernel driver in use: ath5k_pci
    Kernel modules: ath_pci, ath5k

03:00.0 Ethernet controller: Attansic Technology Corp. Device 1062 (rev c0)
    Subsystem: Acer Incorporated [ALI] Device 022f
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 53000000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 1000 [size=128]
    Capabilities: [40] Power Management version 3
    Capabilities: [48] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
    Capabilities: [58] Express Endpoint, MSI 00
    Capabilities: [6c] Vital Product Data <?>
    Capabilities: [100] Advanced Error Reporting <?>
    Capabilities: [180] Device Serial Number ff-5a-23-00-69-55-7f-ff

brandon@alice:~$

---

### Post by lloyd_b on 2009-09-20
That device isn't supported by the regular kernel.  Take a look [here]("http://www.hogchain.net/attansic/attansic.html") - you should be able to download a driver for it.

Note that most of the drivers are marked "EXPERIMENTAL", so don't be too surprised if it doesn't work properly...

Lloyd B.

---

### Post by brandondiederich on 2009-09-20
None of those drivers work with my kernel...

brandon@alice:~$ uname -a
Linux alice 2.6.28-15-generic #49-Ubuntu SMP Tue Aug 18 18:40:08 UTC 2009 i686 GNU/Linux

---

### Post by UpsideDownFace on 2009-09-20
try typing at the terminal "ifconfig" 
it should give something like :- (from my LeNovo laptop)

eth0      Link encap:Ethernet  HWaddr 00:0a:e4:3a:ba:6c  
          inet6 addr: fe80::20a:e4ff:fe3a:ba6c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:346 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:50532 (49.3 KB)  TX bytes:468 (468.0 B)

eth1      Link encap:Ethernet  HWaddr 00:13:ce:8c:f8:12  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::213:ceff:fe8c:f812/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:821 errors:0 dropped:0 overruns:0 frame:0
          TX packets:230 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:104117 (101.6 KB)  TX bytes:41938 (40.9 KB)
          Interrupt:11 Base address:0x6000 Memory:d0200000-d0200fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1609 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1609 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:82092 (80.1 KB)  TX bytes:82092 (80.1 KB)

This says that eth0 exists with an inet6 address,but not an inet address,
eth1 exists with inet address 192.168.1.4
lo is the local host address.

"iwconfig" will tell you what wireless connections you have, mine is :-

eth1      IEEE 802.11g  ESSID:"TiscaliF49FCB"  
          Mode:Managed  Frequency:2.472 GHz  Access Point: 00:01:E3:F4:9F:CB   
          Bit Rate:54 Mb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=99/100  Signal level=-21 dBm  Noise level=-85 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

You can set the addresses and modes etc in System > Administration > Network

Then do :-    ping -c 3 localhost
              ping -c 3 192.168.1.4    (for my laptop)
              ping -c 3 [www.google.com](www.google.com)

and you get messages to say 100% failure at first, but when its working you get 100% success.

You also have to have an ethernet cable to something like a router or hub, or a wireless router like I have.

I hope this is some help.

---

### Post by brandondiederich on 2009-09-20
brandon@alice:~$ ifconfig
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:24:2c:18:4d:61  
          inet addr:192.168.1.6  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::224:2cff:fe18:4d61/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:86005 errors:0 dropped:0 overruns:0 frame:0
          TX packets:35612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:114677531 (114.6 MB)  TX bytes:4733377 (4.7 MB)

wmaster0  Link encap:UNSPEC  HWaddr 00-24-2C-18-4D-61-64-36-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

brandon@alice:~$ iwconfig
lo        no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"NETGEAR"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1B:2F:0B:73:22   
          Bit Rate=1 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=42/100  Signal level:-63 dBm  Noise level=-90 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.

brandon@alice:~$ ping -c 3 localhost
PING localhost (127.0.0.1) 56(84) bytes of data.
64 bytes from localhost (127.0.0.1): icmp_seq=1 ttl=64 time=0.111 ms
64 bytes from localhost (127.0.0.1): icmp_seq=2 ttl=64 time=0.069 ms
64 bytes from localhost (127.0.0.1): icmp_seq=3 ttl=64 time=0.060 ms

--- localhost ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.060/0.080/0.111/0.022 ms
brandon@alice:~$ ping -c 3 192.168.1.6
PING 192.168.1.6 (192.168.1.6) 56(84) bytes of data.
64 bytes from 192.168.1.6: icmp_seq=1 ttl=64 time=0.094 ms
64 bytes from 192.168.1.6: icmp_seq=2 ttl=64 time=0.064 ms
64 bytes from 192.168.1.6: icmp_seq=3 ttl=64 time=0.063 ms

--- 192.168.1.6 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.063/0.073/0.094/0.017 ms
brandon@alice:~$ ping [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.169.147) 56(84) bytes of data.
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=1 ttl=241 time=30.3 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=2 ttl=241 time=26.8 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=3 ttl=241 time=29.3 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=6 ttl=241 time=28.6 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=7 ttl=241 time=32.9 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=8 ttl=241 time=34.8 ms
64 bytes from yo-in-f147.google.com (64.233.169.147): icmp_seq=9 ttl=241 time=28.9 ms
^C
--- [www.l.google.com](www.l.google.com) ping statistics ---
9 packets transmitted, 7 received, 22% packet loss, time 8008ms
rtt min/avg/max/mdev = 26.802/30.266/34.830/2.550 ms



The pings worked but I have wireless working... if I shut off the wireless I get no replys

---

### Post by UpsideDownFace on 2009-09-20
I can't quite understand what you are trying to connect to with your ethernet.
Doesn't the wireless connection do all you want?

The only reason I have to use ethernet with my laptops is to connect to my router before it has been set up for wireless networking.

---

