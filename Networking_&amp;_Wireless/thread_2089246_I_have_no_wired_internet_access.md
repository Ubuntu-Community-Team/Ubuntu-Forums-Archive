---
title: "I have no wired internet access"
date: 2012-11-28
forum: Networking &amp; Wireless
---

### Post by wildonion on 2012-11-28
Hi-I just got done installing ubuntu 12.10, but now I can't connect to the internet with my wired cable modem connection. At the moment, I can only connect to the internet via wireless connection. 

In the help section of the browser, it says that ubuntu should recognize the network and start up a wizard to walk you through the process, but I haven't gotten to that point yet. My connections are the same when I run my windows os, and windows usually recognizes both the wired and wireless connections pretty quickly.  

The only difference between the two operating systems are that one is 64bit (windows) and the other is 32bit (ubuntu). I only went with the 32bit version because it was recommended, but would something like this be the cause of my problem? I'm thinking it could be as simple as installing a few drivers, but I'm not sure.

---

### Post by Monotoko on 2012-11-28
You may have to install the modem drivers first, what's the make and model of your modem?

---

### Post by wildonion on 2012-11-28
Thanks for the reply.

It's a Motorola cable modem, model # SBV5121XM

---

### Post by oldfred on 2012-11-28
Did liveCD connect to Internet?

Post these: best to use code tags as some may be longer. # in edit panel above message.

sudo lshw | grep -m 1 -A 25 "*-network"
lspci
#but I do not like to post HWaddr or Mac address as it is unique and someone can spoof yours
ifconfig eth0

lspci -v
dmesg | grep eth
# Plug in and see if errors:
dmesg | tail -n10
# Check by chipset:ie e1000e
sudo lsmod | grep e1000e

---

### Post by wildonion on 2012-11-28
I didn't try to connect to the internet with the liveCD, so I'm not sure about that.

Here is the terminal output information you asked for:
(This is unfamiliar territory for me, so just let me know if I inputed something wrong.)

```
 *-network UNCLAIMED
                description: Ethernet controller
                product: AR8161 Gigabit Ethernet
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 10
                width: 64 bits
                clock: 33MHz
                capabilities: pm pciexpress msi msix bus_master cap_list
                configuration: latency=0
                resources: memory:e0500000-e053ffff ioport:2000(size=128)
        *-pci:1
             description: PCI bridge
             product: 7 Series/C210 Series Chipset Family PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: c4
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 memory:e0400000-e04fffff

``````
lspci
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

```When I input the ifconfig eth0 into the terminal I just get the following: ```
 ifconfig eth0
eth0: error fetching interface information: Device not found

```When I only input ifconfig I get the following: ```
ifconfig 
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1281 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1281 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:123228 (123.2 KB)  TX bytes:123228 (123.2 KB)

wlan0     Link encap:Ethernet  HWaddr 20:68:9d:54:c5:3c  
          inet addr:192.168.0.100  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::2268:9dff:fe54:c53c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11898 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8911 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12084855 (12.0 MB)  TX bytes:1522913 (1.5 MB)


``````
lspci -v
00:00.0 Host bridge: Intel Corporation 2nd Generation Core Processor Family DRAM Controller (rev 09)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at e0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at e0600000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd

00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at e0614000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>
    Kernel driver in use: mei
    Kernel modules: mei

00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at e0619000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, fast devsel, latency 0, IRQ 44
    Memory at e0610000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: snd_hda_intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: e0500000-e05fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    Memory behind bridge: e0400000-e04fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at e0618000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: lpc_ich

00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04) (prog-if 01 [AHCI 1.0])
    Subsystem: Lenovo Device 3977
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 40
    I/O ports at 3088 [size=8]
    I/O ports at 3094 [size=4]
    I/O ports at 3080 [size=8]
    I/O ports at 3090 [size=4]
    I/O ports at 3060 [size=32]
    Memory at e0617000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci

00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 3977
    Flags: medium devsel, IRQ 10
    Memory at e0615000 (64-bit, non-prefetchable) [size=256]
    I/O ports at 3040 [size=32]
    Kernel modules: i2c-i801

01:00.0 Ethernet controller: Atheros Communications Inc. AR8161 Gigabit Ethernet (rev 10)
    Subsystem: Lenovo Device 3979
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at e0500000 (64-bit, non-prefetchable) [size=256K]
    I/O ports at 2000 [size=128]
    Capabilities: <access denied>

02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
    Subsystem: Lenovo Device 30a1
    Flags: bus master, fast devsel, latency 0, IRQ 17
    Memory at e0400000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: ath9k
    Kernel modules: ath9k


```
For the following codes, I'm not getting much information from the terminal. dmesg | tail -n10 was the only to give me some output, and it was mainly about EEPROM and country codes. I don't know if that makes any sense to you, but I can post it along with the others if you'd like.

dmesg | grep eth
dmesg | tail -n10
sudo lsmod | grep e1000e     

Thanks for the help,

Brian

---

### Post by oldfred on 2012-11-28
See this thread.

[http://ubuntuforums.org/showthread.php?p=12206393](http://ubuntuforums.org/showthread.php?p=12206393)

I am somewhat surprised it is not in 12.10.

But on video we find issues because kernel headers are not installed. I wonder is similar issue? Will not hurt to add headers, then look for Atheros in system settings drivers.
 sudo apt-get install linux-headers-generic

---

### Post by wildonion on 2012-11-28
oldfred,

Thanks so much for that. It was chili555's 6th post on that thread that fixed my problem. I'm not sure exactly what I did, but once I finished the last step, ubuntu recognized my wired connection. 

Take Care,

Brian

---

### Post by wildonion on 2012-11-28
oldfred,

I originally tried following the steps found in reply #4 of the thread you gave me, but when it came to enter the web address into the terminal, I would get a 404 not found error. After that I moved on to reply #6, which worked for me, as I mentioned above.

Brian

---

