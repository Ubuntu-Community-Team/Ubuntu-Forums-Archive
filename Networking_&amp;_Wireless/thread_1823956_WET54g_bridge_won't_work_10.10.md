---
title: "WET54g bridge won't work 10.10"
date: 2011-08-12
forum: Networking &amp; Wireless
---

### Post by moonsal on 2011-08-12
Pretty much just that............ It works fine when I boot into Win7 but in 10.10... Nothing..

ifconfig
```
eth0      Link encap:Ethernet  HWaddr 00:16:76:13:16:44  
          inet6 addr: fe80::216:76ff:fe13:1644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:192 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:29016 (29.0 KB)  TX bytes:13386 (13.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4247 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4247 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:676211 (676.2 KB)  TX bytes:676211 (676.2 KB)

wlan0     Link encap:Ethernet  HWaddr 00:12:17:9d:99:f2  
          inet addr:192.168.1.102  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:17ff:fe9d:99f2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:152204 errors:0 dropped:0 overruns:0 frame:0
          TX packets:131654 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:165926014 (165.9 MB)  TX bytes:18917360 (18.9 MB)
          Interrupt:21 Memory:feaee000-feaf0000 

```

Any thoughts.... I've read and read and tried just about everything out there... Been to multiple forums and always get the same answer... "If it works in WinX it should work in 10.10"... But it doesn't... Any ideas please

---

### Post by moonsal on 2011-08-12
sudo ifconfig eth0 192.168.1.2 up

```
eth0      Link encap:Ethernet  HWaddr 00:16:76:13:16:44  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::216:76ff:fe13:1644/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:466 errors:0 dropped:0 overruns:0 frame:0
          TX packets:321 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:231040 (231.0 KB)  TX bytes:38032 (38.0 KB)

```



Disconnected my Wireless connection and ran
ping -c3 192.168.1.226
```
PING 192.168.1.226 (192.168.1.226) 56(84) bytes of data.
64 bytes from 192.168.1.226: icmp_req=1 ttl=255 time=3.80 ms
64 bytes from 192.168.1.226: icmp_req=1 ttl=254 time=4.77 ms (DUP!)
64 bytes from 192.168.1.226: icmp_req=2 ttl=255 time=1.07 ms
64 bytes from 192.168.1.226: icmp_req=2 ttl=254 time=2.13 ms (DUP!)
64 bytes from 192.168.1.226: icmp_req=3 ttl=255 time=1.10 ms

--- 192.168.1.226 ping statistics ---
3 packets transmitted, 3 received, +2 duplicates, 0% packet loss, time 2003ms
rtt min/avg/max/mdev = 1.072/2.577/4.773/1.482 ms

```

Still Auto Eth0 won't work...

---

### Post by moonsal on 2011-08-13
Anyone???

---

### Post by westie457 on 2011-08-13
> **moonsal said:**
> Anyone???

Hi.

Open a terminal and run these commands one at a time.
```
lspci -v
lshw -C network
rfkill list all
```

Highlight all the output and paste in a new reply here between ```
 
``` tags by clicking the # at the top of the message pane.


Thank you.

---

### Post by moonsal on 2011-08-13
lspci -v
```
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Dell Device 01d5
        Flags: bus master, fast devsel, latency 0
        Memory at e0000000 (32-bit, prefetchable) [size=256M]
        Capabilities: <access denied>
        Kernel driver in use: agpgart-intel
        Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA controller])
        Subsystem: Dell Device 01d5
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ed98 [size=8]
        Expansion ROM at <unassigned> [disabled]
        Capabilities: <access denied>
        Kernel driver in use: i915
        Kernel modules: i915

00:06.0 System peripheral: Intel Corporation 82865G/PE/P Processor to I/O Memory Interface (rev 02)
        Flags: fast devsel
        Memory at fecf0000 (32-bit, non-prefetchable) [size=4K]

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff80 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff60 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff20 [size=32]
        Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 23
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
        Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff
        Kernel modules: shpchp

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0
        Kernel modules: iTCO_wdt, intel-rng

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]
        Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Dell Device 01d5
        Flags: medium devsel, IRQ 3
        I/O ports at eda0 [size=32]
        Kernel modules: i2c-i801

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>
        Kernel driver in use: Intel ICH
        Kernel modules: snd-intel8x0

01:00.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
        Subsystem: Linksys WMP54GS v1.1 802.11g Wireless-G PCI Adapter with SpeedBooster
        Flags: bus master, fast devsel, latency 64, IRQ 21
        Memory at feaee000 (32-bit, non-prefetchable) [size=8K]
        Kernel driver in use: ndiswrapper
        Kernel modules: ssb

01:01.0 Communication controller: Conexant Systems, Inc. HSF 56k Data/Fax Modem
        Subsystem: Conexant Systems, Inc. Dimension 3000
        Flags: bus master, medium devsel, latency 64, IRQ 9
        Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]
        I/O ports at df38 [size=8]
        Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at feaed000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at df40 [size=64]
        Capabilities: <access denied>
        Kernel driver in use: e100
        Kernel modules: e100

```

lshw -C network
```
*-network:0             
       description: Wireless interface
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: wlan0
       version: 02
       serial: 00:12:17:9d:99:f2
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+wmp54gs driverversion=1.56+Linksys,12/22/2004, 3.100.4 ip=192.168.1.102 latency=64 multicast=yes wireless=IEEE 802.11g
       resources: irq:21 memory:feaee000-feaeffff
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:16:76:13:16:44
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI firmware=N/A latency=64 maxlatency=56 mingnt=8 multicast=yes
       resources: irq:20 memory:feaed000-feaedfff ioport:df40(size=64)

```

rfkill list all
```
returns to prompt
```

---

### Post by westie457 on 2011-08-13
Okay here we go with a solution.

Remove the current drivers you have installed, they are not functioning properly. Do not reboot just yet.

Open a terminal and run ```
sudo apt-get install b43-fwcutter && sudo apt-get install firmware-b43-installer
```

Now reboot and when all has settled click on Network Manager top of screen to see a list of available networks. Click on yours enter some details if needed and away you go.

---

### Post by chili555 on 2011-08-13
I wonder how this will assist moonsal to get an ethernet connection to his bridge.

---

### Post by moonsal on 2011-08-13
Isn't the b43 for my wireless card????(it works just fine).. I have an on-board NIC that runs to my bridge....

---

### Post by moonsal on 2011-08-13
```
01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
        Subsystem: Dell Device 01d5
        Flags: bus master, medium devsel, latency 64, IRQ 20
        Memory at feaed000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at df40 [size=64]
        Capabilities: [COLOR="Red"]<access denied>[/color]
        Kernel driver in use: e100
        Kernel modules: e100
```

This is my onboard NIC....Could this "access denied" be a problem???

---

### Post by chili555 on 2011-08-13
> This is my onboard NIC....Could this "access denied" be a problem???No. It just means that there are additional details about your wireless card that are only available if you are sudo.

You obviously are communicating with the WET54G. Can you log in to the configuration pages?```
firefox http://192.168.1.226
```Is the device getting an IP address from the router?

---

### Post by moonsal on 2011-08-13
Ok...


Yea man... I can log right in.... But am unable to get an IP..

---

### Post by westie457 on 2011-08-13
> **chili555 said:**
> I wonder how this will assist moonsal to get an ethernet connection to his bridge.

Thank you for pointing that out chili555, obviously there I completely mis-interpreted the problem. I will step back from this and learn as you go through the steps to resolve this.

---

### Post by chili555 on 2011-08-13
> **moonsal said:**
> Ok...


Yea man... I can log right in.... But am unable to get an IP..At this point, I suspect your computer has an IP temporarily, 192.168.1.2. Have you gone through the appropriate setup in the WET54G? Please see here: [http://www6.nohold.net/Cisco2/ukp.aspx?pid=80&g=80&vw=1&articleid=4898](http://www6.nohold.net/Cisco2/ukp.aspx?pid=80&g=80&vw=1&articleid=4898)

---

### Post by moonsal on 2011-08-13
Yes... I have done all of that.. If it make any difference, I can boot up into Win7 and it works just fine...

---

### Post by Seraph Trend on 2011-08-13
> **westie457 said:**
> Hi.

Open a terminal and run these commands one at a time.
```
lspci -v
lshw -C network
rfkill list all
```

Highlight all the output and paste in a new reply here between ```
 
``` tags by clicking the # at the top of the message pane.


Thank you.
OMG This is amazing!!
After so much searching your advice finally worked for me. 
I recently switched from Windblows to Ubuntu Linux. Everything was working fine except for my wireless internet. 
I have been searching endlessly for a solution. You dont know how happy i am to finally have the last piece of the puzzle.
Thank you so much [westie457]("http://ubuntuforums.org/member.php?u=970779") !!!

---

### Post by Seraph Trend on 2011-08-13
Hello there, i am new to Ubuntu. I was having difficulty with my  wireless connection until i read your post over on  [http://ubuntuforums.org/showthread.php?t=1823956](http://ubuntuforums.org/showthread.php?t=1823956)

now im able to use the net over a wifi connection. Thank you so much. I have been searching for this for a while now. 
I am sooooo grateful of your input.

---

### Post by moonsal on 2011-08-14
bump bu da bump :P

---

### Post by moonsal on 2011-08-14
Of all these people who have much experience in this, you mean to tell me no one has any ideas?? I fail to believe that:o:o

---

### Post by moonsal on 2011-08-14
Here's something odd...... My routers ip area is 192.168.100 - *.149   Now my bridge is set at 192.168.1.226....

I have ifconfig eth0 192.168.1.1 up and still nothing... Would this be a problem???

---

### Post by westie457 on 2011-08-17
Hi.
If you have not got it working yet you could always try the suggestion here.

[http://ubuntuforums.org/showpost.php?p=11150592&postcount=4](http://ubuntuforums.org/showpost.php?p=11150592&postcount=4)

It might work for you.

---

