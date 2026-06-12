---
title: "Surface go 2 At&amp;t"
date: 2022-04-10
forum: MINT
---

### Post by t3ckfr3ak on 2022-04-10
I can't for the life of me get my mobile modem to work and I haven't found any articles regarding the issue.

---

### Post by QIII on 2022-04-10
It might be helpful if you would provide some information.

What OS are you running?

What are you doing to try to get it to work?

What do you expect to happen?

What is happening?  (Telling us what is *not* happening is not particularly helpful.)

What have you done so far in trying to make it work as you expect?

---

### Post by t3ckfr3ak on 2022-04-10
I'm sorry

I'm running Mint 20.3
5.16.17-surface kernal
Based on Ubuntu 20.05.5 lts

And honestly all I've done is go to network settings and add an AT&T lte profile in the mobile broadband category 


```
lsusb
Bus 002 Device 002: ID 045e:09a5 Microsoft Corp. Surface
Bus 002 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 001 Device 004: ID 045e:09b5 Microsoft Corp. Surface Keyboard
Bus 001 Device 002: ID 8087:0029 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

In network settings the mobile modem isn't listed and I don't even know where to start here.

---

### Post by t3ckfr3ak on 2022-04-10
```
lspci
00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers (rev 02)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 615 (rev 02)
00:04.0 Signal processing controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem (rev 02)
00:05.0 Multimedia controller: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit (rev 01)
00:13.0 Non-VGA unclassified device: Intel Corporation Sunrise Point-LP Integrated Sensor Hub (rev 21)
00:14.0 USB controller: Intel Corporation Sunrise Point-LP USB 3.0 xHCI Controller (rev 21)
00:14.2 Signal processing controller: Intel Corporation Sunrise Point-LP Thermal subsystem (rev 21)
00:14.3 Multimedia controller: Intel Corporation Device 9d32 (rev 01)
00:15.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #0 (rev 21)
00:15.1 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #1 (rev 21)
00:15.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #2 (rev 21)
00:15.3 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #3 (rev 21)
00:16.0 Communication controller: Intel Corporation Sunrise Point-LP CSME HECI #1 (rev 21)
00:19.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #2 (rev 21)
00:19.2 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO I2C Controller #4 (rev 21)
00:1c.0 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #3 (rev f1)
00:1c.3 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #4 (rev f1)
00:1c.6 PCI bridge: Intel Corporation Sunrise Point-LP PCI Express Root Port #7 (rev f1)
00:1e.0 Signal processing controller: Intel Corporation Sunrise Point-LP Serial IO UART Controller #0 (rev 21)
00:1f.0 ISA bridge: Intel Corporation Device 9d4b (rev 21)
00:1f.2 Memory controller: Intel Corporation Sunrise Point-LP PMC (rev 21)
00:1f.3 Audio device: Intel Corporation Sunrise Point-LP HD Audio (rev 21)
01:00.0 Network controller: Intel Corporation Wi-Fi 6 AX200 (rev 1a)
02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS522A PCI Express Card Reader (rev 01)
03:00.0 Non-Volatile memory controller: KIOXIA Corporation Device 0001
```

---

### Post by t3ckfr3ak on 2022-04-10
```
lshw
WARNING: you should run this program as super-user.
joe-surface-go-2            
    description: Computer
    width: 64 bits
    capabilities: smp vsyscall32
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 8GiB
     *-cpu
          product: Intel(R) Core(TM) m3-8100Y CPU @ 1.10GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          size: 1962MHz
          capacity: 3400MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx pdpe1gb rdtscp x86-64 constant_tsc art arch_perfmon pebs bts rep_good nopl xtopology nonstop_tsc cpuid aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 sdbg fma cx16 xtpr pdcm pcid sse4_1 sse4_2 x2apic movbe popcnt tsc_deadline_timer aes xsave avx f16c rdrand lahf_lm abm 3dnowprefetch cpuid_fault epb invpcid_single pti ssbd ibrs ibpb stibp tpr_shadow vnmi flexpriority ept vpid ept_ad fsgsbase tsc_adjust bmi1 avx2 smep bmi2 erms invpcid mpx rdseed adx smap clflushopt intel_pt xsaveopt xsavec xgetbv1 xsaves dtherm ida arat pln pts hwp hwp_notify hwp_act_window hwp_epp md_clear flush_l1d arch_capabilities cpufreq
     *-pci
          description: Host bridge
          product: Xeon E3-1200 v6/7th Gen Core Processor Host Bridge/DRAM Registers
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=skl_uncore
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: UHD Graphics 615
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:132 memory:b0000000-b0ffffff memory:a0000000-afffffff ioport:3000(size=64) memory:c0000-dffff
        *-generic:0
             description: Signal processing controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Thermal Subsystem
             vendor: Intel Corporation
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=proc_thermal latency=0
             resources: irq:16 memory:b1730000-b1737fff
        *-multimedia:0
             description: Multimedia controller
             product: Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit
             vendor: Intel Corporation
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: driver=ipu3-imgu latency=0
             resources: irq:135 memory:b1000000-b13fffff
        *-generic:1
             description: Non-VGA unclassified device
             product: Sunrise Point-LP Integrated Sensor Hub
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel_ish_ipc latency=0
             resources: irq:20 memory:b1740000-b1740fff
        *-usb
             description: USB controller
             product: Sunrise Point-LP USB 3.0 xHCI Controller
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:126 memory:b1720000-b172ffff
        *-generic:2
             description: Signal processing controller
             product: Sunrise Point-LP Thermal subsystem
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel_pch_thermal latency=0
             resources: irq:18 memory:b1741000-b1741fff
        *-multimedia:1
             description: Multimedia controller
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=ipu3-cio2 latency=32
             resources: irq:134 memory:b1700000-b170ffff
        *-generic:3
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #0
             vendor: Intel Corporation
             physical id: 15
             bus info: pci@0000:00:15.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:16 memory:b1742000-b1742fff
        *-generic:4
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #1
             vendor: Intel Corporation
             physical id: 15.1
             bus info: pci@0000:00:15.1
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:17 memory:b1743000-b1743fff
        *-generic:5
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #2
             vendor: Intel Corporation
             physical id: 15.2
             bus info: pci@0000:00:15.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:18 memory:b1744000-b1744fff
        *-generic:6
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #3
             vendor: Intel Corporation
             physical id: 15.3
             bus info: pci@0000:00:15.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:19 memory:b1745000-b1745fff
        *-communication
             description: Communication controller
             product: Sunrise Point-LP CSME HECI #1
             vendor: Intel Corporation
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=mei_me latency=0
             resources: irq:133 memory:b1746000-b1746fff
        *-generic:7
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO UART Controller #2
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:32 memory:b1747000-b1747fff
        *-generic:8
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO I2C Controller #4
             vendor: Intel Corporation
             physical id: 19.2
             bus info: pci@0000:00:19.2
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:34 memory:b1748000-b1748fff
        *-pci:0
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #3
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:122 memory:b1600000-b16fffff
           *-network
                description: Wireless interface
                product: Wi-Fi 6 AX200
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                logical name: wlp1s0
                version: 1a
                serial: f8:5e:a0:9e:a6:b5
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=5.16.17-surface firmware=66.f1c864e0.0 cc-a0-66.ucode ip=192.168.0.158 latency=0 link=yes multicast=yes wireless=IEEE 802.11
                resources: irq:18 memory:b1600000-b1603fff
        *-pci:1
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:123 memory:b1500000-b15fffff
           *-generic
                description: Unassigned class
                product: RTS522A PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:125 memory:b1500000-b1500fff
        *-pci:2
             description: PCI bridge
             product: Sunrise Point-LP PCI Express Root Port #7
             vendor: Intel Corporation
             physical id: 1c.6
             bus info: pci@0000:00:1c.6
             version: f1
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:124 memory:b1400000-b14fffff
           *-storage
                description: Non-Volatile memory controller
                product: KIOXIA Corporation
                vendor: KIOXIA Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 00
                width: 64 bits
                clock: 33MHz
                capabilities: storage nvm_express bus_master cap_list
                configuration: driver=nvme latency=0
                resources: irq:18 memory:b1400000-b1403fff
              *-nvme0
                   description: NVMe device
                   product: KBG40ZPZ128G BG4A KIOXIA
                   physical id: 0
                   logical name: /dev/nvme0
                   version: AEMS0104
                   serial: 212200KCNDT1
                   configuration: nqn=nqn.2018-06.com.toshiba-memory:KBG40ZPZ128G BG4A KIOXIA:212200KCNDT1 state=live
                 *-namespace
                      description: NVMe namespace
                      physical id: 1
                      logical name: /dev/nvme0n1
        *-generic:9
             description: Signal processing controller
             product: Sunrise Point-LP Serial IO UART Controller #0
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=intel-lpss latency=0
             resources: irq:20 memory:b1749000-b1749fff
        *-isa
             description: ISA bridge
             product: Intel Corporation
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 21
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-memory UNCLAIMED
             description: Memory controller
             product: Sunrise Point-LP PMC
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 21
             width: 32 bits
             clock: 33MHz (30.3ns)
             capabilities: bus_master
             configuration: latency=0
             resources: memory:b173c000-b173ffff
        *-multimedia:2
             description: Audio device
             product: Sunrise Point-LP HD Audio
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 21
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=snd_hda_intel latency=32
             resources: irq:160 memory:b1738000-b173bfff memory:b1710000-b171ffff
     *-pnp00:00
          product: PnP device PNP0c02
          physical id: 2
          capabilities: pnp
          configuration: driver=system
     *-pnp00:01
          product: PnP device PNP0c02
          physical id: 3
          capabilities: pnp
          configuration: driver=system
     *-pnp00:02
          product: PnP device PNP0c02
          physical id: 4
          capabilities: pnp
          configuration: driver=system
     *-pnp00:03
          product: PnP device PNP0c02
          physical id: 5
          capabilities: pnp
          configuration: driver=system
     *-pnp00:04
          product: PnP device PNP0b00
          physical id: 6
          capabilities: pnp
          configuration: driver=rtc_cmos
     *-pnp00:05
          product: PnP device INT3f0d
          vendor: Interphase Corporation
          physical id: 7
          capabilities: pnp
          configuration: driver=system
     *-pnp00:06
          product: PnP device PNP0303
          physical id: 8
          capabilities: pnp
          configuration: driver=i8042 kbd
     *-pnp00:07
          product: PnP device PNP0c02
          physical id: 9
          capabilities: pnp
          configuration: driver=system
     *-pnp00:08
          product: PnP device PNP0c02
          physical id: a
          capabilities: pnp
          configuration: driver=system
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       bus info: usb@2:3
       logical name: wwan0
       serial: 1a:b0:d0:af:ad:b3
       capabilities: ethernet physical
       configuration: autonegotiation=off broadcast=yes driver=cdc_mbim driverversion=5.16.17-surface duplex=half firmware=CDC MBIM link=no multicast=yes port=twisted pair
WARNING: output may be incomplete or inaccurate, you should run this program as super-user.
joe@joe-Surface-Go-2:~$
```

---

### Post by t3ckfr3ak on 2022-04-10
```
System:    Kernel: 5.16.17-surface x86_64 bits: 64 compiler: N/A Desktop: Cinnamon 5.2.7 
           wm: muffin dm: LightDM Distro: Linux Mint 20.3 Una base: Ubuntu 20.04 focal 
Machine:   Type: Laptop System: Microsoft product: Surface Go 2 v: 1 serial: <filter> Chassis: 
           type: 9 serial: <filter> 
           Mobo: Microsoft model: Surface Go 2 serial: <filter> UEFI: Microsoft v: 1.0.17 
           date: 11/17/2021 
Battery:   ID-1: BAT1 charge: 23.3 Wh condition: 25.5/26.9 Wh (95%) volts: 8.3/7.7 model: DYN Uhu 
           serial: <filter> status: Discharging 
           Device-1: hid-0018:04F3:2A1C.0001-battery model: ELAN9038:00 04F3:2A1C serial: N/A 
           charge: N/A status: N/A 
CPU:       Topology: Dual Core model: Intel Core m3-8100Y bits: 64 type: MT MCP arch: Amber Lake 
           rev: 9 L2 cache: 4096 KiB 
           flags: avx avx2 lm nx pae sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx bogomips: 12799 
           Speed: 600 MHz min/max: 400/3400 MHz Core speeds (MHz): 1: 600 2: 600 3: 600 4: 600 
Graphics:  Device-1: Intel UHD Graphics 615 vendor: QUANTA driver: i915 v: kernel bus ID: 00:02.0 
           chip ID: 8086:591c 
           Display: x11 server: X.Org 1.20.13 driver: modesetting unloaded: fbdev,vesa 
           resolution: 1920x1280~60Hz 
           OpenGL: renderer: Mesa Intel UHD Graphics 615 (AML-KBL) v: 4.6 Mesa 21.2.6 
           direct render: Yes 
Audio:     Device-1: Intel Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor Imaging Unit 
           vendor: QUANTA driver: ipu3-imgu bus ID: 00:05.0 chip ID: 8086:1919 
           Device-2: Intel driver: ipu3-cio2 bus ID: 00:14.3 chip ID: 8086:9d32 
           Device-3: Intel Sunrise Point-LP HD Audio vendor: QUANTA driver: snd_hda_intel 
           v: kernel bus ID: 00:1f.3 chip ID: 8086:9d71 
           Sound Server: ALSA v: k5.16.17-surface 
Network:   Device-1: Intel Wi-Fi 6 AX200 driver: iwlwifi v: kernel port: 3000 bus ID: 01:00.0 
           chip ID: 8086:2723 
           IF: wlp1s0 state: up mac: <filter> 
           IF-ID-1: wwan0 state: down mac: <filter> 
Drives:    Local Storage: total: 119.24 GiB used: 9.60 GiB (8.0%) 
           ID-1: /dev/nvme0n1 model: KBG40ZPZ128G BG4A KIOXIA size: 119.24 GiB speed: 31.6 Gb/s 
           lanes: 4 serial: <filter> 
Partition: ID-1: / size: 116.38 GiB used: 9.59 GiB (8.2%) fs: ext4 dev: /dev/nvme0n1p2 
Sensors:   System Temperatures: cpu: 36.0 C mobo: N/A 
           Fan Speeds (RPM): N/A 
Repos:     Active apt repos in: /etc/apt/sources.list 
           1: deb http: //http.kali.org/kali kali-rolling main contrib non-free
           2: deb http: //http.kali.org/kali kali-rolling main contrib non-free
           Active apt repos in: /etc/apt/sources.list.d/diesch-testing-focal.list 
           1: deb http: //ppa.launchpad.net/diesch/testing/ubuntu focal main
           Active apt repos in: /etc/apt/sources.list.d/linux-surface.list 
           1: deb [arch=amd64] https: //pkg.surfacelinux.com/debian release main
           Active apt repos in: /etc/apt/sources.list.d/official-package-repositories.list 
           1: deb http: //packages.linuxmint.com una main upstream import backport #id:linuxmint_main
           2: deb http: //archive.ubuntu.com/ubuntu focal main restricted universe multiverse
           3: deb http: //archive.ubuntu.com/ubuntu focal-updates main restricted universe multiverse
           4: deb http: //archive.ubuntu.com/ubuntu focal-backports main restricted universe multiverse
           5: deb http: //security.ubuntu.com/ubuntu/ focal-security main restricted universe multiverse
           6: deb http: //archive.canonical.com/ubuntu/ focal partner
           Active apt repos in: /etc/apt/sources.list.d/tj-bugfixes-focal.list 
           1: deb http: //ppa.launchpad.net/tj/bugfixes/ubuntu focal main
Info:      Processes: 236 Uptime: 23m Memory: 7.64 GiB used: 2.41 GiB (31.6%) Init: systemd v: 245 
           runlevel: 5 Compilers: gcc: 9.4.0 alt: 9 Client: Unknown python3.8 client inxi: 3.0.38
```

---

### Post by wildmanne39 on 2022-04-11
Hello t3ckfr3ak, in the future please post all your terminal output in the same post and wrap the output between code tags.

Thanks

---

### Post by coffeecat on 2022-04-11
> **t3ckfr3ak said:**
> I'm running Mint 20.3
5.16.17-surface kernal

*Thread moved to **Mint** sub-forum.*

---

