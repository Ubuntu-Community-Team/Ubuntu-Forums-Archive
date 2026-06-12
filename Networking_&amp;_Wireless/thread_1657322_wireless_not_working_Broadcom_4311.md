---
title: "wireless not working Broadcom 4311"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by guptasurbhi26 on 2011-01-01
I have a HP Pavilion dv 2610tu laptop.I installed ubuntu 10.10 last night and i'm completely new to it..
When i typed lspci on terminal window..this is what i got..

[HTML]root@ashish-HP-Pavilion-dv2500-Notebook-PC:~# lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
07:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
08:09.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
[/HTML]Also when i typed..sudo lshw -C network..it shows that i've broadcom 4311 wireless card.So i clicked on system->Admin->Additional driver and installed the Broadcom B43 wireless driver.At the bottom it shows the driver is activated and currently in use..
but still i dont see my college or home wifi network notifications...

What do i do??

[HTML]root@ashish-HP-Pavilion-dv2500-Notebook-PC:~# sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: 88E8039 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: eth0
       version: 14
       serial: 00:16:d3:f8:df:d5
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=sky2 driverversion=1.28 duplex=full firmware=N/A ip=192.168.1.4 latency=0 link=yes multicast=yes port=twisted pair speed=100MB/s
       resources: irq:44 memory:f4200000-f4203fff ioport:3000(size=256)
  *-network
       description: Network controller
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 02
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=b43-pci-bridge latency=0
       resources: irq:19 memory:f4300000-f4303fff
  *-network DISABLED
       description: Wireless interface
       physical id: 3
       logical name: wlan0
       serial: 00:1a:73:cd:5a:ce
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-24-generic firmware=N/A link=yes multicast=yes wireless=IEEE 802.11bg
[/HTML]

---

### Post by PatchesTheCaveman on 2011-01-01
Hi guptasurbhi26.  Happy New Year!

To install the driver for your Broadcom wireless card, go to System > Administration > Additional Drivers on your top panel.  Then, select the *Broadcom STA wireless driver* and click Install.

You should then be able to click the wireless icon on your top panel and connect to any wireless network in your area.

Let us know if you have any trouble.

---

### Post by guptasurbhi26 on 2011-01-01
Hey Happy new year to you too!Btw i've removed 10.10 and have installed Ubuntu 10.04 LTS.I installed the STA driver and then rebooted the system.I still dont see any wifi notifications on the top panel.Also when i went to System->Preferences->Netwrok Connections..it doesnt show anything under the wireless tab.Though my hardware drivers shows STA activated and currently in use.
I typed sudo lshw -C network on the terminal window and this is what i see for wifi..
> 
 *-network
       description: Wireless interface
       product: BCM4311 802.11b/g WLAN
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth1
       version: 02
       serial: 00:1a:73:cd:5a:ce
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=wl0 driverversion=5.60.48.36 latency=0 multicast=yes wireless=IEEE 802.11bg
       resources: irq:19 memory:f4300000-f4303fff


---

### Post by PatchesTheCaveman on 2011-01-01
Run these commands and copy/paste the output:
```
lspci -v
sudo iwconfig
```

---

### Post by guptasurbhi26 on 2011-01-01
Here..

> ashish@ashish:~$ lspci -v
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>
    Kernel driver in use: agpgart-intel
    Kernel modules: intel-agp

00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, fast devsel, latency 0, IRQ 30
    Memory at f4000000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    Capabilities: <access denied>
    Kernel driver in use: i915
    Kernel modules: i915

00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, fast devsel, latency 0
    Memory at f4100000 (64-bit, non-prefetchable) [size=1M]
    Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 16
    I/O ports at 1840 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 21
    I/O ports at 1860 [size=32]
    Kernel driver in use: uhci_hcd

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 18
    Memory at f4705c00 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, fast devsel, latency 0, IRQ 22
    Memory at f4500000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: HDA Intel
    Kernel modules: snd-hda-intel

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=03, sec-latency=0
    I/O behind bridge: 00002000-00002fff
    Memory behind bridge: f2000000-f3ffffff
    Prefetchable memory behind bridge: 00000000f0000000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=05, subordinate=05, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f4200000-f42fffff
    Prefetchable memory behind bridge: 0000000040000000-00000000401fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=06, subordinate=06, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: 40200000-403fffff
    Prefetchable memory behind bridge: 0000000040400000-00000000405fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=07, subordinate=07, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f4300000-f43fffff
    Prefetchable memory behind bridge: 0000000040600000-00000000407fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport
    Kernel modules: shpchp

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 23
    I/O ports at 1880 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 18a0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 18
    I/O ports at 18c0 [size=32]
    Kernel driver in use: uhci_hcd

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03) (prog-if 20)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f4706000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd

00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3) (prog-if 01)
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=08, subordinate=08, sec-latency=32
    Memory behind bridge: f4400000-f44fffff
    Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>
    Kernel modules: iTCO_wdt

00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 1830 [size=16]
    Kernel driver in use: ata_piix

00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03) (prog-if 01)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 29
    I/O ports at 18f8 [size=8]
    I/O ports at 18ec [size=4]
    I/O ports at 18f0 [size=8]
    I/O ports at 18e8 [size=4]
    I/O ports at 1c00 [size=32]
    Memory at f4705000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ahci
    Kernel modules: ahci

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: medium devsel, IRQ 11
    Memory at 40800000 (32-bit, non-prefetchable) [size=256]
    I/O ports at 1c20 [size=32]
    Kernel modules: i2c-i801

05:00.0 Ethernet controller: Marvell Technology Group Ltd. 88E8039 PCI-E Fast Ethernet Controller (rev 14)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at f4200000 (64-bit, non-prefetchable) [size=16K]
    I/O ports at 3000 [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sky2
    Kernel modules: sky2

07:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
    Subsystem: Hewlett-Packard Company Device 1375
    Flags: bus master, fast devsel, latency 0, IRQ 19
    Memory at f4300000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: wl
    Kernel modules: wl, ssb

08:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05) (prog-if 10)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 32, IRQ 16
    Memory at f4400000 (32-bit, non-prefetchable) [size=2K]
    Capabilities: <access denied>
    Kernel driver in use: ohci1394
    Kernel modules: firewire-ohci, ohci1394

08:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 32, IRQ 18
    Memory at f4400800 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci-pci

08:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 32, IRQ 10
    Memory at f4400c00 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: ricoh-mmc
    Kernel modules: ricoh_mmc

08:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
    Subsystem: Hewlett-Packard Company Device 30cd
    Flags: bus master, medium devsel, latency 32, IRQ 10
    Memory at f4401000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>

08:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff) (prog-if ff)
    !!! Unknown header type 7f

ashish@ashish:~$ 


> 
ashish@ashish:~$ sudo iwconfig
[sudo] password for ashish: 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   Tx-Power:off   
          Retry min limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Managementmode:All packets received
          Link Quality=5/5  Signal level=0 dBm  Noise level=0 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


---

### Post by bkratz on 2011-01-01
Everything looks looks good there (except tx power off). Do you see any wireless networks when you do

sudo ifconfig eth1 up
sudo iwlist scan

?

---

### Post by guptasurbhi26 on 2011-01-01
hey bkratz..Happy new year!

ok..this is what i got..
> ashish@ashish:~$ sudo ifconfig eth1 up
ashish@ashish:~$ sudo iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Failed to read scan data : Invalid argument

pan0      Interface doesn't support scanning.


---

### Post by bkratz on 2011-01-01
I don't have any idea what Invalid argument is referring too!? Maybe someone else does ( I hope) or could have it been a typing error?.

Anyway,  let's try

sudo iwconfig eth1 txpower 15
sudo iwlist scan

If the txpower command gives an error try a smaller number like 10.
and happy New Year to you too.

---

### Post by bkratz on 2011-01-01
Look at Patches post in post 22 and 23 here

[http://art.ubuntuforums.org/showthread.php?t=1655602&page=3](http://art.ubuntuforums.org/showthread.php?t=1655602&page=3)

---

### Post by guptasurbhi26 on 2011-01-01
> ashish@ashish:~$ sudo iwconfig eth1 txpower 10
Error for wireless request "Set Tx Power" (8B26) :
    SET failed on device eth1 ; No such device.

does this mean that my wireless is switched off in some weird manner?because my wireless is very much on and my bluetooth is working..

---

### Post by bkratz on 2011-01-01
> **guptasurbhi26 said:**
> does this mean that my wireless is switched off in some weird manner?because my wireless is very much on and my bluetooth is working..

That was how I understood what he said. Anyway, can you post the output of

```
rfkill list
```

if it is not installed then.

```
sudo apt-get install rfkill
```

then rfkill list

and copy paste the output back here.

---

### Post by guptasurbhi26 on 2011-01-01
ok..this is what i got..
> 0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
ashish@ashish:~$ 

---

### Post by guptasurbhi26 on 2011-01-01
Hey..i did rfkill list and it showed that my wlan was harblocked..
so i passed 'rfkill unblock all' on the terminal...and now i can see all the wifi networks in wicd manager.

Guess..its working now..but i've no idea how to do it again next time..lol!i dont even know what all i've been doing for the past 8 hours..to get this thing working..

---

### Post by bkratz on 2011-01-01
> **guptasurbhi26 said:**
> Hey..i did rfkill list and it showed that my wlan was harblocked..
so i passed 'rfkill unblock all' on the terminal...and now i can see all the wifi networks in wicd manager.

Guess..its working now..but i've no idea how to do it again next time..lol!i dont even know what all i've been doing for the past 8 hours..to get this thing working..


Glad you got it going, congratulations.
First, I would get some rest. Then reboot your system and make sure it still works and come back if not. If so, mark the thread as solved with the thread tools above.

---

### Post by guptasurbhi26 on 2011-01-01
> **bkratz said:**
> Glad you got it going, congratulations.
First, I would get some rest. Then reboot your system and make sure it still works and come back if not. If so, mark the thread as solved with the thread tools above.


Damn..i rebooted my system and now i dont see any wifi networks in wicd manager.I then tried passing the same command on the terminal..'rfkill unblock all'..but it didnt work..as in my wlan was still hardblocked.

I switched off my wifi..switched it back on..then tried 'rfkill unblock all'..and this time it worked..
now i see all wifi networks in wicd manager again..

Does this mean i've to keep repeating the same thing everytime i switch on my laptop?

---

