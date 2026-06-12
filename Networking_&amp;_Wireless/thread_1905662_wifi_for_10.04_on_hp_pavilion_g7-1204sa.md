---
title: "wifi for 10.04 on hp pavilion g7-1204sa"
date: 2012-01-07
forum: Networking &amp; Wireless
---

### Post by paulernest on 2012-01-07
Hi,

Just got a new laptop and have having some real problems getting the wifi to work. There are several articles with other people having this sort of problem, but I'm not quite sure where to being with the solutions and I was looking for some help.

Firstly I thought it would be sensible to identify exactly what chipset/wifi adapter this machine has. The HP website was useless (as expected), but various articles and the output of lshw, I believe it's some type of atheros communications card, but I can find out which one exactly.

The full output from lshw is shown below. I'd really appreciate any help that anyone can give me.

Thanks,

Paul

```
dominic-laptop            
    description: Notebook
    product: HP Pavilion g7 Notebook PC
    vendor: Hewlett-Packard
    version: 0691120000204610000620100
    serial: 5CD14515TD
    width: 64 bits
    capabilities: smbios-2.7 dmi-2.7 vsyscall64 vsyscall32
    configuration: boot=normal chassis=notebook uuid=35434431-3435-3135-5444-EC9A743E1945
  *-core
       description: Motherboard
       product: 3568
       vendor: Hewlett-Packard
       physical id: 0
       version: 21.27
       serial: PCFSF002C130KR
       slot: Base Board Chassis Location
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.35 (10/17/2011)
          size: 128KiB
          capacity: 1984KiB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppynec int13floppytoshiba int13floppy360 int13floppy1200 int13floppy720 int13floppy2880 int9keyboard int10video acpi usb
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 6GiB
        *-bank:0
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: 8JSF25664HZ-1G4D1
             vendor: Micron Technology
             physical id: 0
             serial: 3328F97E
             slot: Bottom - Slot 1 (top)
             size: 2GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
        *-bank:1
             description: SODIMM Synchronous 1333 MHz (0.8 ns)
             product: M471B5273DH0-CH9
             vendor: Samsung
             physical id: 1
             serial: 0035838D
             slot: Bottom - Slot 2 (under)
             size: 4GiB
             width: 64 bits
             clock: 1333MHz (0.8ns)
     *-cpu
          description: CPU
          product: AMD A6-3400M APU with Radeon(tm) HD Graphics
          vendor: Advanced Micro Devices [AMD]
          physical id: 11
          bus info: cpu@0
          version: AMD A6-3400M APU with Radeon(tm) HD Graphics
          serial: NotSupport
          slot: Socket FS1
          size: 800MHz
          capacity: 1400MHz
          width: 64 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt pdpe1gb rdtscp x86-64 3dnowext 3dnow constant_tsc nonstop_tsc extd_apicid pni monitor cx16 popcnt lahf_lm cmp_legacy svm extapic cr8_legacy abm sse4a misalignsse 3dnowprefetch osvw ibs skinit wdt arat cpufreq
        *-cache:0
             description: L1 cache
             physical id: 12
             slot: L1 Cache
             size: 512KiB
             capacity: 512KiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
        *-cache:1
             description: L2 cache
             physical id: 13
             slot: L2 Cache
             size: 4MiB
             capacity: 4MiB
             clock: 1GHz (1.0ns)
             capabilities: pipeline-burst internal write-back unified
     *-pci:0
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 00
          width: 32 bits
          clock: 66MHz
          configuration: latency=32
        *-display UNCLAIMED
             description: VGA compatible controller
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: latency=0
             resources: memory:e0000000-efffffff(prefetchable) ioport:3000(size=256) memory:f0300000-f033ffff
        *-multimedia:0
             description: Audio device
             product: ATI Technologies Inc
             vendor: ATI Technologies Inc
             physical id: 1.1
             bus info: pci@0000:00:01.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pm pciexpress msi bus_master cap_list
             configuration: driver=HDA Intel latency=0
             resources: irq:19 memory:f0344000-f0347fff
        *-pci:0
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 4
             bus info: pci@0000:00:04.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:24 memory:f0200000-f02fffff memory:f0400000-f04fffff(prefetchable)
           *-network UNCLAIMED
                description: Network controller
                product: Atheros Communications Inc.
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:01:00.0
                version: 01
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f0200000-f027ffff memory:f0400000-f040ffff(prefetchable)
        *-pci:1
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 5
             bus info: pci@0000:00:05.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:25 ioport:2000(size=4096) ioport:f0000000(size=1048576)
           *-network
                description: Ethernet interface
                product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: eth0
                version: 05
                serial: ec:9a:74:3e:19:45
                size: 100MB/s
                capacity: 100MB/s
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.0.2 latency=0 link=yes multicast=yes port=MII speed=100MB/s
                resources: irq:28 ioport:2000(size=256) memory:f0004000-f0004fff(prefetchable) memory:f0000000-f0003fff(prefetchable)
        *-pci:2
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 6
             bus info: pci@0000:00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm pciexpress msi ht bus_master cap_list
             configuration: driver=pcieport
             resources: irq:26 memory:f0100000-f01fffff memory:f0500000-f05fffff(prefetchable)
           *-generic UNCLAIMED
                product: Realtek Semiconductor Co., Ltd.
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:03:00.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list
                configuration: latency=0
                resources: memory:f0100000-f0100fff memory:f0500000-f050ffff(prefetchable)
        *-storage
             description: SATA controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 11
             bus info: pci@0000:00:11.0
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi bus_master cap_list emulated
             configuration: driver=ahci latency=64
             resources: irq:27 ioport:3118(size=8) ioport:3124(size=4) ioport:3110(size=8) ioport:3120(size=4) ioport:3100(size=16) memory:f034e000-f034e7ff
           *-disk
                description: ATA Disk
                product: WDC WD7500BPVT-6
                vendor: Western Digital
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: 01.0
                serial: WD-WXD1A91A3938
                size: 698GiB (750GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=5e9183ec
              *-volume:0
                   description: Extended partition
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   size: 679GiB
                   capacity: 679GiB
                   capabilities: primary extended partitioned partitioned:extended
                 *-logicalvolume:0
                      description: Linux filesystem partition
                      physical id: 5
                      logical name: /dev/sda5
                      logical name: /
                      capacity: 23GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,barrier=1,data=ordered state=mounted
                 *-logicalvolume:1
                      description: Linux swap / Solaris partition
                      physical id: 6
                      logical name: /dev/sda6
                      capacity: 4767MiB
                      capabilities: nofs
                 *-logicalvolume:2
                      description: Linux filesystem partition
                      physical id: 7
                      logical name: /dev/sda7
                      logical name: /tmp
                      capacity: 3814MiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:3
                      description: Linux filesystem partition
                      physical id: 8
                      logical name: /dev/sda8
                      logical name: /home
                      capacity: 27GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
                 *-logicalvolume:4
                      description: Linux filesystem partition
                      physical id: 9
                      logical name: /dev/sda9
                      logical name: /DATA
                      capacity: 620GiB
                      configuration: mount.fstype=ext4 mount.options=rw,relatime,barrier=1,data=ordered state=mounted
              *-volume:1
                   description: Windows NTFS volume
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   version: 3.1
                   serial: 9832611f-4152-2f40-ac99-c51c27b93d8d
                   size: 14GiB
                   capacity: 14GiB
                   capabilities: primary ntfs initialized
                   configuration: clustersize=4096 created=2011-11-25 09:33:20 filesystem=ntfs label=Recovery state=clean
              *-volume:2
                   description: Windows FAT volume
                   vendor: MSDOS5.0
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: FAT32
                   serial: c24f-d0a0
                   size: 4049MiB
                   capacity: 4062MiB
                   capabilities: primary fat initialized
                   configuration: FATs=2 filesystem=fat
           *-cdrom
                description: DVD-RAM writer
                product: DVD-RAM UJ8B1
                vendor: hp
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: H.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
                configuration: ansiversion=5 status=nodisc
        *-usb:0
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 12
             bus info: pci@0000:00:12.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f034d000-f034dfff
        *-usb:1
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 12.2
             bus info: pci@0000:00:12.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:f034c000-f034c0ff
        *-usb:2
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f034b000-f034bfff
        *-usb:3
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:f034a000-f034a0ff
        *-serial UNCLAIMED
             description: SMBus
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 13
             width: 32 bits
             clock: 66MHz
             configuration: latency=0
        *-multimedia:1
             description: Audio device
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 01
             width: 64 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=HDA Intel latency=32
             resources: irq:16 memory:f0340000-f0343fff
        *-isa
             description: ISA bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:3
             description: PCI bridge
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 40
             width: 32 bits
             clock: 66MHz
             capabilities: pci bus_master
        *-usb:4
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 16
             bus info: pci@0000:00:16.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: bus_master
             configuration: driver=ohci_hcd latency=32
             resources: irq:18 memory:f0349000-f0349fff
        *-usb:5
             description: USB Controller
             product: Advanced Micro Devices [AMD]
             vendor: Advanced Micro Devices [AMD]
             physical id: 16.2
             bus info: pci@0000:00:16.2
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: pm debug bus_master cap_list
             configuration: driver=ehci_hcd latency=32
             resources: irq:17 memory:f0348000-f03480ff
     *-pci:1
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 43
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@0000:00:18.4
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:6
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 106
          bus info: pci@0000:00:18.5
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:7
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 107
          bus info: pci@0000:00:18.6
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:8
          description: Host bridge
          product: Advanced Micro Devices [AMD]
          vendor: Advanced Micro Devices [AMD]
          physical id: 108
          bus info: pci@0000:00:18.7
          version: 00
          width: 32 bits
          clock: 33MHz
  *-battery
       description: Lithium Ion Battery
       product: MU06047
       vendor: 13-15
       physical id: 1
       slot: Primary
       capacity: 47520mWh
       configuration: voltage=10.8V

```

---

### Post by wildmanne39 on 2012-01-07
Hi, please post the output of:
```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
iwconfig
rfkill list all
lsmod
```
by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by paulernest on 2012-01-07
Thanks for offering some help, here is the output you've requested. I've run all of those as root, let me know if I should run them as myself. 

```
dominic@dominic-laptop:~$ sudo cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=10.04
DISTRIB_CODENAME=lucid
DISTRIB_DESCRIPTION="Ubuntu 10.04.3 LTS"
Linux dominic-laptop 2.6.32-37-generic #81-Ubuntu SMP Fri Dec 2 20:32:42 UTC 2011 x86_64 GNU/Linux
``````
dominic@dominic-laptop:~$ sudo lspci -nnk | grep -iA2 net
01:00.0 Network controller [0280]: Atheros Communications Inc. Device [168c:0032] (rev 01)
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Kernel driver in use: r8169
    Kernel modules: r8169
``````
dominic@dominic-laptop:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.


```No results from rfkill list all
```
dominic@dominic-laptop:~$ sudo lsmod
Module                  Size  Used by
binfmt_misc             7960  1 
ppdev                   6375  0 
snd_hda_codec_idt      61546  1 
snd_hda_codec_atihdmi     3023  1 
snd_hda_intel          25805  2 
snd_hda_codec          85759  3 snd_hda_codec_idt,snd_hda_codec_atihdmi,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
psmouse                65040  0 
uvcvideo               62915  0 
videodev               40550  1 uvcvideo
v4l1_compat            15495  2 uvcvideo,videodev
v4l2_compat_ioctl32    11892  1 videodev
serio_raw               4918  0 
snd                    71283  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
i2c_piix4               9639  0 
video                  20623  0 
output                  2503  1 video
soundcore               8052  1 snd
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
vga16fb                12757  1 
vgastate                9857  1 vga16fb
lp                      9336  0 
parport                37160  2 ppdev,lp
r8169                  39714  0 
mii                     5237  1 r8169
ahci                   38350  5
```

---

### Post by paulernest on 2012-01-07
Thanks to [wildmanne39]("http://ubuntuforums.org/member.php?u=508533") for showing me the telling me about th[FONT=monospace]e l[/FONT]spci -nnk | grep -iA2 net command, it allowed me to find the code for my hardware, which was 168:0032. Googling this gave me the solution, the full thread can be found in this [thread]("http://ubuntuforums.org/showthread.php?t=1857808"), post #63, I've repeated it below for convenience.

```

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential 
wget http://www.orbit-lab.org/kernel/compat-wireless-2.6/compat-wireless-2.6.tar.bz2  
tar jxvf compat-wireless-2.6.tar.bz2
cd compat-wireless-20*
./scripts/driver-select atheros 
make
sudo make install

```then follow the instructions that appear after the last command.

---

### Post by wildmanne39 on 2012-01-07
Hi, your device is not supported until kernel 2.6.39 which means you need to upgrade preferrabley to 11.10 or try to install this device with ndiswrapper which is a last resort.
Thanks

---

### Post by wildmanne39 on 2012-01-07
Hi paulernest, that is my thread.
Did you have to upgrade ubuntu?
Thanks

---

### Post by paulernest on 2012-01-08
Nope, no upgrade, just downloaded the 64bit version of long term support yesterday, installed, ran the update manager (didn't upgrade).

The latest version of ubuntu doesn't install or even successfully boot from the livecd on this machine! When I use the live cd I get the first screen with the two/three little icons at the bottom (usb drive, equals sign and little man), but then the screen goes blank and I need to hold the power button to reset.

As an experiment whilst trying to get the wireless working, I installed 10.04, plugged in the wired network and upgraded to 10.10 then 11.04, but on reboot the machine wouldn't start. I started it in recovery mode and it came up with a message of something like "unable to initialise (either atheros or ath9h).

I really wanted to use 10.04, not the newer version, so I'm happy as I am.

Thanks again for your help.

---

### Post by wildmanne39 on 2012-01-08
Hi, thank you for letting me know that it works in 10.04 also.

---

### Post by paulernest on 2012-01-09
Hi Wildmanne39

If you are still following this thread, then I do have another question. One of my experiments was to install Lucid and then to upgrade through to the latest release. When I got as far as Natty, the machine wouldn't start successfully and in recovery mode it also failed to load, but I got an error which I *think* was something like
Failed to load atheros ath9k
Do you know if it is possible to disable the wifi card (no options exist to do this in my bios) so that I can at least boot into Natty, then maybe fix the problem.

Thanks again.

---

### Post by wildmanne39 on 2012-01-09
Hi, you can disable the wireless lan in some bios but not all.

Also you can use nomodeset to disable things here is a link for that.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
Thanks

---

