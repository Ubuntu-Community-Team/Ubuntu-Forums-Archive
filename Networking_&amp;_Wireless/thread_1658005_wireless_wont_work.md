---
title: "wireless wont work"
date: 2011-01-02
forum: Networking &amp; Wireless
---

### Post by mcfritzl on 2011-01-02
Alright, so my wireless isn't working. My netbook wireless detects the available networks but when I try to connect it doesn't. The box that asks me to put in the password occasionally shows up but it still doesn't load. I even tried re-installing Ubuntu and that didn't fix anything. Any help with this would be nice.

I'm using kernel version 2.6.35-22-generic and 

```
 *-network               
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:23:8b:4c:8e:02
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 multicast=yes
       resources: irq:44 ioport:3000(size=256) memory:51010000-51010fff memory:51000000-5100ffff memory:51020000-5103ffff
  *-network
       description: Wireless interface
       product: AR5001 Wireless Network Adapter
       vendor: Atheros Communications Inc.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 01
       serial: 00:24:2b:12:9f:6a
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:18 memory:55200000-5520ffff

```

---

### Post by Bucky Ball on 2011-01-02
Okay, first off, post the output of these two commands. Hit them one at a time pressing enter after each:

```
iwconfig
ifconfig

```Machine make and model would be handy, too, cos can't remember from last thread! Here's a couple of ideas:

1/ 10.04? If you are using the default network manager (NOT wicd), right click  on the network icon (or System->Administration->Network) and 'Edit Connections ...', click 'Wireless' and make sure the details in there match the ones on your wireless access point (AP or wireless router in other words). You should match the ESSID (SSID) and the security key; WEP, WPA, whatever it's using on the local machine.

Note well: If you are looking to use a static IP, you need to set that up there also and disable the router as a DHCP server. There are ways around this but it can be a problem if your router is serving IPs to other machines on your LAN (local area network, but you prob know that) via DHCP. I went for static IPs on all our machines; easier to identify when trying to communicate. But, of course, I could do that because it's a home network. Not always possible. 

2/ If all this fails you might like to try installing wicd instead of Network Manager. System->Admin->Synaptics and search for wicd. _**This will uninstall network manager!**_ If you have no success with wicd you may need to plug in an ethernet cable to kill wicd and reinstall Network Manager but that's about as drastic as it gets. 

See how you get on and let us know. Good luck. :wink:

---

### Post by mcfritzl on 2011-01-02
```

iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

```

```
 
ifconfig
eth0      Link encap:Ethernet  HWaddr 00:23:8b:4c:8e:02  
          inet addr:192.168.1.103  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:8bff:fe4c:8e02/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1457 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1399 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1299376 (1.2 MB)  TX bytes:191035 (191.0 KB)
          Interrupt:44 Base address:0x4000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6896 (6.8 KB)  TX bytes:6896 (6.8 KB)

wlan0     Link encap:Ethernet  HWaddr 00:24:2b:12:9f:6a  
          inet6 addr: fe80::224:2bff:fe12:9f6a/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:22 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:5623 (5.6 KB)

```I have an Acer Aspire One model ZG5. I tried the wicd but when I searched for it there were no results...

---

### Post by PatchesTheCaveman on 2011-01-02
You need to run
```
sudo iwconfig
```
for it to return useful results.  While you're at it, run this too so we can see if there are any known problems with your hardware/driver:
```
lspci -v
```

Also, to install wicd, run this:
```
sudo apt-get update
sudo apt-get remove network-manager
sudo apt-get install wicd
```

---

### Post by Bucky Ball on 2011-01-02
Patches: New user. wicd can be installed through Synaptic Package Manager and it will remove Network Manager in the process. No need for the command line.

Also, the results of iwconfig and ifconfig are right there (sudo not required). I asked OP to do this in my first post here. ;)

---

### Post by mcfritzl on 2011-01-02
Okay, so I installed wicd and something weird happened. I input all the information and clicked connect but when my netbook connected the computer I was using (I use one too look at the forums {that one has windows} while I try and fix my netbook) got a pop-up box that said there was a IP conflict and both computers wireless stopped working. So I disabled the wireless on the computer with windows and my laptop's wireless worked fine. I've never had an IP conflict before so I don't have a clue what it means. Any ideas?

Also @PatchesTheCaveMan 
My lspci -v results were as follows:

```

00:00.0 Host bridge: Intel Corporation Mobile 945GME Express Memory Controller Hub (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile 945GME Express Integrated Graphics Controller (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at 58480000 (32-bit, non-prefetchable) [size=512K]
    I/O ports at 60c0 [size=8]
    Memory at 40000000 (32-bit, prefetchable) [size=256M]
    Memory at 58500000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0
    Memory at 58400000 (32-bit, non-prefetchable) [size=512K]
    Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation N10/ICH 7 Family High Definition Audio Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 45
    Memory at 58540000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: 57300000-583fffff
    Prefetchable memory behind bridge: 0000000050000000-0000000050ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 2 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00003000-00004fff
    Memory behind bridge: 56300000-572fffff
    Prefetchable memory behind bridge: 0000000051000000-00000000520fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 3 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: 55200000-562fffff
    Prefetchable memory behind bridge: 0000000052100000-00000000530fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation N10/ICH 7 Family PCI Express Port 4 (rev 02) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=04, sec-latency=0
    I/O behind bridge: 00001000-00001fff
    Memory behind bridge: 54100000-551fffff
    Prefetchable memory behind bridge: 0000000053100000-00000000540fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 6080 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 17
    I/O ports at 6060 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 6040 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.3 USB Controller: Intel Corporation N10/ICH 7 Family USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 6020 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation N10/ICH 7 Family USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at 58544400 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e2) (prog-if 01 [Subtractive decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=32
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: leds-ss4200, iTCO_wdt, intel-rng

00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA IDE Controller (rev 02) (prog-if 80 [Master])
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 17
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 60a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix

00:1f.3 SMBus: Intel Corporation N10/ICH 7 Family SMBus Controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: medium devsel, IRQ 11
    I/O ports at 6000 [size=32]
    Kernel modules: i2c-i801

02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 44
    I/O ports at 3000 [size=256]
    Memory at 51010000 (64-bit, prefetchable) [size=4K]
    Memory at 51000000 (64-bit, prefetchable) [size=64K]
    Expansion ROM at 51020000 [disabled] [size=128K]
    Capabilities: <access denied>
    Kernel driver in use: r8169
    Kernel modules: r8169

03:00.0 Ethernet controller: Atheros Communications Inc. AR5001 Wireless Network Adapter (rev 01)
    Subsystem: Foxconn International, Inc. Device e008
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at 55200000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath5k
    Kernel modules: ath5k

04:00.0 System peripheral: JMicron Technology Corp. SD/MMC Host Controller
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 54100300 (32-bit, non-prefetchable) [size=256]
    Expansion ROM at 53100000 [disabled] [size=32K]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

04:00.2 SD Host controller: JMicron Technology Corp. Standard SD Host Controller (prog-if 01)
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: fast devsel, IRQ 19
    Memory at 54100200 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel modules: sdhci-pci

04:00.3 System peripheral: JMicron Technology Corp. MS Host Controller
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at 54100100 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: jmb38x_ms
    Kernel modules: jmb38x_ms

04:00.4 System peripheral: JMicron Technology Corp. xD Host Controller
    Subsystem: Acer Incorporated [ALI] Device 015b
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at 54100000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
 
```

---

### Post by mcfritzl on 2011-01-02
My wireless is fixed!!! I just had to uncheck static IP's cause apparently it conflicted with the main computer. But it's working great now! Thanks everyone!

---

### Post by Bucky Ball on 2011-01-03
Well done! You beat me to it. static IP set.

Great news. Please mark thread as solved, have fun with the OS, post back with problems, and enjoy the learning curve. ;)

*** Oh, right. Conflicted with the main computer? Easy: just give your machine a different static IP and away you go. If it's another Ubuntu machine then you should be able to connect directly to the other computer by doing:

Places->Connect to Server ...
Service Type = 'SSH'
Server = IP of the other computer

Voila!

You need to know the user name and password for the other machine, of course! I find this method easy and better for identifying the other three machines here and you can use the IPs in just about any app whereas computer names are sometimes dodgy.

---

