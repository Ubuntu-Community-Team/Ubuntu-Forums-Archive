---
title: "About to give up on 16"
date: 2017-04-30
forum: Multimedia Software
---

### Post by benlyboy on 2017-04-30
Hi all.

I’m out of ideas.

I've been using three dell inspiron 3500 micro desktop (is intel based with intel hd video)as myth front ends, and they worked great, they were all rock solid for almost two years. then after a problem with my back end I decided to update the whole system to 16.04. Big mistake. I have been fighting them ever since. there seem to work fine, but after about two or so hours (its very unpredictable some nights they will work all night no problems, other nights it can happen two or even three times in a hour) they will freeze, all you can do at that point is a hard shut down. I even took one and tried loading a desk top version lubuntu 16.10 and then installed myth front end. it does exactly the something. 
se
I'm just about to give up and see if I can reinstall a version 14.04

Any one have any ideas be for I do?

---

### Post by TheFu on 2017-04-30
I never move my media center systems forward quickly.  I always have a back out plan.  When things go badly, they tend to go really badly, IME.  I used to update every 3 months and was getting burned more often than I liked.  Now before I update, I have a know-I-can-restore backup PRIOR to do any update, then do the update/patching.  I'm on 14.04 with no plans to move to 16 or 18 at this point for those machines.  Heck, just moved off my last 12.04 box today.

Newer isn't always better, though sometimes it is.  

One of my media center machines had an old Radeon GPU, so when that support was dropped, I moved to a different system completely.  Planned to make that box useful for some other purpose, but ran into physical expansion slot issues, so it has been unused since that time. It was a $99 special, so not really a terrible loss.

At least that has been my experience.

It really is amazing what can be accomplished with R-pi for front-ends/players teamed with a $120 system for the backend/storage center.

---

### Post by walterav on 2017-05-04
Guessing what hardware/drivers are related to your problem is not a good start, please post the output of the following terminal commands and if its the frontend dell 3500 (is this a Pentium II?) or backend server PC:

```

uname -a #shows kernel version

glxinfo | grep "OpenGL version" #shows mesa/opengl version 

vainfo #shows GPU related videofeatures, might apt-get vainfo first

cat /proc/cpuinfo #shows cpu

lspci -nn #shows hardware info




```

Further guessing of hard lockups brings me to video acceleration and cpu throttling, If you happen to have a Intel baytrail CPU family which cpu throttling was the cause of random lockups in my situation.

[https://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail](https://www.phoronix.com/scan.php?page=news_item&px=Intel-Linux-Bay-Trail-Fail)

---

### Post by TheFu on 2017-05-04
If we are going after hardware AND drivers, the **sudo lshw** command would be helpful. It provides the chips, cards, and the current drivers.  Don't assume that all three machines have the same hardware, even if that was the claim.

If I were starting new, I'd load 16.04.0 and work from that.  I would **not** move to 16.04.1, before LTS support has been announced for it. I looked last week and it hadn't.

---

### Post by benlyboy on 2017-05-04
Thanks for the help

below is the info you asked for.


 uname -a #shows kernel version
```

Linux frontendlivingroom 4.4.0-21-generic #37-Ubuntu SMP Mon Apr 18 18:34:49 UTC 2016 i686 i686 i686 GNU/Linux

```


 glxinfo | grep "OpenGL version" #shows mesa/opengl version 
```

OpenGL version string: 3.0 Mesa 11.2.0

```



vainfo #shows GPU related videofeatures, might apt-get vainfo girst
```

libva info: VA-API version 0.39.0
libva info: va_getDriverName() returns 0
libva info: Trying to open /usr/lib/i386-linux-gnu/dri/i965_drv_video.so
libva info: Found init function __vaDriverInit_0_39
libva info: va_openDriver() returns 0
vainfo: VA-API version: 0.39 (libva 1.7.0)
vainfo: Driver version: Intel i965 driver for Intel(R) Bay Trail - 1.7.0
vainfo: Supported profile and entrypoints
      VAProfileMPEG2Simple            :	VAEntrypointVLD
      VAProfileMPEG2Simple            :	VAEntrypointEncSlice
      VAProfileMPEG2Main              :	VAEntrypointVLD
      VAProfileMPEG2Main              :	VAEntrypointEncSlice
      VAProfileH264ConstrainedBaseline:	VAEntrypointVLD
      VAProfileH264ConstrainedBaseline:	VAEntrypointEncSlice
      VAProfileH264Main               :	VAEntrypointVLD
      VAProfileH264Main               :	VAEntrypointEncSlice
      VAProfileH264High               :	VAEntrypointVLD
      VAProfileH264High               :	VAEntrypointEncSlice
      VAProfileH264StereoHigh         :	VAEntrypointVLD
      VAProfileVC1Simple              :	VAEntrypointVLD
      VAProfileVC1Main                :	VAEntrypointVLD
      VAProfileVC1Advanced            :	VAEntrypointVLD
      VAProfileNone                   :	VAEntrypointVideoProc
      VAProfileJPEGBaseline           :	VAEntrypointVLD

```




cat /proc/cpuinfo #shows cpu
```


processor	: 0
vendor_id	: GenuineIntel
cpu family	: 6
model		: 55
model name	: Intel(R) Celeron(R) CPU  J1800  @ 2.41GHz
stepping	: 8
microcode	: 0x831
cpu MHz		: 1766.386
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 0
cpu cores	: 2
apicid		: 0
initial apicid	: 0
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat
bugs		:
bogomips	: 4825.60
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

processor	: 1
vendor_id	: GenuineIntel
cpu family	: 6
model		: 55
model name	: Intel(R) Celeron(R) CPU  J1800  @ 2.41GHz
stepping	: 8
microcode	: 0x831
cpu MHz		: 1334.202
cache size	: 1024 KB
physical id	: 0
siblings	: 2
core id		: 1
cpu cores	: 2
apicid		: 2
initial apicid	: 2
fdiv_bug	: no
f00f_bug	: no
coma_bug	: no
fpu		: yes
fpu_exception	: yes
cpuid level	: 11
wp		: yes
flags		: fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp lm constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat
bugs		:
bogomips	: 4825.60
clflush size	: 64
cache_alignment	: 64
address sizes	: 36 bits physical, 48 bits virtual
power management:

```



lspci -nn #shows hardware info
```

00:00.0 Host bridge [0600]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register [8086:0f00] (rev 0e)
00:02.0 VGA compatible controller [0300]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Graphics & Display [8086:0f31] (rev 0e)
00:13.0 SATA controller [0106]: Intel Corporation Atom Processor E3800 Series SATA AHCI Controller [8086:0f23] (rev 0e)
00:14.0 USB controller [0c03]: Intel Corporation Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI [8086:0f35] (rev 0e)
00:1a.0 Encryption controller [1080]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine [8086:0f18] (rev 0e)
00:1b.0 Audio device [0403]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller [8086:0f04] (rev 0e)
00:1c.0 PCI bridge [0604]: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 1 [8086:0f48] (rev 0e)
00:1c.1 PCI bridge [0604]: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 2 [8086:0f4a] (rev 0e)
00:1c.2 PCI bridge [0604]: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 3 [8086:0f4c] (rev 0e)
00:1c.3 PCI bridge [0604]: Intel Corporation Atom Processor E3800 Series PCI Express Root Port 4 [8086:0f4e] (rev 0e)
00:1f.0 ISA bridge [0601]: Intel Corporation Atom Processor Z36xxx/Z37xxx Series Power Control Unit [8086:0f1c] (rev 0e)
00:1f.3 SMBus [0c05]: Intel Corporation Atom Processor E3800 Series SMBus Controller [8086:0f12] (rev 0e)
02:00.0 Network controller [0280]: Intel Corporation Wireless 3160 [8086:08b3] (rev 83)
03:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5229 PCI Express Card Reader [10ec:5229] (rev 01)
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0c)

```




sudo lshw
```

[sudo] password for graham: 
frontendlivingroom        
    description: Computer
    product: DELL
    vendor: AS09
    width: 32 bits
    capabilities: smbios-2.8 smp-1.4 smp
    configuration: cpus=2
  *-core
       description: Motherboard
       physical id: 0
     *-cpu:0
          product: Intel(R) Celeron(R) CPU  J1800  @ 2.41GHz
          vendor: Intel Corp.
          physical id: 0
          bus info: cpu@0
          version: 6.7.8
          serial: 0003-0678-0000-0000-0000-0000
          size: 2582MHz
          capacity: 2582MHz
          width: 64 bits
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx rdtscp x86-64 constant_tsc arch_perfmon pebs bts xtopology nonstop_tsc aperfmperf pni pclmulqdq dtes64 monitor ds_cpl vmx est tm2 ssse3 cx16 xtpr pdcm sse4_1 sse4_2 movbe popcnt tsc_deadline_timer rdrand lahf_lm 3dnowprefetch epb tpr_shadow vnmi flexpriority ept vpid tsc_adjust smep erms dtherm ida arat cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             width: 64 bits
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             width: 64 bits
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             width: 64 bits
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             width: 64 bits
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             width: 64 bits
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             width: 64 bits
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             width: 64 bits
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             width: 64 bits
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             width: 64 bits
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             width: 64 bits
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             width: 64 bits
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             width: 64 bits
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             width: 64 bits
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             width: 64 bits
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             width: 64 bits
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             width: 64 bits
             capabilities: logical
     *-cpu:1
          physical id: 1
          bus info: cpu@1
          version: 6.7.8
          serial: 0003-0678-0000-0000-0000-0000
          size: 2582MHz
          capacity: 2582MHz
          capabilities: vmx ht cpufreq
          configuration: id=0
        *-logicalcpu:0
             description: Logical CPU
             physical id: 0.1
             capabilities: logical
        *-logicalcpu:1
             description: Logical CPU
             physical id: 0.2
             capabilities: logical
        *-logicalcpu:2
             description: Logical CPU
             physical id: 0.3
             capabilities: logical
        *-logicalcpu:3
             description: Logical CPU
             physical id: 0.4
             capabilities: logical
        *-logicalcpu:4
             description: Logical CPU
             physical id: 0.5
             capabilities: logical
        *-logicalcpu:5
             description: Logical CPU
             physical id: 0.6
             capabilities: logical
        *-logicalcpu:6
             description: Logical CPU
             physical id: 0.7
             capabilities: logical
        *-logicalcpu:7
             description: Logical CPU
             physical id: 0.8
             capabilities: logical
        *-logicalcpu:8
             description: Logical CPU
             physical id: 0.9
             capabilities: logical
        *-logicalcpu:9
             description: Logical CPU
             physical id: 0.a
             capabilities: logical
        *-logicalcpu:10
             description: Logical CPU
             physical id: 0.b
             capabilities: logical
        *-logicalcpu:11
             description: Logical CPU
             physical id: 0.c
             capabilities: logical
        *-logicalcpu:12
             description: Logical CPU
             physical id: 0.d
             capabilities: logical
        *-logicalcpu:13
             description: Logical CPU
             physical id: 0.e
             capabilities: logical
        *-logicalcpu:14
             description: Logical CPU
             physical id: 0.f
             capabilities: logical
        *-logicalcpu:15
             description: Logical CPU
             physical id: 0.10
             capabilities: logical
     *-memory
          description: System memory
          physical id: 2
          size: 1897MiB
     *-pci
          description: Host bridge
          product: Atom Processor Z36xxx/Z37xxx Series SoC Transaction Register
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0e
          width: 32 bits
          clock: 33MHz
          configuration: driver=iosf_mbi_pci
          resources: irq:0
        *-display
             description: VGA compatible controller
             product: Atom Processor Z36xxx/Z37xxx Series Graphics & Display
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:91 memory:d0000000-d03fffff memory:c0000000-cfffffff ioport:f080(size=8)
        *-storage
             description: SATA controller
             product: Atom Processor E3800 Series SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 0e
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:88 ioport:f070(size=8) ioport:f060(size=4) ioport:f050(size=8) ioport:f040(size=4) ioport:f020(size=32) memory:d0915000-d09157ff
        *-usb
             description: USB controller
             product: Atom Processor Z36xxx/Z37xxx, Celeron N2000 Series USB xHCI
             vendor: Intel Corporation
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi xhci bus_master cap_list
             configuration: driver=xhci_hcd latency=0
             resources: irq:87 memory:d0900000-d090ffff
           *-usbhost:0
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 0
                bus info: usb@2
                logical name: usb2
                version: 4.04
                capabilities: usb-3.00
                configuration: driver=hub slots=1 speed=5000Mbit/s
           *-usbhost:1
                product: xHCI Host Controller
                vendor: Linux 4.4.0-21-generic xhci-hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 4.04
                capabilities: usb-2.00
                configuration: driver=hub slots=6 speed=480Mbit/s
              *-usb:0
                   description: Keyboard
                   product: USB Receiver
                   vendor: Logitech
                   physical id: 1
                   bus info: usb@1:1
                   version: 29.00
                   capabilities: usb-2.00
                   configuration: driver=usbhid maxpower=98mA speed=12Mbit/s
              *-usb:1
                   description: Bluetooth wireless interface
                   vendor: Intel Corp.
                   physical id: 3
                   bus info: usb@1:3
                   version: 0.01
                   capabilities: bluetooth usb-2.00
                   configuration: driver=btusb maxpower=100mA speed=12Mbit/s
              *-usb:2
                   description: USB hub
                   product: USB2.0 Hub
                   vendor: Genesys Logic, Inc.
                   physical id: 4
                   bus info: usb@1:4
                   version: 88.30
                   capabilities: usb-2.00
                   configuration: driver=hub maxpower=100mA slots=4 speed=480Mbit/s
        *-generic
             description: Encryption controller
             product: Atom Processor Z36xxx/Z37xxx Series Trusted Execution Engine
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=mei_txe latency=0
             resources: irq:92 memory:d0500000-d05fffff memory:d0400000-d04fffff
        *-multimedia
             description: Audio device
             product: Atom Processor Z36xxx/Z37xxx Series High Definition Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 0e
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:94 memory:d0910000-d0913fff
        *-pci:0
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:16 ioport:1000(size=4096) memory:80000000-801fffff ioport:80200000(size=2097152)
        *-pci:1
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:17 ioport:2000(size=4096) memory:d0800000-d08fffff ioport:80400000(size=2097152)
           *-network
                description: Wireless interface
                product: Wireless 3160
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wlp2s0
                version: 83
                serial: e4:f8:9c:5c:c6:41
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwlwifi driverversion=4.4.0-21-generic firmware=16.242414.0 ip=192.168.1.224 latency=0 link=yes multicast=yes wireless=IEEE 802.11abgn
                resources: irq:93 memory:d0800000-d0801fff
        *-pci:2
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:18 ioport:3000(size=4096) memory:d0700000-d07fffff ioport:80600000(size=2097152)
           *-generic
                description: Unassigned class
                product: RTS5229 PCI Express Card Reader
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: driver=rtsx_pci latency=0
                resources: irq:89 memory:d0700000-d0700fff
        *-pci:3
             description: PCI bridge
             product: Atom Processor E3800 Series PCI Express Root Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:19 ioport:e000(size=4096) memory:d0600000-d06fffff ioport:80800000(size=2097152)
           *-network
                description: Ethernet interface
                product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:04:00.0
                logical name: enp4s0
                version: 0c
                serial: 74:e6:e2:e0:a2:1c
                size: 10Mbit/s
                capacity: 1Gbit/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8168g-2_0.0.1 02/06/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
                resources: irq:90 ioport:e000(size=256) memory:d0604000-d0604fff memory:d0600000-d0603fff
        *-isa
             description: ISA bridge
             product: Atom Processor Z36xxx/Z37xxx Series Power Control Unit
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-serial UNCLAIMED
             description: SMBus
             product: Atom Processor E3800 Series SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 0e
             width: 32 bits
             clock: 33MHz
             capabilities: pm cap_list
             configuration: latency=0
             resources: memory:d0914000-d091401f ioport:f000(size=32)
     *-scsi
          physical id: 3
          logical name: scsi1
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: LITEON CS1-SP32-
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/sda
             version: 10A
             serial: TW07FM7R5508553N3207
             size: 29GiB (32GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 logicalsectorsize=512 sectorsize=512 signature=709320db
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@1:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: afdf534d-5b10-4466-ae79-765e800a650f
                size: 27GiB
                capacity: 27GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink extents ext4 ext2 initialized
                configuration: created=2017-05-04 20:17:09 filesystem=ext4 lastmountpoint=/target modified=2017-05-04 20:25:53 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2017-05-04 20:17:12 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@1:0.0.0,2
                logical name: /dev/sda2
                size: 1928MiB
                capacity: 1928MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 1928MiB
                   capabilities: nofs

```

 other info you need please let me know
thanks again

---

### Post by TheFu on 2017-05-04
If you could please change/edit the 'quote' into 'code' tags, that would help make it readable.  Things will line up better.

My chromebook uses i915 video drivers.  When running full screen video, it locks up all the time after a few minutes. If I keep the video windowed, it only locks up once a week. Cannot ssh into the machine from any other machines on the network here, so the entire OS is locked, not just the video/screen inputs. It doesn't matter if I'm using mplayer, kodi, or a full-screen web-browser showing video.  They all lock up.  So ... I pulled the latest drivers from Intel (against my better judgment) and gave them a try for a few hours. It was worse.  The system logs showed the issue was in the video drivers (had to boot from alternate media to see the logs without the next boot trashing them). Removed the direct-from-intel iGP driver, back to the default included video driver.  The devil you know is better than the devil you don't know, right?

My CPU is a Core i3 5015U - kinda need to know the CPU to know the HD-iGP i915 involved.

Of course, none of this helps solve the issue, but if you could try to ssh in when the system appears locked, we'd know if it was just GUI or the entire system.  Also, if you could look at the logs after a crash (boot from alternate media), then we'd have some more facts.

---

### Post by benlyboy on 2017-05-05
Don't have time to edit my post this morning but will do it tonight. I believe that it's more than the GUI that's locking up for two reasons.
  One is that when it's working you can just hit the power button to start a shutdown, but when it's locked up I have to do a hard shut down, 
The other reason is I noticed once that when it locks up it drops off the network.

Thanks for the help

---

### Post by vasa1 on 2017-05-05
> **benlyboy said:**
> Don't have time to edit my post this morning but will do it tonight. ...
I think I've done that for you. As TheFu says, code tags ensure that a fixed width font is used and that the output here is very much like what you see in your terminal all columns nicely aligned. With quote tags, terminal output may not look pretty.
Code tags:```
04:38 PM /boot $ ll
total 98924
-rw-r--r-- 1 root root  1246246 Apr 20 17:32 abi-4.4.0-75-generic
-rw-r--r-- 1 root root  1246313 Apr 26 16:00 abi-4.4.0-77-generic
-rw-r--r-- 1 root root   190214 Apr 20 17:32 config-4.4.0-75-generic
-rw-r--r-- 1 root root   190355 Apr 26 16:00 config-4.4.0-77-generic
drwxr-xr-x 3 root root     4096 Apr  6  2016 extlinux/
drwxr-xr-x 5 root root     4096 May  5 10:04 grub/
-rw-r--r-- 1 root root 37950635 Apr 28 06:26 initrd.img-4.4.0-75-generic
-rw-r--r-- 1 root root 37951911 May  2 06:42 initrd.img-4.4.0-77-generic
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3883390 Apr 20 17:32 System.map-4.4.0-75-generic
-rw------- 1 root root  3883390 Apr 26 16:00 System.map-4.4.0-77-generic
-rw------- 1 root root  7081872 Apr 20 17:32 vmlinuz-4.4.0-75-generic
-rw------- 1 root root  7081808 Apr 26 16:00 vmlinuz-4.4.0-77-generic
04:38 PM /boot $ 

```
Quote tags:> 04:38 PM /boot $ ll
total 98924
-rw-r--r-- 1 root root  1246246 Apr 20 17:32 abi-4.4.0-75-generic
-rw-r--r-- 1 root root  1246313 Apr 26 16:00 abi-4.4.0-77-generic
-rw-r--r-- 1 root root   190214 Apr 20 17:32 config-4.4.0-75-generic
-rw-r--r-- 1 root root   190355 Apr 26 16:00 config-4.4.0-77-generic
drwxr-xr-x 3 root root     4096 Apr  6  2016 extlinux/
drwxr-xr-x 5 root root     4096 May  5 10:04 grub/
-rw-r--r-- 1 root root 37950635 Apr 28 06:26 initrd.img-4.4.0-75-generic
-rw-r--r-- 1 root root 37951911 May  2 06:42 initrd.img-4.4.0-77-generic
-rw-r--r-- 1 root root   182704 Jan 28  2016 memtest86+.bin
-rw-r--r-- 1 root root   184380 Jan 28  2016 memtest86+.elf
-rw-r--r-- 1 root root   184840 Jan 28  2016 memtest86+_multiboot.bin
-rw------- 1 root root  3883390 Apr 20 17:32 System.map-4.4.0-75-generic
-rw------- 1 root root  3883390 Apr 26 16:00 System.map-4.4.0-77-generic
-rw------- 1 root root  7081872 Apr 20 17:32 vmlinuz-4.4.0-75-generic
-rw------- 1 root root  7081808 Apr 26 16:00 vmlinuz-4.4.0-77-generic
04:38 PM /boot $ 


---

### Post by benlyboy on 2017-05-05
If you could tell me what log files you would like and where to find them I'll be happy to copy them after the next crash.

Thanks again for the help

---

### Post by TheFu on 2017-05-05
There are lots of logs. I'd look through all of them using **grep**.  They are in /var/log/ and sometimes in directories below that.  [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles) tries to explain more.

[CENTER]I'm not interested in looking at complete log files.  [/CENTER]

YOU should look through them for problem areas that seem related to the lockups and only post 10-20 lines above the issue.

I'd work backwards from the last entry (bottom of each file).  Be certain to boot from alternate media so the new boot doesn't overwrite the old logs.  Normally for HW stuff, **dmesg** is really helpful.  Get a feel for what is normal, before any lockup by running it now.

---

### Post by walterav on 2017-05-06
@benlyboy

This is the "first" cause of your lockup/freeze problems!

```

model name	: Intel(R) Celeron(R) CPU  J1800  @ 2.41GHz
Linux 4.4.0-21-generic

```

You happen to have a intel Bay Trail(Fail) processor which I assumed earlier. Since you are using a newer kernel than Ubuntu 14.04 (3.x) and now 16.04 uses 4.4.x you are prone to hard freezes(which I also had)! Did you read the Phoronix link I posted earlier and tried to add the following "intel_idle.max_cstate=1" to your "/etc/default/grub" boot kernel parameter?

```

sudo nano /etc/default/grub
#change the following line
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
#into this
GRUB_CMDLINE_LINUX_DEFAULT="intel_idle.max_cstate=1 quiet splash"
#Press CTRL + X and Press Y to save changes to file
sudo update-grub2
#reboot

```

The "second" cause is assisted video playback, newer kernel and newer KMS/DRM/mesa/vaapi/EGL versions is way better performance and playback quality (4K lancoz scaling etc) but also bugs. Right now you are using a very old 16.04 kernel 4.4.0-21 and even 32bit only, apt-get update/upgrade-dist-upgrade helps you there. 

However "the way" to go for future intel videoplayback improvements is use EGL according to KODI developer because the older way will never be fixed/stable. This means at least you use kodi 17 or higher and up to date intel HD graphics drivers.
[http://forum.kodi.tv/showthread.php?tid=231955](http://forum.kodi.tv/showthread.php?tid=231955)

---

### Post by benlyboy on 2017-05-06
Ok because I needed it to crash it went for the longest it ever has. :) 
But in the end it crashed, this a couple of the logs that seem to show something. One talks about the skew being to large, have no idea what that means.
Thanks for the help, if you need anything else let me know, im going to hold off booting the system again incase you all need something else.

syslog
```

May  6 11:52:52 frontendlivingroom kernel: [26977.111179] iwlwifi 0000:02:00.0: Q 30 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
May  6 11:52:52 frontendlivingroom kernel: [26977.145667] clocksource: timekeeping watchdog: Marking clocksource 'tsc' as unstable because the skew is too large:
May  6 11:52:52 frontendlivingroom kernel: [26977.145674] clocksource:                       'acpi_pm' wd_now: b79ba9 wd_last: 2b48e8 mask: ffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.145677] clocksource:                       'tsc' cs_now: 3b38b887b25f cs_last: 3b374676f961 mask: ffffffffffffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.146218] clocksource: Switched to clocksource acpi_pm
May  6 11:53:22 frontendlivingroom kernel: [27007.531999] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:22 frontendlivingroom kernel: [27007.532083] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:22 frontendlivingroom kernel: [27007.532088] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:22 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:23 frontendlivingroom kernel: [27008.555280] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:23 frontendlivingroom kernel: [27008.555341] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:23 frontendlivingroom kernel: [27008.555346] iwlwifi 0000:02:00.0: Scan failed! ret -5May  6 11:52:52 frontendlivingroom kernel: [26977.111179] iwlwifi 0000:02:00.0: Q 30 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
May  6 11:52:52 frontendlivingroom kernel: [26977.145667] clocksource: timekeeping watchdog: Marking clocksource 'tsc' as unstable because the skew is too large:
May  6 11:52:52 frontendlivingroom kernel: [26977.145674] clocksource:                       'acpi_pm' wd_now: b79ba9 wd_last: 2b48e8 mask: ffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.145677] clocksource:                       'tsc' cs_now: 3b38b887b25f cs_last: 3b374676f961 mask: ffffffffffffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.146218] clocksource: Switched to clocksource acpi_pm
May  6 11:53:22 frontendlivingroom kernel: [27007.531999] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:22 frontendlivingroom kernel: [27007.532083] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:22 frontendlivingroom kernel: [27007.532088] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:22 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:23 frontendlivingroom kernel: [27008.555280] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:23 frontendlivingroom kernel: [27008.555341] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:23 frontendlivingroom kernel: [27008.555346] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:24 frontendlivingroom kernel: [27009.582653] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:24 frontendlivingroom kernel: [27009.582769] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:24 frontendlivingroom kernel: [27009.582773] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604001] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:25 frontendlivingroom kernel: [27010.604084] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604092] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:25 frontendlivingroom wpa_supplicant[801]: message repeated 3 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
May  6 11:53:26 frontendlivingroom kernel: [27011.627273] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:26 frontendlivingroom kernel: [27011.627351] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:26 frontendlivingroom kernel: [27011.627356] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:26 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:28 frontendlivingroom kernel: [27012.647840] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:28 frontendlivingroom kernel: [27012.647942] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:28 frontendlivingroom kernel: [27012.647951] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670065] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:29 frontendlivingroom kernel: [27013.670155] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670163] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:30 frontendlivingroom kernel: [27014.691968] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:30 frontendlivingroom kernel: [27014.692064] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:30 frontendlivingroom kernel: [27014.692073] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:31 frontendlivingroom kernel: [27015.713965] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:31 frontendlivingroom kernel: [27015.714068] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:31 frontendlivingroom kernel: [27015.714077] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734490] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:32 frontendlivingroom kernel: [27016.734620] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734634] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:32 frontendlivingroom wpa_supplicant[801]: message repeated 5 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
May  6 11:53:33 frontendlivingroom kernel: [27017.755921] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:33 frontendlivingroom kernel: [27017.756012] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:33 frontendlivingroom kernel: [27017.756021] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:33 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:34 frontendlivingroom kernel: [27018.777349] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:34 frontendlivingroom kernel: [27018.777435] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:34 frontendlivingroom kernel: [27018.777444] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798259] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:35 frontendlivingroom kernel: [27019.798348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819378] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:36 frontendlivingroom kernel: [27020.819490] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819498] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841720] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:37 frontendlivingroom kernel: [27021.841852] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841861] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864333] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:38 frontendlivingroom kernel: [27022.864462] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864471] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:38 frontendlivingroom wpa_supplicant[801]: message repeated 5 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]o
May  6 11:53:39 frontendlivingroom kernel: [27023.884186] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:39 frontendlivingroom kernel: [27023.884271] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:39 frontendlivingroom kernel: [27023.884280] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:39 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:40 frontendlivingroom kernel: [27024.907137] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:40 frontendlivingroom kernel: [27024.907225] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:40 frontendlivingroom kernel: [27024.907234] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927609] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:41 frontendlivingroom kernel: [27025.927674] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927682] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949252] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:42 frontendlivingroom kernel: [27026.949348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:43 frontendlivingroom kernel: [27027.968992] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:43 frontendlivingroom kernel: [27027.969091] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:43 frontendlivingroom kernel: [27027.969100] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:44 frontendlivingroom kernel: [27028.991945] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:44 frontendlivingroom kernel: [27028.992066] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:44 frontendlivingroom kernel: [27028.992074] iwlwifi 0000:02:00.0: Scan failed! ret -5o
May  6 11:53:44 frontendlivingroom wpa_supplicant[801]: message repeated 5 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
May  6 11:53:45 frontendlivingroom kernel: [27030.014943] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:45 frontendlivingroom kernel: [27030.015021] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:45 frontendlivingroom kernel: [27030.015026] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:45 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:24 frontendlivingroom kernel: [27009.582653] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:24 frontendlivingroom kernel: [27009.582769] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:24 frontendlivingroom kernel: [27009.582773] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604001] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:25 frontendlivingroom kernel: [27010.604084] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604092] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:25 frontendlivingroom wpa_supplicant[801]: message repeated 3 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
May  6 11:53:26 frontendlivingroom kernel: [27011.627273] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:26 frontendlivingroom kernel: [27011.627351] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:26 frontendlivingroom kernel: [27011.627356] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:26 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:28 frontendlivingroom kernel: [27012.647840] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:28 frontendlivingroom kernel: [27012.647942] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:28 frontendlivingroom kernel: [27012.647951] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670065] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:29 frontendlivingroom kernel: [27013.670155] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670163] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:30 frontendlivingroom kernel: [27014.691968] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:30 frontendlivingroom kernel: [27014.692064] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:30 frontendlivingroom kernel: [27014.692073] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:31 frontendlivingroom kernel: [27015.713965] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:31 frontendlivingroom kernel: [27015.714068] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:31 frontendlivingroom kernel: [27015.714077] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734490] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:32 frontendlivingroom kernel: [27016.734620] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734634] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:32 frontendlivingroom wpa_supplicant[801]: message repeated 5 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
May  6 11:53:33 frontendlivingroom kernel: [27017.755921] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:33 frontendlivingroom kernel: [27017.756012] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:33 frontendlivingroom kernel: [27017.756021] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:33 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:34 frontendlivingroom kernel: [27018.777349] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:34 frontendlivingroom kernel: [27018.777435] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:34 frontendlivingroom kernel: [27018.777444] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798259] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:35 frontendlivingroom kernel: [27019.798348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819378] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:36 frontendlivingroom kernel: [27020.819490] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819498] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841720] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:37 frontendlivingroom kernel: [27021.841852] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841861] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864333] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:38 frontendlivingroom kernel: [27022.864462] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864471] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:38 frontendlivingroom wpa_supplicant[801]: message repeated 5 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
May  6 11:53:39 frontendlivingroom kernel: [27023.884186] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:39 frontendlivingroom kernel: [27023.884271] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:39 frontendlivingroom kernel: [27023.884280] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:39 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1
May  6 11:53:40 frontendlivingroom kernel: [27024.907137] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:40 frontendlivingroom kernel: [27024.907225] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:40 frontendlivingroom kernel: [27024.907234] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927609] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:41 frontendlivingroom kernel: [27025.927674] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927682] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949252] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:42 frontendlivingroom kernel: [27026.949348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:43 frontendlivingroom kernel: [27027.968992] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:43 frontendlivingroom kernel: [27027.969091] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:43 frontendlivingroom kernel: [27027.969100] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:44 frontendlivingroom kernel: [27028.991945] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:44 frontendlivingroom kernel: [27028.992066] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:44 frontendlivingroom kernel: [27028.992074] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:44 frontendlivingroom wpa_supplicant[801]: message repeated 5 times: [ wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1]
May  6 11:53:45 frontendlivingroom kernel: [27030.014943] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:45 frontendlivingroom kernel: [27030.015021] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:45 frontendlivingroom kernel: [27030.015026] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:45 frontendlivingroom wpa_supplicant[801]: wlp2s0: CTRL-EVENT-SCAN-FAILED ret=-5 retry=1


```

kern.log
```

May  6 11:52:52 frontendlivingroom kernel: [26977.111179] iwlwifi 0000:02:00.0: Q 30 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
May  6 11:52:52 frontendlivingroom kernel: [26977.145667] clocksource: timekeeping watchdog: Marking clocksource 'tsc' as unstable because the skew is too large:o
May  6 11:52:52 frontendlivingroom kernel: [26977.145674] clocksource:                       'acpi_pm' wd_now: b79ba9 wd_last: 2b48e8 mask: ffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.145677] clocksource:                       'tsc' cs_now: 3b38b887b25f cs_last: 3b374676f961 mask: ffffffffffffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.146218] clocksource: Switched to clocksource acpi_pm
May  6 11:53:22 frontendlivingroom kernel: [27007.531999] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:22 frontendlivingroom kernel: [27007.532083] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:22 frontendlivingroom kernel: [27007.532088] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:23 frontendlivingroom kernel: [27008.555280] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:23 frontendlivingroom kernel: [27008.555341] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:23 frontendlivingroom kernel: [27008.555346] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:24 frontendlivingroom kernel: [27009.582653] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:24 frontendlivingroom kernel: [27009.582769] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:24 frontendlivingroom kernel: [27009.582773] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604001] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:5 skew is too large3:25 frontendlivingroom kernel: [27010.604084] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604092] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:26 frontendlivingroom kernel: [27011.627273] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:26 frontendlivingroom kernel: [27011.627351] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:26 frontendlivingroom kernel: [27011.627356] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:28 frontendlivingroom kernel: [27012.647840] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:28 frontendlivingroom kernel: [27012.647942] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:28 frontendlivingroom kernel: [27012.647951] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670065] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:29 frontendlivingroom kernel: [27013.670155] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670163] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:30 frontendlivingroom kernel: [27014.691968] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:30 frontendlivingroom kernel: [27014.692064] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:30 frontendlivingroom kernel: [27014.692073] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:31 frontendlivingroom kernel: [27015.713965] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:31 frontendlivingroom kernel: [27015.714068] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:31 frontendlivingroom kernel: [27015.714077] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734490] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:32 frontendlivingroom kernel: [27016.734620] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734634] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:33 frontendlivingroom kernel: [27017.755921] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:33 frontendlivingroom kernel: [27017.756012] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:33 frontendlivingroom kernel: [27017.756021] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:34 frontendlivingroom kernel: [27018.777349] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:34 frontendlivingroom kernel: [27018.777435] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:34 frontendlivingroom kernel: [27018.777444] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798259] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:35 frontendlivingroom kernel: [27019.798348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819378] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:36 frontendlivingroom kernel: [27020.819490] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819498] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841720] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:37 frontendlivingroom kernel: [27021.841852] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841861] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864333] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:38 frontendlivingroom kernel: [27022.864462] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864471] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:39 frontendlivingroom kernel: [27023.884186] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:39 frontendlivingroom kernel: [27023.884271] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:39 frontendlivingroom kernel: [27023.884280] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:40 frontendlivingroom kernel: [27024.907137] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:40 frontendlivingroom kernel: [27024.907225] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:40 frontendlivingroom kernel: [27024.907234] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927609] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:41 frontendlivingroom kernel: [27025.927674] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927682] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949252] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:42 frontendlivingroom kernel: [27026.949348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:43 frontendlivingroom kernel: [27027.968992] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:43 frontendlivingroom kernel: [27027.969091] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:43 frontendlivingroom kernel: [27027.969100] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:44 frontendlivingroom kernel: [27028.991945] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:44 frontendlivingroom kernel: [27028.992066] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:44 frontendlivingroom kernel: [27028.992074] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:45 frontendlivingroom kernel: [27030.014943] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:45 frontendlivingroom kernel: [27030.015021] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:45 frontendlivingroom kernel: [27030.015026] iwlwifi 0000:02:00.0: Scan failed! ret -5


```

Thanks all:)

---

### Post by TheFu on 2017-05-06
Dont use wifi. Use wired ethernet.

The clock being off at boot isn't crash worthy. NTP should fix that over time, or you can run rdate.  Having the correct time across all your systems is important for many reasons, including security stuff like remote authentication.

I doubt those log entries caused any system crash. You need to find the real error still.  Did you boot from alternate media, then mount the HDD, and look in the /var/log directory on the HDD? It won't be in that location, it will be under the temporary mount.

---

### Post by benlyboy on 2017-05-06
Yes I booted from a thumb drive so the logs should be intact.
Just heading out the door but will take another look at the logs tonight.
Any hints as to what to look for would be a great help.
Thanks again.

---

### Post by benlyboy on 2017-05-07
Ok here are some more log snippets 

First one comes from the mythfrontend.log

```

May  6 11:53:19 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 26855ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:19 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 26972ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:19 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 27089ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:19 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 27205ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:20 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 27322ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:20 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 27439ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:20 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 27555ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:20 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 27672ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:20 frontendlivingroom mythfrontend.real: mythfrontend[1087]: N CoreContext mythplayer.cpp:2176 (PrebufferEnoughFrames) Player(7): Waited 27789ms for video buffers UAAUAAUAAUAAuUAAuAALUAAUAAUAAAUP
May  6 11:53:20 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E MythSocketThread(-1) mythsocket.cpp:858 (ReadStringListReal) MythSocket(b8ba358:75): ReadStringList: Error, timed out after 30000 ms.
May  6 11:53:20 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E RingBuffer mythsocket.cpp:358 (SendReceiveStringList) MythSocket(b8ba358:-1): No response.
May  6 11:53:26 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ffffffff8b65a940:-1): Failed to connect to (192.168.1.222:6543) Host unreachable
May  6 11:53:26 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E RingBuffer remotefile.cpp:164 (openSocket) RemoteFile::openSocket(control socket): Could not connect to server backend1:6543
May  6 11:53:26 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E RingBuffer fileringbuffer.cpp:572 (safe_read) FileRingBuf(myth://backend1/1012_20170409130000.ts): safe_read(RemoteFile* ...): read failed
May  6 11:53:32 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ffffffffa14e1178:-1): Failed to connect to (192.168.1.222:6543) Host unreachable
May  6 11:53:32 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E RingBuffer remotefile.cpp:164 (openSocket) RemoteFile::openSocket(control socket): Could not connect to server backend1:6543
May  6 11:53:38 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ffffffffa99ce7d0:-1): Failed to connect to (192.168.1.222:6543) Host unreachable
May  6 11:53:38 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E RingBuffer remotefile.cpp:164 (openSocket) RemoteFile::openSocket(control socket): Could not connect to server backend1:6543
May  6 11:53:38 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E RingBuffer fileringbuffer.cpp:572 (safe_read) FileRingBuf(myth://backend1/1012_20170409130000.ts): safe_read(RemoteFile* ...): read failed
May  6 11:53:44 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E MythSocketThread(-1) mythsocket.cpp:729 (ConnectToHostReal) MythSocket(ffffffffa992bfa8:-1): Failed to connect to (192.168.1.222:6543) Host unreachable
May  6 11:53:44 frontendlivingroom mythfrontend.real: mythfrontend[1087]: E RingBuffer remotefile.cpp:164 (openSocket) RemoteFile::openSocket(control socket): Could not connect to server backend1:6543



```
And this is around the same time in the kern.log

```

 6 11:52:52 frontendlivingroom kernel: [26977.076530] ------------[ cut here ]------------
May  6 11:52:52 frontendlivingroom kernel: [26977.076546] WARNING: CPU: 0 PID: 0 at /build/linux-QkdMiT/linux-4.4.0/drivers/net/wireless/iwlwifi/iwl-trans.h:1058 iwl_pcie_txq_stuck_timer+0x2f7/0x3c0 [iwlwifi]()
May  6 11:52:52 frontendlivingroom kernel: [26977.076549] Modules linked in: drbg ansi_cprng ctr ccm bnep ir_xmp_decoder dell_wmi sparse_keymap ir_lirc_codec ir_mce_kbd_decoder ir_sharp_decoder ir_sony_decoder ir_sanyo_decoder ir_rc6_decoder ir_jvc_decoder ir_rc5_decoder ir_nec_decoder intel_rapl rc_streamzap intel_soc_dts_iosf streamzap lirc_dev rc_core dcdbas intel_powerclamp coretemp dell_smm_hwmon kvm_intel snd_hda_codec_hdmi arc4 kvm snd_hda_codec_realtek snd_hda_codec_generic iwlmvm irqbypass punit_atom_debug mac80211 crc32_pclmul iwlwifi cfg80211 serio_raw rtsx_pci_ms memstick snd_hda_intel snd_hda_codec lpc_ich snd_intel_sst_acpi btusb btrtl snd_intel_sst_core btbcm btintel snd_hda_core snd_soc_sst_mfld_platform bluetooth shpchp joydev snd_hwdep snd_soc_rt5640 mei_txe mei input_leds snd_soc_rl6231 snd_soc_core snd_compress ac97_bus snd_pcm_dmaengine snd_pcm snd_seq_midi snd_seq_midi_event snd_rawmidi 8250_fintek snd_seq dw_dmac snd_seq_device snd_timer dw_dmac_core snd mac_hid rfkill_gpio i2c_designware_platform soundcore spi_pxa2xx_platform i2c_designware_core snd_soc_sst_acpi 8250_dw pwm_lpss_platform pwm_lpss parport_pc ppdev lp parport autofs4 hid_logitech_hidpp hid_logitech_dj usbhid rtsx_pci_sdmmc i915 psmouse i2c_algo_bit drm_kms_helper syscopyarea r8169 sysfillrect mii sysimgblt fb_sys_fops ahci rtsx_pci drm libahci wmi video sdhci_acpi fjes i2c_hid sdhci hid
May  6 11:52:52 frontendlivingroom kernel: [26977.076648] CPU: 0 PID: 0 Comm: swapper/0 Tainted: G        W       4.4.0-75-generic #96-Ubuntu
May  6 11:52:52 frontendlivingroom kernel: [26977.076651] Hardware name: Dell Inc. Inspiron 3050/0GN4PW, BIOS A01 03/26/2015
May  6 11:52:52 frontendlivingroom kernel: [26977.076653]  c1adf967 d77f568f 00200286 f603fe90 c13ac2df 00000000 f8c60a14 f603fec0
May  6 11:52:52 frontendlivingroom kernel: [26977.076660]  c1070337 c19cf7a4 00000000 00000000 f8c60a14 00000422 f8c4b447 f8c4b447
May  6 11:52:52 frontendlivingroom kernel: [26977.076666]  00a02eac 0000001e f8c5b2e0 f603fed0 c1070442 00000009 00000000 f603ff3c
May  6 11:52:52 frontendlivingroom kernel: [26977.076673] Call Trace:
May  6 11:52:52 frontendlivingroom kernel: [26977.076680]  [<c13ac2df>] dump_stack+0x58/0x79
May  6 11:52:52 frontendlivingroom kernel: [26977.076685]  [<c1070337>] warn_slowpath_common+0x87/0xc0
May  6 11:52:52 frontendlivingroom kernel: [26977.076696]  [<f8c4b447>] ? iwl_pcie_txq_stuck_timer+0x2f7/0x3c0 [iwlwifi]
May  6 11:52:52 frontendlivingroom kernel: [26977.076706]  [<f8c4b447>] ? iwl_pcie_txq_stuck_timer+0x2f7/0x3c0 [iwlwifi]
May  6 11:52:52 frontendlivingroom kernel: [26977.076710]  [<c1070442>] warn_slowpath_null+0x22/0x30
May  6 11:52:52 frontendlivingroom kernel: [26977.076721]  [<f8c4b447>] iwl_pcie_txq_stuck_timer+0x2f7/0x3c0 [iwlwifi]
May  6 11:52:52 frontendlivingroom kernel: [26977.076726]  [<c10d9b10>] call_timer_fn+0x30/0x120
May  6 11:52:52 frontendlivingroom kernel: [26977.076736]  [<f8c4b150>] ? iwl_pcie_txq_unmap+0xf0/0xf0 [iwlwifi]
May  6 11:52:52 frontendlivingroom kernel: [26977.076740]  [<c10da3d9>] run_timer_softirq+0x1c9/0x280
May  6 11:52:52 frontendlivingroom kernel: [26977.076750]  [<f8c4b150>] ? iwl_pcie_txq ureadahead:events/fs/open_exec/enable: Ignored relative path_unmap+0xf0/0xf0 [iwlwifi]
May  6 11:52:52 frontendlivingroom kernel: [26977.076753]  [<c1074987>] __do_softirq+0xd7/0x260
May  6 11:52:52 frontendlivingroom kernel: [26977.076757]  [<c10748b0>] ? cpu_callback+0x1d0/0x1d0
May  6 11:52:52 frontendlivingroom kernel: [26977.076761]  [<c102c208>] do_softirq_own_stack+0x28/0x30
May  6 11:52:52 frontendlivingroom kernel: [26977.076763]  <IRQ>  [<c1074c85>] irq_exit+0xa5/0xb0
May  6 11:52:52 frontendlivingroom kernel: [26977.076770]  [<c17bd6e8>] smp_apic_timer_interrupt+0x38/0x50
May  6 11:52:52 frontendlivingroom kernel: [26977.076774]  [<c17bcdb8>] apic_timer_interrupt+0x34/0x3c
May  6 11:52:52 frontendlivingroom kernel: [26977.076778]  [<c166eb4f>] ? cpuidle_enter_state+0x13f/0x330
May  6 11:52:52 frontendlivingroom kernel: [26977.076782]  [<c166ed74>] cpuidle_enter+0x14/0x20
May  6 11:52:52 frontendlivingroom kernel: [26977.076785]  [<c10affd3>] call_cpuidle+0x33/0x70
May  6 11:52:52 frontendlivingroom kernel: [26977.076789]  [<c10b0282>] cpu_startup_entry+0x272/0x320
May  6 11:52:52 frontendlivingroom kernel: [26977.076793]  [<c17b2517>] rest_init+0x67/0x70
May  6 11:52:52 frontendlivingroom kernel: [26977.076798]  [<c1b99bc0>] start_kernel+0x3ee/0x407
May  6 11:52:52 frontendlivingroom kernel: [26977.076802]  [<c1b992ff>] i386_start_kernel+0x9a/0x9e
May  6 11:52:52 frontendlivingroom kernel: [26977.076804] ---[ end trace 7b046a6a129e060f ]---
May  6 11:52:52 frontendlivingroom kernel: [26977.111179] iwlwifi 0000:02:00.0: Q 30 is active and mapped to fifo 2 ra_tid 0xa5a5 [90,1515870810]
May  6 11:52:52 frontendlivingroom kernel: [26977.145667] clocksource: timekeeping watchdog: Marking clocksource 'tsc' as unstable because the skew is too large:
May  6 11:52:52 frontendlivingroom kernel: [26977.145674] clocksource:                       'acpi_pm' wd_now: b79ba9 wd_last: 2b48e8 mask: ffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.145677] clocksource:                       'tsc' cs_now: 3b38b887b25f cs_last: 3b374676f961 mask: ffffffffffffffff
May  6 11:52:52 frontendlivingroom kernel: [26977.146218] clocksource: Switched to clocksource acpi_pm
May  6 11:53:22 frontendlivingroom kernel: [27007.531999] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:22 frontendlivingroom kernel: [27007.532083] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:22 frontendlivingroom kernel: [27007.532088] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:23 frontendlivingroom kernel: [27008.555280] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:23 frontendlivingroom kernel: [27008.555341] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:23 frontendlivingroom kernel: [27008.555346] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:24 frontendlivingroom kernel: [27009.582653] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:24 frontendlivingroom kernel: [27009.582769] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:24 frontendlivingroom kernel: [27009.582773] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604001] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:25 frontendlivingroom kernel: [27010.604084] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:25 frontendlivingroom kernel: [27010.604092] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:26 frontendlivingroom kernel: [27011.627273] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:26 frontendlivingroom kernel: [27011.627351] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:26 frontendlivingroom kernel: [27011.627356] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:28 frontendlivingroom kernel: [27012.647840] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:28 frontendlivingroom kernel: [27012.647942] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:28 frontendlivingroom kernel: [27012.647951] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670065] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:29 frontendlivingroom kernel: [27013.670155] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:29 frontendlivingroom kernel: [27013.670163] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:30 frontendlivingroom kernel: [27014.691968] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:30 frontendlivingroom kernel: [27014.692064] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:30 frontendlivingroom kernel: [27014.692073] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:31 frontendlivingroom kernel: [27015.713965] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:31 frontendlivingroom kernel: [27015.714068] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:31 frontendlivingroom kernel: [27015.714077] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734490] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:32 frontendlivingroom kernel: [27016.734620] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:32 frontendlivingroom kernel: [27016.734634] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:33 frontendlivingroom kernel: [27017.755921] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:33 frontendlivingroom kernel: [27017.756012] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:33 frontendlivingroom kernel: [27017.756021] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:34 frontendlivingroom kernel: [27018.777349] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:34 frontendlivingroom kernel: [27018.777435] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:34 frontendlivingroom kernel: [27018.777444] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798259] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:35 frontendlivingroom kernel: [27019.798348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:35 frontendlivingroom kernel: [27019.798357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819378] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:36 frontendlivingroom kernel: [27020.819490] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:36 frontendlivingroom kernel: [27020.819498] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841720] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:37 frontendlivingroom kernel: [27021.841852] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:37 frontendlivingroom kernel: [27021.841861] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864333] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:38 frontendlivingroom kernel: [27022.864462] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:38 frontendlivingroom kernel: [27022.864471] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:39 frontendlivingroom kernel: [27023.884186] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:39 frontendlivingroom kernel: [27023.884271] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:39 frontendlivingroom kernel: [27023.884280] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:40 frontendlivingroom kernel: [27024.907137] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:40 frontendlivingroom kernel: [27024.907225] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:40 frontendlivingroom kernel: [27024.907234] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927609] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:41 frontendlivingroom kernel: [27025.927674] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:41 frontendlivingroom kernel: [27025.927682] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949252] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:42 frontendlivingroom kernel: [27026.949348] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:42 frontendlivingroom kernel: [27026.949357] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:43 frontendlivingroom kernel: [27027.968992] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:43 frontendlivingroom kernel: [27027.969091] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:43 frontendlivingroom kernel: [27027.969100] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:44 frontendlivingroom kernel: [27028.991945] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:44 frontendlivingroom kernel: [27028.992066] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:44 frontendlivingroom kernel: [27028.992074] iwlwifi 0000:02:00.0: Scan failed! ret -5
May  6 11:53:45 frontendlivingroom kernel: [27030.014943] iwlwifi 0000:02:00.0: Failed to wake NIC for hcmd
May  6 11:53:45 frontendlivingroom kernel: [27030.015021] iwlwifi 0000:02:00.0: Error sending SCAN_OFFLOAD_REQUEST_CMD: enqueue_hcmd failed: -5
May  6 11:53:45 frontendlivingroom kernel: [27030.015026] iwlwifi 0000:02:00.0: Scan failed! ret -5



```

any idea?

thanks :)

---

### Post by walterav on 2017-05-11
Could you please comment if the info/fix suggested in post #nr11 (top post on this page nr2) has affected/improved your setup, the buggy wireless driver is of later interest.

[https://ubuntuforums.org/showthread.php?t=2360004&p=13642162#post13642162](https://ubuntuforums.org/showthread.php?t=2360004&p=13642162#post13642162)

---

### Post by benlyboy on 2017-05-12
Hey walterav I'm really sorry I completely missed your second post, and didn't really understand what you were getting at in the first, my fault not yours. 

I've now done the "intel_idle.max_cstate=1" I'll look at the other point you brought up in your other post and do that soon.

 I'll let you know if the "intel_idle.max_cstate=1" helps,

Hey again sorry for not replaying sooner, and thanks so much for your help

---

### Post by walterav on 2017-05-13
@benlyboy

There is so much information even I ;-) miss some posts, this cpu fix is just one thing. Since graphics lockup by doing gpu assisted video decoding is another also your wifi. BTW your bios is A01 and maybe there is also a upgrade available (probably windows only) but you might have a look at the changelog to see if its worth the risk to upgrade.

---

### Post by mörgæs on 2017-05-13
The Bay Trail series has had several problems over time and a considerable effort has been put into fixing them. 

Installing 17.04 will give you the best foundation for getting a working system. One can't expect bug fixes applied to 17.04 to trickle down to stale software like 16.* It may happen eventually but don't take it for granted.

---

### Post by benlyboy on 2017-05-14
Walterav  thanks.
Waited for a night or two to be sure before posting, 
It seems that the "intel_idle.max_cstate=1" fix fixed the freeze&#128540;&#128077; very happy.
So do I still need to do the "assisted video playback " as well?

Thanks again?

---

### Post by walterav on 2017-05-15
Good to hear, I was also going in circles before it got stable (running almost a year uptime as a simple server for now). But trust me assisted videoplayback is still a good candidate to lockup or freeze graphics or the whole system, depending on codec mpeg2/h264 it may work perfect or lockup. If you have ssh access you can debug crashing graphics stack, also wireless driver is a candidate according to your logs for crash, use ethernet for video streaming.

I would advice you to use KODI for debugging although you like mythtv, if all kind of video assisted playback works fine/stable with kodi and maybe some PPA with newest graphics stack (try LTS stack first) than go back to mythtv using the settings that were succesfull for kodi.

---

### Post by benlyboy on 2017-05-19
I have two boxes that are basically the same, so I'm going to leave one alone as it now seem stable. I may play with the other and see if I can make the changes you talked about. but I think I will now mark this a solved as its been running for a week now with no problems.



walterav thanks for the help, I had completely run out of ideas. so I really do appreciate the help. 
Oh and my wife is happy to as it no longer freezes in the middle of real housewives of somewhere :roll:

So thanks again :-k I think :o

---

### Post by walterav on 2017-05-19
Thanks for responding, your possibilities for further optimization of possible graphics bugs are as follow:

Stay on 16.04 for the LTS stable apps but add HWE upgrades (kernel & graphics stack) from newer ubuntu releases into 16.04 with simple meta packages hwe-16.04 / hwe-16.04-edge see article about apt-getting these "hwe" options. 

[https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack](https://wiki.ubuntu.com/Kernel/RollingLTSEnablementStack)

The other route for mainly graphic improvements is adding PPA's with updated graphics stacks from oibaf or padoka

[https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers/](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers/)
[https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates](https://launchpad.net/~ubuntu-x-swat/+archive/ubuntu/updates)
[https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa](https://launchpad.net/~paulo-miguel-dias/+archive/ubuntu/mesa)

Add the ppa and update/upgrade your reboot system and your are running newer drivers, don't add all these ppa's at the same time try one at a time good luck!

---

