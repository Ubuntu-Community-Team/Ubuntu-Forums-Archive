---
title: "Intel Corporation Centrino Advanced-N 6205 does not work"
date: 2013-03-19
forum: Networking &amp; Wireless
---

### Post by Cyril4133 on 2013-03-19
Hi,


I have no wireless with  my Intel Corporation Centrino Advanced-N 6205. I have tried to reinstall iwlwifi module without success. Network manager says > "Wireless is disable by hardware switch".
And rfkill gives


```
rfkill list1: phy1: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
```


And the command > sudo rfkill unblock all change nothing.

Additional information

```
lspci -v00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
    Subsystem: Lenovo Device 21f3
    Flags: bus master, fast devsel, latency 0
    Capabilities: <access denied>


00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
    I/O behind bridge: 00005000-00005fff
    Memory behind bridge: f0000000-f10fffff
    Prefetchable memory behind bridge: 00000000c0000000-00000000d1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Lenovo Device 21f4
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f1400000 (64-bit, non-prefetchable) [size=4M]
    Memory at e0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 6000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: <access denied>


00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04) (prog-if 30 [XHCI])
    Subsystem: Lenovo Device 21f3
    Flags: bus master, medium devsel, latency 0, IRQ 41
    Memory at f3920000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: <access denied>
    Kernel driver in use: xhci_hcd


00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
    Subsystem: Lenovo Device 21f3
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f3935000 (64-bit, non-prefetchable) [size=16]
    Capabilities: <access denied>


00:16.3 Serial controller: Intel Corporation 7 Series/C210 Series Chipset Family KT Controller (rev 04) (prog-if 02 [16550])
    Subsystem: Lenovo Device 21f3
    Flags: bus master, 66MHz, fast devsel, latency 0, IRQ 19
    I/O ports at 60e0 [size=8]
    Memory at f393b000 (32-bit, non-prefetchable) [size=4K]
    Capabilities: <access denied>
    Kernel driver in use: serial


00:19.0 Ethernet controller: Intel Corporation 82579LM Gigabit Network Connection (rev 04)
    Subsystem: Lenovo Device 21f3
    Flags: bus master, fast devsel, latency 0, IRQ 42
    Memory at f3900000 (32-bit, non-prefetchable) [size=128K]
    Memory at f393a000 (32-bit, non-prefetchable) [size=4K]
    I/O ports at 6060 [size=32]
    Capabilities: <access denied>
    Kernel driver in use: e1000e
    Kernel modules: e1000e


00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 21f3
    Flags: bus master, medium devsel, latency 0, IRQ 16
    Memory at f3939000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd


00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
    Subsystem: Lenovo Device 21f3
    Flags: bus master, fast devsel, latency 0, IRQ 10
    Memory at f3930000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>


00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
    I/O behind bridge: 00004000-00004fff
    Memory behind bridge: f3100000-f38fffff
    Prefetchable memory behind bridge: 00000000f1800000-00000000f1ffffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
    Memory behind bridge: f3000000-f30fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4) (prog-if 00 [Normal decode])
    Flags: bus master, fast devsel, latency 0
    Bus: primary=00, secondary=04, subordinate=0b, sec-latency=0
    I/O behind bridge: 00003000-00003fff
    Memory behind bridge: f2800000-f2ffffff
    Prefetchable memory behind bridge: 00000000f2000000-00000000f27fffff
    Capabilities: <access denied>
    Kernel driver in use: pcieport


00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04) (prog-if 20 [EHCI])
    Subsystem: Lenovo Device 21f3
    Flags: bus master, medium devsel, latency 0, IRQ 23
    Memory at f3938000 (32-bit, non-prefetchable) [size=1K]
    Capabilities: <access denied>
    Kernel driver in use: ehci_hcd


00:1f.0 ISA bridge: Intel Corporation QM77 Express Chipset LPC Controller (rev 04)
    Subsystem: Lenovo Device 21f3
    Flags: bus master, medium devsel, latency 0
    Capabilities: <access denied>


00:1f.2 IDE interface: Intel Corporation 7 Series Chipset Family 4-port SATA Controller [IDE mode] (rev 04) (prog-if 8a [Master SecP PriP])
    Subsystem: Lenovo Device 21f3
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 01f0 [size=8]
    I/O ports at 03f4 [size=1]
    I/O ports at 0170 [size=8]
    I/O ports at 0374 [size=1]
    I/O ports at 60b0 [size=16]
    I/O ports at 60a0 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix


00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
    Subsystem: Lenovo Device 21f3
    Flags: medium devsel, IRQ 7
    Memory at f3934000 (64-bit, non-prefetchable) [size=256]
    I/O ports at efa0 [size=32]


00:1f.5 IDE interface: Intel Corporation 7 Series Chipset Family 2-port SATA Controller [IDE mode] (rev 04) (prog-if 85 [Master SecO PriO])
    Subsystem: Lenovo Device 21f3
    Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 19
    I/O ports at 60c8 [size=8]
    I/O ports at 60ec [size=4]
    I/O ports at 60c0 [size=8]
    I/O ports at 60e8 [size=4]
    I/O ports at 6090 [size=16]
    I/O ports at 6080 [size=16]
    Capabilities: <access denied>
    Kernel driver in use: ata_piix


01:00.0 VGA compatible controller: NVIDIA Corporation GF108 [Quadro NVS 5400M] (rev ff) (prog-if ff)
    !!! Unknown header type 7f


02:00.0 System peripheral: Ricoh Co Ltd PCIe SDXC/MMC Host Controller (rev 07) (prog-if 01)
    Subsystem: Lenovo Device 21f3
    Flags: bus master, fast devsel, latency 0, IRQ 11
    Memory at f3100000 (32-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>


03:00.0 Network controller: Intel Corporation Centrino Advanced-N 6205 (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN
    Flags: bus master, fast devsel, latency 0, IRQ 43
    Memory at f3000000 (64-bit, non-prefetchable) [size=8K]
    Capabilities: <access denied>
    Kernel driver in use: iwlwifi
    Kernel modules: iwlwifi
```


```
lsmodModule                  Size  Used by
lib80211               14382  0 
iwldvm                241894  0 
iwlwifi               165881  1 iwldvm
bbswitch               13469  0 
arc4                   12530  2 
ghash_clmulni_intel    13221  0 
mac80211              549341  1 iwldvm
joydev                 17458  0 
aesni_intel            51038  0 
cryptd                 20404  2 ghash_clmulni_intel,aesni_intel
aes_x86_64             17256  1 aesni_intel
microcode              22804  0 
psmouse                95595  0 
serio_raw              13216  0 
cfg80211              211134  3 iwldvm,iwlwifi,mac80211
video                  19391  0 
bnep                   18141  2 
rfcomm                 42652  4 
bluetooth             205000  8 bnep,rfcomm
compat                 14950  8 lib80211,iwldvm,iwlwifi,mac80211,cfg80211,bnep,rfcomm,bluetooth
parport_pc             32689  0 
ppdev                  17074  0 
binfmt_misc            17501  1 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
e1000e                199273  0 
```
and 
```
sudo lshw -C Network  *-network               
       description: Ethernet interface
       product: 82579LM Gigabit Network Connection
       vendor: Intel Corporation
       physical id: 19
       bus info: pci@0000:00:19.0
       logical name: eth0
       version: 04
       serial: 00:21:cc:da:76:fd
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.0.0-k duplex=full firmware=0.13-3 ip=128.178.152.24 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:42 memory:f3900000-f391ffff memory:f393a000-f393afff ioport:6060(size=32)
  *-network DISABLED
       description: Wireless interface
       product: Centrino Advanced-N 6205
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan0
       version: 34
       serial: 84:3a:4b:3e:fd:c8
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlwifi driverversion=3.5.0-25-generic firmware=18.168.6.1 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
       resources: irq:43 memory:f3000000-f3001fff
```
Thanks

---

### Post by chili555 on 2013-03-19
May we see the entire output of:```
rfkill list all
```What is the effect of pressing the wireless switch or key combination or, as on my Lenovo, both?

---

### Post by Cyril4133 on 2013-03-20
I get the same
> 
rfkill list all0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes




---

### Post by Cyril4133 on 2013-03-20
I have solved my problem by discovering that there was a wireless switch on the right side of my T430-2.

---

### Post by chili555 on 2013-03-20
> **Cyril4133 said:**
> I have solved my problem by discovering that there was a wireless switch on the right side of my T430-2.Glad it's working!

---

