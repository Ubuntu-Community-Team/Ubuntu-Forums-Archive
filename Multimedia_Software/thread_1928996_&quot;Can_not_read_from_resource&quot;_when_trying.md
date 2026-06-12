---
title: "&quot;Can not read from resource&quot; when trying to play DVD"
date: 2012-02-21
forum: Multimedia Software
---

### Post by gabriella on 2012-02-21
Hi,

The title pretty much says it all.

When I try to play a DVD I get the error message "can not read from resource" I checked to see if I have the package libdvdcss2 installed and I do. So I don't understand why it won't work.

So if someone could help me please?
I'm using Maveric btw and will provide any other info needed.

Thanks

---

### Post by Grenage on 2012-02-21
You've ruled out the DVD, I presume, by trying other discs?

---

### Post by roelforg on 2012-02-21
If Grenage's idea won't work;
check if the ide/sata cable inside the pc is loose.
My pc's dvd-reader  wouldn't work for a while because the connector inside was only half-inserted.

---

### Post by gabriella on 2012-02-22
Well thanks Guys..

No DVD's will play and cable is connected. The drive will play audio CD's but no DVD's. "Can not read from resource" every time! :confused:

---

### Post by Grenage on 2012-02-22
> **gabriella said:**
> Well thanks Guys..

No DVD's will play and cable is connected. The drive will play audio CD's but no DVD's. "Can not read from resource" every time! :confused:

Well that's promising. Try installing the restricted extras (if not installed) with:

```
sudo apt-get install ubuntu-restricted-extras
```

If that does not help, I would recommend another media player, such as VLC.  It's a decent player.

---

### Post by winh8r on 2012-02-22
Can you open a terminal and enter the following:
 
```
sudo lshw
```

and copy and paste the results of the " *-cdrom" section of that report in your next post please.

---

### Post by gabriella on 2012-02-22
Thanks for the ideas..

Ubuntu-restricted-extras is already installed.
I have several media players installed, including VLC, and its the same on all of them!

```
Gabhome@M2000:~$ sudo lshw
[sudo] password for gabhome: 
m2000                     
    description: Notebook
    product: Presario M2000 (EK823EA#ABU)
    vendor: Hewlett-Packard
    version: Rev 1
    serial: CNF5452FZ2
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31 smp-1.4 smp
    configuration: boot=oem-specific chassis=notebook cpus=1 uuid=A0C6B6B5-3E08-DA11-8B2A-00C09FF39778
  *-core
       description: Motherboard
       product: 3096
       vendor: Quanta
       physical id: 0
       version: 47.0E
       serial: None
     *-firmware
          description: BIOS
          vendor: Hewlett-Packard
          physical id: 0
          version: F.13 (10/19/2005)
          size: 104KiB
          capacity: 448KiB
          capabilities: pci pcmcia pnp apm upgrade shadowing escd cdboot int5printscreen int9keyboard int14serial int17printer int10video acpi usb
     *-cpu
          description: CPU
          product: AMD Turion(tm) 64 Mobile Technology ML-30
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: 15.4.2
          slot: U23
          size: 1600MHz
          capacity: 1600MHz
          width: 64 bits
          clock: 200MHz
          capabilities: boot fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow up pni lahf_lm cpufreq
        *-cache:0
             description: L2 cache
             physical id: 5
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: synchronous internal write-back
        *-cache:1
             description: L1 cache
             physical id: 0
             size: 128KiB
        *-cache:2
             description: L2 cache
             physical id: 1
             size: 1MiB
     *-memory
          description: System Memory
          physical id: 9
          slot: System board or motherboard
          size: 1GiB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: U5
             size: 512MiB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: U6
             size: 512MiB
             width: 32 bits
     *-pci:0
          description: Host bridge
          product: RS480 Host Bridge
          vendor: ATI Technologies Inc
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 01
          width: 32 bits
          clock: 66MHz
          configuration: latency=64
        *-pci:0
             description: PCI bridge
             product: RS480 PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci ht normal_decode bus_master cap_list
             resources: ioport:9000(size=4096) memory:c0100000-c01fffff ioport:c8000000(size=134217728)
           *-display
                description: VGA compatible controller
                product: Radeon XPRESS 200M 5955 (PCIE)
                vendor: ATI Technologies Inc
                physical id: 5
                bus info: pci@0000:01:05.0
                version: 00
                width: 32 bits
                clock: 66MHz
                capabilities: pm vga_controller bus_master cap_list rom
                configuration: driver=radeon latency=66 mingnt=8
                resources: irq:17 memory:c8000000-cfffffff ioport:9000(size=256) memory:c0100000-c010ffff memory:c0120000-c013ffff
        *-usb:0
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13
             bus info: pci@0000:00:13.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0000000-c0000fff
        *-usb:1
             description: USB Controller
             product: IXP SB400 USB Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.1
             bus info: pci@0000:00:13.1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: msi ohci bus_master cap_list
             configuration: driver=ohci_hcd latency=64
             resources: irq:19 memory:c0001000-c0001fff
        *-usb:2
             description: USB Controller
             product: IXP SB400 USB2 Host Controller
             vendor: ATI Technologies Inc
             physical id: 13.2
             bus info: pci@0000:00:13.2
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pm msi ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=64
             resources: irq:19 memory:c0002000-c0002fff
        *-serial
             description: SMBus
             product: IXP SB400 SMBus Controller
             vendor: ATI Technologies Inc
             physical id: 14
             bus info: pci@0000:00:14.0
             version: 11
             width: 32 bits
             clock: 66MHz
             capabilities: ht cap_list
             configuration: driver=piix4_smbus latency=0
             resources: irq:0 ioport:8400(size=16) memory:c0003000-c00033ff
        *-ide
             description: IDE interface
             product: IXP SB400 IDE Controller
             vendor: ATI Technologies Inc
             physical id: 14.1
             bus info: pci@0000:00:14.1
             logical name: scsi0
             logical name: scsi1
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: ide msi bus_master cap_list emulated
             configuration: driver=pata_atiixp latency=64
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:8410(size=16)
           *-disk
                description: ATA Disk
                product: SAMSUNG HM121HC
                physical id: 0
                bus info: scsi@0:0.0.0
                logical name: /dev/sda
                version: LS10
                serial: S2FDJDRZ800265
                size: 111GiB (120GB)
                capabilities: partitioned partitioned:dos
                configuration: ansiversion=5 signature=adf1adf1
              *-volume:0
                   description: Windows NTFS volume
                   physical id: 1
                   bus info: scsi@0:0.0.0,1
                   logical name: /dev/sda1
                   version: 3.1
                   serial: d2a10e86-a389-b94b-8c35-e7ce04fe95d1
                   size: 18GiB
                   capacity: 18GiB
                   capabilities: primary bootable ntfs initialized
                   configuration: clustersize=4096 created=2011-03-05 04:37:43 filesystem=ntfs modified_by_chkdsk=true mounted_on_nt4=true resize_log_file=true state=dirty upgrade_on_mount=true
              *-volume:1
                   description: EXT4 volume
                   vendor: Linux
                   physical id: 2
                   bus info: scsi@0:0.0.0,2
                   logical name: /dev/sda2
                   logical name: /
                   version: 1.0
                   serial: c50b126a-7859-4109-a6ca-dd55cf3e36cd
                   size: 55GiB
                   capacity: 55GiB
                   capabilities: primary journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                   configuration: created=2011-03-05 10:25:55 filesystem=ext4 lastmountpoint=/mj&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;c&#65533;Tv!&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;c&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;8&#65533;c&#65533;&#65533;x!&#65533;&#65533;o modified=2012-02-20 10:12:20 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,commit=600,barrier=1,data=ordered mounted=2012-02-22 11:04:15 state=mounted
              *-volume:2
                   description: Linux swap volume
                   physical id: 3
                   bus info: scsi@0:0.0.0,3
                   logical name: /dev/sda3
                   version: 1
                   serial: 06d65032-bec4-4427-bceb-6bd7f26df6d4
                   size: 477MiB
                   capacity: 477MiB
                   capabilities: primary nofs swap initialized
                   configuration: filesystem=swap pagesize=4096
           *-cdrom
                description: DVD writer
                product: UJ-840D
                vendor: MATSHITA
                physical id: 1
                bus info: scsi@1:0.0.0
                logical name: /dev/cdrom
                logical name: /dev/cdrw
                logical name: /dev/dvd
                logical name: /dev/dvdrw
                logical name: /dev/scd0
                logical name: /dev/sr0
                version: 1.02
                capabilities: removable audio cd-r cd-rw dvd dvd-r
                configuration: ansiversion=5 status=nodisc
        *-isa
             description: ISA bridge
             product: IXP SB400 PCI-ISA Bridge
             vendor: ATI Technologies Inc
             physical id: 14.3
             bus info: pci@0000:00:14.3
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-pci:1
             description: PCI bridge
             product: IXP SB400 PCI-PCI Bridge
             vendor: ATI Technologies Inc
             physical id: 14.4
             bus info: pci@0000:00:14.4
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci subtractive_decode bus_master
             resources: ioport:a000(size=4096) memory:c0200000-c02fffff memory:40000000-43ffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 0
                bus info: pci@0000:05:00.0
                logical name: eth0
                version: 10
                serial: 00:c0:9f:f3:97:78
                size: 10MB/s
                capacity: 100MB/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
                resources: irq:18 ioport:a000(size=256) memory:c0208000-c02080ff
           *-network:1
                description: Network controller
                product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
                vendor: Broadcom Corporation
                physical id: 2
                bus info: pci@0000:05:02.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master
                configuration: driver=b43-pci-bridge latency=64
                resources: irq:20 memory:c0204000-c0205fff
           *-pcmcia
                description: CardBus bridge
                product: PCIxx21/x515 Cardbus Controller
                vendor: Texas Instruments
                physical id: 9
                bus info: pci@0000:05:09.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:17 memory:c0200000-c0200fff ioport:a400(size=256) ioport:a800(size=256) memory:40000000-43ffffff memory:44000000-47ffffff
        *-multimedia
             description: Multimedia audio controller
             product: IXP SB400 AC'97 Audio Controller
             vendor: ATI Technologies Inc
             physical id: 14.5
             bus info: pci@0000:00:14.5
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi bus_master cap_list
             configuration: driver=ATI IXP AC97 controller latency=64 mingnt=2
             resources: irq:17 memory:c0003400-c00034ff
        *-communication
             description: Modem
             product: SB400 AC'97 Modem Controller
             vendor: ATI Technologies Inc
             physical id: 14.6
             bus info: pci@0000:00:14.6
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: msi generic bus_master cap_list
             configuration: driver=ATI IXP MC97 controller latency=64 mingnt=2
             resources: irq:17 memory:c0003800-c00038ff
     *-pci:1
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 101
          bus info: pci@0000:00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@0000:00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@0000:00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@0000:00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
          configuration: driver=k8temp
          resources: irq:0
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan0
       serial: 00:14:a5:29:d2:c2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=2.6.35-28-generic firmware=N/A ip=192.168.2.3 link=yes multicast=yes wireless=IEEE 802.11bg
 
```

---

### Post by winh8r on 2012-02-23
Try entering this in the terminal:


```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 
```


then run this:

```
sudo apt-get update
```

Has this drive only recently stopped playing DVD's?

---

### Post by gabriella on 2012-02-23
> **winh8r said:**
> Try entering this in the terminal:


```
sudo apt-get install libdvdcss2 libdvdread4 libdvdnav4 
```


then run this:

```
sudo apt-get update
```

Has this drive only recently stopped playing DVD's?

Thanks..
I ran that and as suspected the newest versions are already istalled, updated the rest etc.

As to recently stopped playing? Hmmm? I cant say exactly when because I didn't try DVD's for a while. It used to play them just fine. 

At some point last year I did a fresh install of Maverick. Whether it directly coincided with that I honestly cant say. All I can say is it used to work. Sorry this is not much help!

I just tried the DVD again. The drive physically whirs and clunks like normal like it's trying to read the tracks right before the error message pops up

---

### Post by winh8r on 2012-02-23
try running this command:


```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

then stick a dvd in the drive and see what happens.

---

### Post by gabriella on 2012-02-24
> **winh8r said:**
> try running this command:


```
sudo /usr/share/doc/libdvdread4/install-css.sh
```

then stick a dvd in the drive and see what happens.

But I already have libdvdread4 installed don't I? 
Anyway I tried that and the result is still the same "unable to read from resource" Grrrr :confused:

---

### Post by BicyclerBoy on 2012-02-24
Matshita optical drives are trouble (especially laptop/notebook drives).
They cause problems with windows & linux users..

These drives' RPC2 firmware are picky about region setting.

Is it possible your windows install has permanently set the region (used up the 5 changes).
Does the drive work in windows ?
What region & region change count does windows report ?

Things to try:
- (long shot) try to set the region with regionset..
- find an alt firmware for the drive (dump, modify, reflash)

([http://forum.rpc1.org/viewtopic.php?f=2&t=46246](http://forum.rpc1.org/viewtopic.php?f=2&t=46246))

- get a replacement (non-matshita) optical drive.
- external optical drive

---

### Post by spegru on 2012-02-25
AFAIK DVD regions are set in software not on the drive itself so it's unlikely to be that. Much more likely to be the disc or the drive itself.
Can you try an external USB drive?

---

### Post by BicyclerBoy on 2012-02-25
Nonsense
You're thinking of BDs.
RPC2 firmware DVD drives store the region setting, this is mandatory for mpeg licence.
Furthermore licenced player software & OS also store/set the region.

i.e.
windows stores/sets the region.
windows player stores/sets the region
The player firmware allows 5 changes & stores/set/locks the region.

This is why RPC1 firmware for this drive may be helpful.

@OP Does VLC in 'windows' work with this DVD optical drive (& same DVD).
The windows build of VLC includes libdvdcss.

---

### Post by gabriella on 2012-02-25
> **BicyclerBoy said:**
> Matshita optical drives are trouble (especially laptop/notebook drives).
They cause problems with windows & linux users..

These drives' RPC2 firmware are picky about region setting.

Is it possible your windows install has permanently set the region (used up the 5 changes).
Does the drive work in windows ?
What region & region change count does windows report ?

Things to try:
- (long shot) try to set the region with regionset..
- find an alt firmware for the drive (dump, modify, reflash)

([http://forum.rpc1.org/viewtopic.php?f=2&t=46246](http://forum.rpc1.org/viewtopic.php?f=2&t=46246))

- get a replacement (non-matshita) optical drive.
- external optical drive

Thanks for those sugestions. I do travel quite a lot so this is a possibility, however, I don't remember changing the region in quite a while. The Laptop does have a Windows XP partition hidden away on it but haven't booted into that in a long lomg time. I try your ideas and report back.

Thanks :)

---

### Post by mc4man on 2012-02-25
> Matshita optical drives are trouble (especially laptop/notebook drives).
They cause problems with windows & linux users..

These drives' RPC2 firmware are picky about region setting.

That's putting it mildly, most Matshita laptop drives will absolutely not allow access to encrypted sectors if there is a region mismatch. End of story.

Historically there have been almost no firmware flash's for these drives, one was developed for a model used mainly on Mac's.

I believe an alternate method arose a year ago or so, it isn't a firmware flash per se.
What it does is dump the drives current firmware & uses that to create a new firmware for that drive.

Even though I have a Matshita laptop drive here have never bothered to check out or see if it needs to be done on windows ect.
(the cost of replacing a bricked ultra slim drive on this laptop isn't   worth the small gain to me


Edit: Just to point out the difference
On most dvd drives - when using an open source, unlicensed player with libdvdcss, if there is a region mismatch then libdvdcss switches from disc/title key extraction, which isn't available, to a brute force method.
If there is a large enough sample then it's always successful, (assuming no additional structure protection),  that's how poor css is.
Occasionally some extra's may not provide enough of a sample & can't be decrypted if in fact they are.

Matshita laptop drives take this a step further, no access to the encrypted sectors at all, so then even brute force can't possibly work

---

