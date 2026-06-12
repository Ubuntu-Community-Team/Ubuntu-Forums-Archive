---
title: "Another ipw2200BG problem"
date: 2009-11-25
forum: Networking &amp; Wireless
---

### Post by brucem9999 on 2009-11-25
I have a Dell Inspirion I6000 running XP (for the moment! Until I get this networking problem solved!)

I'm trying to configure 9.10 running the LiveCD until I get this working. I've been using the Ubuntu Hacks book, which is somewhat disjointed, but has a lot of good info. Anyway....

I tried all of the solutions offered for this person ([http://ubuntuforums.org/showthread.php?t=1314355&highlight=2200bg](http://ubuntuforums.org/showthread.php?t=1314355&highlight=2200bg)), and here are the print outs:

   To run a command as administrator (user "root"), use "sudo <command>". 
  See "man sudo_root" for details. 
   
  **ubuntu@ubuntu:~$ sudo modprobe iwp2200 **
  FATAL: Module iwp2200 not found. 
   
  **ubuntu@ubuntu:~$ lspci -vn **
  00:00.0 0600: 8086:2590 (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, fast devsel, latency 0 
              Capabilities: <access denied> 
              Kernel driver in use: agpgart-intel 
              Kernel modules: intel-agp 
   
  00:02.0 0300: 8086:2592 (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, fast devsel, latency 0, IRQ 16 
              Memory at dff00000 (32-bit, non-prefetchable) [size=512K] 
              I/O ports at ec38 [size=8] 
              Memory at c0000000 (32-bit, prefetchable) [size=256M] 
              Memory at dfec0000 (32-bit, non-prefetchable) [size=256K] 
              Capabilities: <access denied> 
              Kernel modules: intelfb 
   
  00:02.1 0380: 8086:2792 (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, fast devsel, latency 0 
              Memory at dff80000 (32-bit, non-prefetchable) [size=512K] 
              Capabilities: <access denied> 
   
  00:1d.0 0c03: 8086:2658 (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 0, IRQ 16 
              I/O ports at bf80 [size=32] 
              Kernel driver in use: uhci_hcd 
   
  00:1d.1 0c03: 8086:2659 (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 0, IRQ 17 
              I/O ports at bf60 [size=32] 
              Kernel driver in use: uhci_hcd 
   
  00:1d.2 0c03: 8086:265a (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 0, IRQ 18 
              I/O ports at bf40 [size=32] 
              Kernel driver in use: uhci_hcd 
   
  00:1d.3 0c03: 8086:265b (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 0, IRQ 19 
              I/O ports at bf20 [size=32] 
              Kernel driver in use: uhci_hcd 
   
  00:1d.7 0c03: 8086:265c (rev 03) (prog-if 20) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 0, IRQ 16 
              Memory at ffa80800 (32-bit, non-prefetchable) [size=1K] 
              Capabilities: <access denied> 
              Kernel driver in use: ehci_hcd 
   
  00:1e.0 0604: 8086:2448 (rev d3) (prog-if 01) 
              Flags: bus master, fast devsel, latency 0 
              Bus: primary=00, secondary=03, subordinate=07, sec-latency=32 
              Memory behind bridge: dfd00000-dfdfffff 
              Prefetchable memory behind bridge: 0000000030000000-0000000033ffffff 
              Capabilities: <access denied> 
   
  00:1e.2 0401: 8086:266e (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 0, IRQ 16 
              I/O ports at ed00 [size=256] 
              I/O ports at ec40 [size=64] 
              Memory at dfebfe00 (32-bit, non-prefetchable) [size=512] 
              Memory at dfebfd00 (32-bit, non-prefetchable) [size=256] 
              Capabilities: <access denied> 
              Kernel driver in use: Intel ICH 
              Kernel modules: snd-intel8x0 
   
  00:1e.3 0703: 8086:266d (rev 03) 
              Subsystem: 14f1:5423 
              Flags: medium devsel, IRQ 17 
              I/O ports at ee00 [size=256] 
              I/O ports at ec80 [size=128] 
              Capabilities: <access denied> 
              Kernel modules: snd-intel8x0m 
   
  00:1f.0 0601: 8086:2641 (rev 03) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 0 
              Kernel modules: iTCO_wdt, intel-rng 
   
  00:1f.2 0101: 8086:2653 (rev 03) (prog-if 80 [Master]) 
              Subsystem: 1028:0188 
              Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17 
              I/O ports at 01f0 [size=8] 
              I/O ports at 03f4 [size=1] 
              I/O ports at 0170 [size=8] 
              I/O ports at 0374 [size=1] 
              I/O ports at bfa0 [size=16] 
              Capabilities: <access denied> 
              Kernel driver in use: ata_piix 
   
  00:1f.3 0c05: 8086:266a (rev 03) 
              Subsystem: 1028:0188 
              Flags: medium devsel, IRQ 10 
              I/O ports at 10c0 [size=32] 
              Kernel modules: i2c-i801 
   
  03:00.0 0200: 14e4:170c (rev 02) 
              Subsystem: 1028:0188 
              Flags: bus master, fast devsel, latency 64, IRQ 18 
              Memory at dfdfe000 (32-bit, non-prefetchable) [size=8K] 
              Capabilities: <access denied> 
              Kernel driver in use: b44 
              Kernel modules: b44 
   
  03:01.0 0607: 1180:0476 (rev b3) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 168, IRQ 19 
              Memory at dfd00000 (32-bit, non-prefetchable) [size=4K] 
              Bus: primary=03, secondary=04, subordinate=07, sec-latency=176 
              Memory window 0: 30000000-33fff000 (prefetchable) 
              Memory window 1: 34000000-37fff000 
              I/O window 0: 00001400-000014ff 
              I/O window 1: 00001800-000018ff 
              16-bit legacy interface ports at 0001 
              Kernel driver in use: yenta_cardbus 
              Kernel modules: yenta_socket 
   
  03:01.1 0c00: 1180:0552 (rev 0(prog-if 10) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 64, IRQ 18 
              Memory at dfdfc800 (32-bit, non-prefetchable) [size=2K] 
              Capabilities: <access denied> 
              Kernel driver in use: ohci1394 
              Kernel modules: firewire-ohci, ohci1394 
   
  03:01.2 0805: 1180:0822 (rev 17) (prog-if 01) 
              Subsystem: 1028:0188 
              Flags: bus master, medium devsel, latency 64, IRQ 17 
              Memory at dfdfc700 (32-bit, non-prefetchable) [size=256] 
              Capabilities: <access denied> 
              Kernel driver in use: sdhci-pci 
              Kernel modules: sdhci-pci 
   
  03:03.0 0280: 8086:4220 (rev 05) 
              Subsystem: 8086:2721 
              Flags: bus master, medium devsel, latency 64, IRQ 17 
              Memory at dfdfd000 (32-bit, non-prefetchable) [size=4K] 
              Capabilities: <access denied> 
              Kernel driver in use: ipw2200 
              Kernel modules: ipw2200 
   
  **ubuntu@ubuntu:~$ iwconfig **
  lo        no wireless extensions. 
   
  eth0      no wireless extensions. 
   
  eth1      unassociated  ESSIDff/any  
            Mode:Managed  Channel=0  Access Point: Not-Associated   
            Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
            Retry limit:7   RTS thrff   Fragment thrff 
            Power Managementff 
            Link Quality:0  Signal level:0  Noise level:0 
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0 
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0 
   
  pan0      no wireless extensions. 
   
  **ubuntu@ubuntu:~$ sudo apt-get install linux-backports-modules-karmic**
  
  Reading package lists... Done
  
  Building dependency tree       
  
  Reading state information... Done
  
  E: Couldn't find package linux-backports-modules-karmic
  
   
  **ubuntu@ubuntu:~$ sudo ifconfig eth1 up**
  
  
  **ubuntu@ubuntu:~$ iwconfig**
  
  lo        no wireless extensions.
  
   
   
  eth0      no wireless extensions.
  
   
   
  eth1      unassociated  ESSIDff/any  
  
            Mode:Managed  Channel=0  Access Point: Not-Associated   
  
            Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
  
            Retry limit:7   RTS thrff   Fragment thrff
  
            Power Managementff
  
            Link Quality:0  Signal level:0  Noise level:0
  
            Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
  
            Tx excessive retries:0  Invalid misc:0   Missed beacon:0
  
   
   
  pan0      no wireless extensions.
  
   
  **ubuntu@ubuntu:~$ sudo lshw -C network **
    *-network:0             
         description: Ethernet interface 
         product: BCM4401-B0 100Base-TX 
         vendor: Broadcom Corporation 
         physical id: 0 
         bus info: pci@0000:03:00.0 
         logical name: eth0 
         version: 02 
         serial: 00:12:3f:ea:43:0b 
         size: 10MB/s 
         capacity: 100MB/s 
         width: 32 bits 
         clock: 33MHz 
         capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
         configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=2.0 duplex=half latency=64 link=no module=ssb multicast=yes port=twisted pair speed=10MB/s 
    *-network:1 
         description: Wireless interface 
         product: PRO/Wireless 2200BG [Calexico2] Network Connection 
         vendor: Intel Corporation 
         physical id: 3 
         bus info: pci@0000:03:03.0 
         logical name: eth1 
         version: 05 
         serial: 00:13:ce:3f:0c:fa 
         width: 32 bits 
         clock: 33MHz 
         capabilities: pm bus_master cap_list ethernet physical wireless 
         configuration: broadcast=yes driver=ipw2200 driverversion=1.2.2kmprq firmware=ABG:9.0.2.6 (Mar 22 2005) latency=64 link=no maxlatency=24 mingnt=3 module=ipw2200 multicast=yes wireless=unassociated 
    *-network DISABLED 
         description: Ethernet interface 
         physical id: 2 
         logical name: pan0 
         serial: f2:e3:52:6c:66:f1 
         capabilities: ethernet physical 
         configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes 
  ubuntu@ubuntu:~$ 


-----------------------------------------------------

END OF LISTING
-------------------------------------------


I've downloaded ipw2200-1.2.0.tgz, -ap-0-3.tgz, -fw-3.1.tgz and _linux_1_2_0.tgz from another web site, but ipw is supposed to work "out of the box" according to the list:

   PRO/Wireless 2200 (Centrino) 
  ? 
  ipw2200 
  Supports network install: Yes* 
  Supported in installed system: Yes* 
  Works &#8220;out of the box&#8221;: Yes* 
  Automatically detected since the first installation steps. [Driver Upgrade How-To]("http://nickselby.com/articles/technology/index.htm?a=1807") [WPA How-To]("http://ubuntuforums.org/showthread.php?t=26623")
  2005-12-09 

Help, please.

---

