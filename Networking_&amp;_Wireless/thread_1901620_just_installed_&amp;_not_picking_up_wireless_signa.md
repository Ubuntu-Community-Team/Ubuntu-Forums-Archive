---
title: "just installed &amp; not picking up wireless signals"
date: 2011-12-28
forum: Networking &amp; Wireless
---

### Post by longdraw on 2011-12-28
just installed 11.10 its not picking up wireless networks. it did when i was running alongside windows,just went live and nothing. i had to manually input my network and it even says it connects but still cant access internet. after running command lshw i get warning: output may be incomplete or inaccurate,you should run this program as super-user...dont know if this has anything to do with my problem ,also i get configuration:driver=k8temp
thanks

---

### Post by 2F4U on 2011-12-29
It would certainly help if you could post the output of lshw or otherwise provide some hardware specs.

---

### Post by longdraw on 2011-12-31
update:still cant access wirelessly. internet access with hardline only.my wireless signal is the only one the laptop sees and its only there because i inputed it manualy.its connects,even says it connected but im not online.
here is the lshw output:

pgwilde@pgwilde-Aspire-5520:~$ lshw
WARNING: you should run this program as super-user.
pgwilde-aspire-5520       
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory:0
          description: System memory
          physical id: 3
          size: 1760MiB
     *-cpu
          product: AMD Turion(tm) 64 X2 Mobile Technology TL-58
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 5
          bus info: cpu@0
          version: 15.8.1
          size: 1800MHz
          capacity: 1800MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt rdtscp x86-64 3dnowext 3dnow extd_apicid pni cx16 lahf_lm cmp_legacy svm extapic cr8_legacy 3dnowprefetch lbrv cpufreq
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KiB
     *-memory:1 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 0
          bus info: pci@0000:00:00.0
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          capabilities: bus_master cap_list
          configuration: latency=0
     *-isa
          description: ISA bridge
          product: MCP67 ISA Bridge
          vendor: nVidia Corporation
          physical id: 1
          bus info: pci@0000:00:01.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: isa bus_master
          configuration: latency=0
          resources: ioport:1d00(size=256)
     *-serial
          description: SMBus
          product: MCP67 SMBus
          vendor: nVidia Corporation
          physical id: 1.1
          bus info: pci@0000:00:01.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: cap_list
          configuration: driver=nForce2_smbus latency=0
          resources: irq:10 ioport:3080(size=64) ioport:3040(size=64) ioport:3000(size=64)
     *-memory:2 UNCLAIMED
          description: RAM memory
          product: MCP67 Memory Controller
          vendor: nVidia Corporation
          physical id: 1.2
          bus info: pci@0000:00:01.2
          version: a2
          width: 32 bits
          clock: 66MHz (15.2ns)
          configuration: latency=0
     *-processor UNCLAIMED
          description: Co-processor
          product: MCP67 Co-processor
          vendor: nVidia Corporation
          physical id: 1.3
          bus info: pci@0000:00:01.3
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master
          configuration: latency=0 maxlatency=1 mingnt=3
          resources: memory:f2400000-f247ffff
     *-usb:0
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 2
          bus info: pci@0000:00:02.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:20 memory:f2686000-f2686fff
     *-usb:1
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 2.1
          bus info: pci@0000:00:02.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:22 memory:f2689000-f26890ff
     *-usb:2
          description: USB Controller
          product: MCP67 OHCI USB 1.1 Controller
          vendor: nVidia Corporation
          physical id: 4
          bus info: pci@0000:00:04.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=ohci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:23 memory:f2687000-f2687fff
     *-usb:3
          description: USB Controller
          product: MCP67 EHCI USB 2.0 Controller
          vendor: nVidia Corporation
          physical id: 4.1
          bus info: pci@0000:00:04.1
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=0 maxlatency=1 mingnt=3
          resources: irq:21 memory:f2689400-f26894ff
     *-ide:0
          description: IDE interface
          product: MCP67 IDE Controller
          vendor: nVidia Corporation
          physical id: 6
          bus info: pci@0000:00:06.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=pata_amd latency=0 maxlatency=1 mingnt=3
          resources: irq:0 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:30c0(size=16)
     *-multimedia
          description: Audio device
          product: MCP67 High Definition Audio
          vendor: nVidia Corporation
          physical id: 7
          bus info: pci@0000:00:07.0
          version: a1
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list
          configuration: driver=HDA Intel latency=0 maxlatency=5 mingnt=2
          resources: irq:21 memory:f2680000-f2683fff
     *-pci:0
          description: PCI bridge
          product: MCP67 PCI Bridge
          vendor: nVidia Corporation
          physical id: 8
          bus info: pci@0000:00:08.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: pci subtractive_decode bus_master cap_list
          resources: memory:f2300000-f23fffff
        *-firewire
             description: FireWire (IEEE 1394)
             product: R5C832 IEEE 1394 Controller
             vendor: Ricoh Co Ltd
             physical id: 4
             bus info: pci@0000:01:04.0
             version: 05
             width: 32 bits
             clock: 33MHz
             capabilities: ohci bus_master cap_list
             configuration: driver=firewire_ohci latency=64 maxlatency=4 mingnt=2
             resources: irq:11 memory:f2300000-f23007ff
        *-generic:0
             description: SD Host controller
             product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 4.1
             bus info: pci@0000:01:04.1
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=sdhci-pci latency=64
             resources: irq:11 memory:f2300800-f23008ff
        *-generic:1
             description: System peripheral
             product: R5C592 Memory Stick Bus Host Adapter
             vendor: Ricoh Co Ltd
             physical id: 4.2
             bus info: pci@0000:01:04.2
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=r592 latency=64
             resources: irq:11 memory:f2300c00-f2300cff
        *-generic:2
             description: System peripheral
             product: xD-Picture Card Controller
             vendor: Ricoh Co Ltd
             physical id: 4.3
             bus info: pci@0000:01:04.3
             version: 12
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=r852 latency=64
             resources: irq:11 memory:f2301000-f23010ff
     *-ide:1
          description: IDE interface
          product: MCP67 AHCI Controller
          vendor: nVidia Corporation
          physical id: 9
          bus info: pci@0000:00:09.0
          version: a2
          width: 32 bits
          clock: 66MHz
          capabilities: ide bus_master cap_list
          configuration: driver=ahci latency=0 maxlatency=1 mingnt=3
          resources: irq:23 ioport:30f0(size=8) ioport:30e4(size=4) ioport:30e8(size=8) ioport:30e0(size=4) ioport:30d0(size=16) memory:f2684000-f2685fff
     *-network
          description: Ethernet interface
          product: MCP67 Ethernet
          vendor: nVidia Corporation
          physical id: a
          bus info: pci@0000:00:0a.0
          logical name: eth0
          version: a2
          serial: 00:1b:38:5d:27:d3
          size: 100Mbit/s
          capacity: 1Gbit/s
          width: 32 bits
          clock: 66MHz
          capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
          configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.2.3 latency=0 maxlatency=20 mingnt=1 multicast=yes port=MII speed=100Mbit/s
          resources: irq:42 memory:f2688000-f2688fff ioport:30f8(size=8) memory:f2689c00-f2689cff memory:f2689800-f268980f
     *-pci:1
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: c
          bus info: pci@0000:00:0c.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:40 ioport:4000(size=4096) memory:f2000000-f21fffff ioport:f2800000(size=2097152)
     *-pci:2
          description: PCI bridge
          product: MCP67 PCI Express Bridge
          vendor: nVidia Corporation
          physical id: d
          bus info: pci@0000:00:0d.0
          version: a2
          width: 32 bits
          clock: 33MHz
          capabilities: pci normal_decode bus_master cap_list
          configuration: driver=pcieport
          resources: irq:41 memory:f2200000-f22fffff
        *-network
             description: Wireless interface
             product: AR242x / AR542x Wireless Network Adapter (PCI-Express)
             vendor: Atheros Communications Inc.
             physical id: 0
             bus info: pci@0000:05:00.0
             logical name: wlan0
             version: 01
             serial: 00:1d:d9:27:41:d1
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical wireless
             configuration: broadcast=yes driver=ath5k driverversion=3.0.0-14-generic firmware=N/A ip=10.42.43.1 latency=0 multicast=yes wireless=IEEE 802.11bg
             resources: irq:19 memory:f2200000-f220ffff
     *-display
          description: VGA compatible controller
          product: C67 [GeForce 7000M / nForce 610M]
          vendor: nVidia Corporation
          physical id: 12
          bus info: pci@0000:00:12.0
          version: a2
          width: 64 bits
          clock: 66MHz
          capabilities: vga_controller bus_master cap_list rom
          configuration: driver=nouveau latency=0
          resources: irq:17 memory:f1000000-f1ffffff memory:d0000000-dfffffff memory:f0000000-f0ffffff memory:80000000-8001ffff
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 100
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 101
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 102
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Hynix Semiconductor (Hyundai Electronics)
          physical id: 103
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
pgwilde@pgwilde-Aspire-5520:~$ ^C
pgwilde@pgwilde-Aspire-5520:~$

---

### Post by praseodym on 2011-12-31
Hi,

with the driver ath5k you need to deactivate its hardware encryption:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```
Check after that:
```
lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | egrep 'ath|country'
```

---

### Post by r00tr4t on 2012-02-17
> **praseodym said:**
> Hi,

with the driver ath5k you need to deactivate its hardware encryption:

```
echo "options ath5k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```Check after that:
```
lsmod
iwconfig
sudo iwlist scan
rfkill list
dmesg | egrep 'ath|country'
```
 
Thanks this info saved my day :)
Just one suggestion after the last modprobe command the wlan0 interface is down.
Change that by ```
sudo ifconfig wlan0 up
```:KSThanks! :KS

---

