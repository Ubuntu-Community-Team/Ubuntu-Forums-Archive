---
title: "Connecting to Wifi with a HP mini"
date: 2010-12-30
forum: Networking &amp; Wireless
---

### Post by bayern on 2010-12-30
Hi

I'm using a HP mini netbook, and I recently installed Ubuntu on it. I updated and did the whole proprietary drivers activation and it now scans and sees networks but I am having trouble actually using them now. It says that it is connected to a wireless network but it never loads any pages.

Any help?

---

### Post by PatchesTheCaveman on 2010-12-30
Hi bayern!  I'm sorry you're having trouble.

I'm going to have you run a few commands that will give us some diagnostic information that will help us pinpoint what's going wrong.

First, go to Applications > Accessories > Terminal on your top panel.  Then, in the black box that appears, type the following and press Enter:
```
lspci -v
```
Copy and paste what appears into a reply to this thread.  That tells us what kind of hardware you're running and whether the appropriate drivers are properly installed.

Next, type this and hit Enter:
```
sudo iwconfig
```
You'll need to enter your password when asked.  Copy and paste that in here too.  That lets us verify whether you're connected to your wireless router properly.

Finally, type this command and press Enter:
```
ifconfig -a
```
and copy and paste again.  That lets us know your IP configuration so we can see if something's wrong.

With all that in hand, we should be able to sort out your problem.  Thank you!

---

### Post by bayern on 2010-12-30
sean@ubuntu:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe980000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at dc80 [size=8]
    Memory at d0000000 (32-bit, prefetchable) [size=256M]
    Memory at fe940000 (32-bit, non-prefetchable) [size=256K]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0
    Memory at fe880000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fe938000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: fea00000-feafffff
    Prefetchable memory behind bridge: 0000000080000000-00000000801fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 0000e000-0000efff
    Memory behind bridge: feb00000-febfffff
    Prefetchable memory behind bridge: 0000000080200000-00000000803fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH7 Family USB UHCI Controller #1 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at dc00 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at d880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at d800 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at d480 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at fe937c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt, intel-rng

00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 02) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 26
    I/O ports at d400 [size=8]
    I/O ports at d080 [size=4]
    I/O ports at d000 [size=8]
    I/O ports at cc80 [size=4]
    I/O ports at cc00 [size=16]
    Memory at fe937800 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

01:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g (rev 01)
    Subsystem: Hewlett-Packard Company Device 365e
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at feafc000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

02:00.0 Ethernet controller: Atheros Communications Atheros AR8132 / L1c Gigabit Ethernet Adapter (rev c0)
    Subsystem: Hewlett-Packard Company Device 308f
    Flags: bus master, fast devsel, latency 0, IRQ 27
    Memory at febc0000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at ec80 [size=128]
    Capabilities: <access denied>
    Kernel driver in use: atl1c
    Kernel modules: atl1c







-----------------------------------------------------------








sean@ubuntu:~$ sudo iwconfig
[sudo] password for sean: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:"Munich"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:25:9C:4F:F4:67   
          Bit Rate=54 Mb/s   Tx-Power:24 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=-29 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:79  Rx invalid frag:0
          Tx excessive retries:6  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.



---------------------------------------------------



sean@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:26:55:cd:78:c9  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::226:55ff:fecd:78c9/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:54575861 errors:0 dropped:0 overruns:0 frame:0
          TX packets:29137 errors:0 dropped:0 overruns:0 carrier:6
          collisions:0 txqueuelen:1000 
          RX bytes:56346497 (56.3 MB)  TX bytes:2858108 (2.8 MB)
          Interrupt:27 

eth1      Link encap:Ethernet  HWaddr 0c:60:76:47:53:a0  
          inet addr:10.42.43.1  Bcast:10.42.43.255  Mask:255.255.255.0
          inet6 addr: fe80::e60:76ff:fe47:53a0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:1375
          TX packets:95 errors:19 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:7001 (7.0 KB)  TX bytes:23426 (23.4 KB)
          Interrupt:16 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20612 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20612 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6161077 (6.1 MB)  TX bytes:6161077 (6.1 MB)

pan0      Link encap:Ethernet  HWaddr f2:f0:f3:3b:ce:79  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by PatchesTheCaveman on 2010-12-30
All that looks good.  Let's try and see what happens when you contact the Internet.

Run this:
```
ping 8.8.8.8
```
Wait about 20 seconds and then press CTRL+C.  Copy and paste it in a thread here.

Then run this:
```
ping google.com
```
Wait another 20 seconds and press CTRL+C again.  Copy and paste that too.

---

### Post by bayern on 2010-12-30
sean@ubuntu:~$ ping 8.8.8.8
connect: Network is unreachable
sean@ubuntu:~$ ping google.com
ping: unknown host google.com
sean@ubuntu:~$

---

### Post by PatchesTheCaveman on 2010-12-30
Okay.  I just noticed that you are plugged into a wired network as well as a wireless network.  However, they appear to be completely different networks.  Is that the case?

---

### Post by bayern on 2010-12-30
I am plugged into the router via Ethernet cable, but when I ran that test I unplugged it since it ran perfectly fine with the cable in.

---

### Post by bayern on 2010-12-30
Never mind, I forgot that I messed with the WEP settings before I updated and all that. It works fine now, thanks for all your help!!!

---

