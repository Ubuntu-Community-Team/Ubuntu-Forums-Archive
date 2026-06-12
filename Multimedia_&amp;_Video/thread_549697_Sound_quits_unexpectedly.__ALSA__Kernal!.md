---
title: "Sound quits unexpectedly.  ALSA?  Kernal?!"
date: 2007-09-12
forum: Multimedia &amp; Video
---

### Post by whatisdot on 2007-09-12
Ok, i have had it!  :-x  Every time I think I have solved this problem, it just keeps popping up.  Every time I boot, I have sound.  No problem, right?  I use the system for a while, and after what seems like a random amount of time (could be days, could be minutes), all devices playing or trying to play sound crash HARD.  I mean they stop responding...  At this point, any device that starts up and tries to use sound becomes unresponsive.  I try to restart the system and it halts at "Shutting down ALSA" and stays that way, so I am forced to push the reset button.  The system reboots and we start all over again...

I have been through 10+ threads (most of which were unanswered...) about something that sounds like this issue, as well as all of the "How to set up your sound card" threads on multiple forums, and now its time to finish this.  I believe I had this problem, or a very similar one when I was using Fedora, so this could be a kernel issue.  I've heard whispers that might be it...but no answers...not even any GOOD IDEAS!  Just so you know, I never had any of these problems with Windows.

Now, I lay my system before you.  If I want to find out every little thing sound related, what kind of logs should I look in, and what commands should I have running/outputting?  Here is some preliminary information for you guys:

I am using software sound mixing:

***.asoundrc:***
```
pcm.dsp0 { ## This is accessed by oss applications
	type plug
	slave.pcm "dmixer"
}
ctl.mixer0 { ## This ties mixer controls for oss mixer programs
	type hw
	card 0
}
pcm.dmixer { ## This is a softward driven mixer, alsa's 'dmix'
	type dmix
	ipc_key 1024 ## this can be any unique value
	slave {
		pcm "hw:0,0" ## pointing to your card
		period_time 0
		period_size 2048 ## These options are tweakable,
		buffer_size 8192 ## but use powers of 2 for sizes
		rate 48000 ## the sample rate
		periods 518
	}
	bindings { ## this binds channel 'n's input to channel 'n' output
		0 0
		1 1
	}
}
pcm.!default { ## The default sound driver, a wrapper for dmixer
	type plug
	slave.pcm "dmixer"
}
```

I am running on board audio through usb_audio with ALSA.  If you want my hardware info, prepare to drink from the fire hose:

***lshw:***
```
ubuntu-comp
    description: Desktop Computer
    product: 939Dual-VSTA
    vendor: To Be Filled By O.E.M.
    version: To Be Filled By O.E.M.
    serial: To Be Filled By O.E.M.
    width: 32 bits
    capabilities: smbios-2.4 dmi-2.4
    configuration: boot=normal chassis=desktop uuid=00020003-0004-0005-0006-000700080009
  *-core
       description: Motherboard
       product: 939Dual-VSTA
       physical id: 0
     *-firmware
          description: BIOS
          vendor: American Megatrends Inc.
          physical id: 0
          version: P1.30 (09/25/2006)
          size: 64KB
          capacity: 448KB
          capabilities: pci upgrade shadowing cdboot bootselect socketedrom edd int13floppy1200 int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video acpi usb agp ls120boot zipboot biosbootspecification
     *-cpu
          description: CPU
          product: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          vendor: Advanced Micro Devices [AMD]
          physical id: 4
          bus info: cpu@0
          version: AMD Athlon(tm) 64 X2 Dual Core Processor 4800+
          serial: To Be Filled By O.E.M.
          slot: CPUSocket
          size: 1GHz
          capacity: 2400MHz
          width: 64 bits
          clock: 200MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush mmx fxsr sse sse2 ht syscall nx mmxext fxsr_opt x86-64 3dnowext 3dnow pni lahf_lm cmp_legacy cpufreq
        *-cache:0
             description: L1 cache
             physical id: 5
             slot: L1-Cache
             size: 256KB
             capacity: 256KB
             capabilities: pipeline-burst internal varies data
        *-cache:1
             description: L2 cache
             physical id: 6
             slot: L2-Cache
             size: 2MB
             capacity: 2MB
             capabilities: pipeline-burst internal varies unified
     *-memory
          description: System Memory
          physical id: 12
          slot: System board or motherboard
          size: 1GB
        *-bank:0
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum0
             vendor: Manufacturer0
             physical id: 0
             serial: SerNum0
             slot: DIMM0
             size: 512MB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:1
             description: DIMM DDR Synchronous 266 MHz (3.8 ns)
             product: PartNum1
             vendor: Manufacturer1
             physical id: 1
             serial: SerNum1
             slot: DIMM1
             size: 512MB
             width: 64 bits
             clock: 266MHz (3.8ns)
        *-bank:2
             description: DIMM [empty]
             product: PartNum2
             vendor: Manufacturer2
             physical id: 2
             serial: SerNum2
             slot: DIMM2
        *-bank:3
             description: DIMM [empty]
             product: PartNum3
             vendor: Manufacturer3
             physical id: 3
             serial: SerNum3
             slot: DIMM3
     *-pci:0
          description: Host bridge
          product: M1695 K8 Northbridge [PCI Express and HyperTransport]
          vendor: ALi Corporation
          physical id: 100
          bus info: pci@00:00.0
          version: 00
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: PCI Express Root Port
             vendor: ALi Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:1
             description: PCI bridge
             product: PCI Express Root Port
             vendor: ALi Corporation
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-pci:2
             description: PCI bridge
             product: AGP8X Controller
             vendor: ALi Corporation
             physical id: 5
             bus info: pci@00:05.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display:0
                description: VGA compatible controller
                product: Radeon R350 [Radeon 9800 Pro]
                vendor: ATI Technologies Inc
                physical id: 0
                bus info: pci@03:00.0
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                configuration: driver=fglrx_pci latency=255 mingnt=8
                resources: iomemory:d8000000-dfffffff ioport:e000-e0ff iomemory:f7ef0000-f7efffff irq:16
           *-display:1 UNCLAIMED
                description: Display controller
                product: Radeon R350 [Radeon 9800 Pro] (Secondary)
                vendor: ATI Technologies Inc
                physical id: 0.1
                bus info: pci@03:00.1
                version: 00
                size: 128MB
                width: 32 bits
                clock: 66MHz
                capabilities: bus_master cap_list
                configuration: latency=32 mingnt=8
                resources: iomemory:d0000000-d7ffffff iomemory:f7ee0000-f7eeffff
        *-pci:3
             description: PCI bridge
             product: M5249 HTT to PCI Bridge
             vendor: ALi Corporation
             physical id: 6
             bus info: pci@00:06.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master
           *-network
                description: Wireless interface
                product: AR5212 802.11abg NIC
                vendor: Atheros Communications, Inc.
                physical id: 6
                bus info: pci@04:06.0
                logical name: wifi0
                version: 01
                serial: 00:14:6c:85:78:3a
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath_pci driverversion=0.9.4.5 (0.9.3.1) ip=192.168.1.3 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11g
                resources: iomemory:f7ff0000-f7ffffff irq:21
        *-isa
             description: ISA bridge
             product: M1563 HyperTransport South Bridge
             vendor: ALi Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 70
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: driver=ali1563_smbus latency=0 maxlatency=24 mingnt=1
        *-bridge UNCLAIMED
             description: Bridge
             product: M7101 Power Management Controller [PMU]
             vendor: ALi Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             configuration: latency=0
        *-network
             description: Ethernet interface
             product: ULi 1689,1573 integrated ethernet.
             vendor: ALi Corporation
             physical id: 11
             bus info: pci@00:11.0
             logical name: eth0
             version: 40
             serial: 00:13:8f:c8:b0:e2
             capacity: 100MB/s
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=uli526x driverversion=0.9.3 latency=32 link=no maxlatency=40 mingnt=20 multicast=yes port=MII
             resources: ioport:d800-d8ff iomemory:f7dffc00-f7dffcff irq:17
        *-ide
             description: IDE interface
             product: M5229 IDE
             vendor: ALi Corporation
             physical id: 12
             bus info: pci@00:12.0
             version: c7
             width: 32 bits
             clock: 66MHz
             capabilities: ide bus_master
             configuration: driver=ALI15x3_IDE latency=32
             resources: iomemory:1f0-1f7 iomemory:3f0-3ef iomemory:170-177 iomemory:370-36f ioport:ff00-ff0f irq:19
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 66MHz
              *-disk
                   description: ATA Disk
                   product: SAMSUNG SP1604N
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: TM100-24
                   serial: S013J20WC29013
                   size: 149GB
                   capabilities: ata dma lba iordy smart security pm partitioned partitioned:dos
                   configuration: mode=udma5 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 146GB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      size: 2933MB
                      capacity: 2933MB
                      capabilities: primary extended partitioned partitioned:extended
                    *-logicalvolume
                         description: Linux swap / Solaris partition
                         physical id: 5
                         logical name: /dev/hda5
                         capacity: 2933MB
                         capabilities: nofs
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 66MHz
              *-cdrom
                   description: DVD writer
                   product: SONY DVD RW DW-Q28A
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: KYS1
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio cd-r cd-rw dvd dvd-r
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb:0
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 13
             bus info: pci@00:13.0
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:f7dfe000-f7dfefff irq:20
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
        *-usb:1
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 13.1
             bus info: pci@00:13.1
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:f7dfd000-f7dfdfff irq:21
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@2
                logical name: usb2
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb:0
                   description: Printer
                   product: HP LaserJet 2200
                   vendor: HewLett Packard
                   physical id: 1
                   bus info: usb@2:1
                   version: 1.00
                   serial: 00USBGG06524
                   capabilities: usb-1.10 ieee1284.4
                   configuration: driver=usblp maxpower=2mA speed=12.0MB/s
              *-usb:1
                   description: Mouse
                   product: PTZ-631W
                   vendor: Tablet
                   physical id: 2
                   bus info: usb@2:2
                   version: 1.09
                   capabilities: usb-1.10
                   configuration: driver=wacom maxpower=300mA speed=12.0MB/s
        *-usb:2
             description: USB Controller
             product: USB 1.1 Controller
             vendor: ALi Corporation
             physical id: 13.2
             bus info: pci@00:13.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: ohci bus_master
             configuration: driver=ohci_hcd latency=32 maxlatency=80
             resources: iomemory:f7dfc000-f7dfcfff irq:22
           *-usbhost
                product: OHCI Host Controller
                vendor: Linux 2.6.20-16-generic ohci_hcd
                physical id: 1
                bus info: usb@3
                logical name: usb3
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=3 speed=12.0MB/s
              *-usb
                   description: Audio device
                   product: PnP Audio Device
                   physical id: 2
                   bus info: usb@3:2
                   version: 0.10
                   capabilities: usb-1.10 audio-control
                   configuration: driver=snd-usb-audio maxpower=500mA speed=12.0MB/s
        *-usb:3
             description: USB Controller
             product: USB 2.0 Controller
             vendor: ALi Corporation
             physical id: 13.3
             bus info: pci@00:13.3
             version: 01
             width: 32 bits
             clock: 66MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=32 maxlatency=32 mingnt=16
             resources: iomemory:f7dff800-f7dff8ff irq:23
           *-usbhost
                product: EHCI Host Controller
                vendor: Linux 2.6.20-16-generic ehci_hcd
                physical id: 1
                bus info: usb@4
                logical name: usb4
                version: 2.06
                capabilities: usb-2.00
                configuration: driver=hub maxpower=0mA slots=8 speed=480.0MB/s
     *-pci:1
          description: Host bridge
          product: M1689 K8 Northbridge [Super K8 Single Chip]
          vendor: ALi Corporation
          physical id: 101
          bus info: pci@00:04.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:2
          description: Host bridge
          product: K8 [Athlon64/Opteron] HyperTransport Technology Configuration
          vendor: Advanced Micro Devices [AMD]
          physical id: 102
          bus info: pci@00:18.0
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:3
          description: Host bridge
          product: K8 [Athlon64/Opteron] Address Map
          vendor: Advanced Micro Devices [AMD]
          physical id: 103
          bus info: pci@00:18.1
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:4
          description: Host bridge
          product: K8 [Athlon64/Opteron] DRAM Controller
          vendor: Advanced Micro Devices [AMD]
          physical id: 104
          bus info: pci@00:18.2
          version: 00
          width: 32 bits
          clock: 33MHz
     *-pci:5
          description: Host bridge
          product: K8 [Athlon64/Opteron] Miscellaneous Control
          vendor: Advanced Micro Devices [AMD]
          physical id: 105
          bus info: pci@00:18.3
          version: 00
          width: 32 bits
          clock: 33MHz
```

---

### Post by whatisdot on 2007-09-18
BUMP BUMP
Hello?
Anyone here???
:confused:

---

### Post by whatisdot on 2007-09-19
Ok, well here's something to think about...

Every now and then the devices connected to the motherboard (not a USB Card.  I don't have one .) will mysteriously look as if the power has been cut to them.  Is this related to the sound issue???  I know the sound device says it runs through the USB Bus, so could that be related?

Has anyone even seen this thread...?

---

### Post by whatisdot on 2007-09-27
Bump...

---

### Post by mthei on 2007-09-28
My word probably means nothing, but I'll jump in anyway. Do you have MPD installed by any chance? Because I had this exact problem, based on your original post a while ago while I was using MPD exclusively, and for some reason I assumed that was the culprit  for the sound problems, as I had jumped from player to player since I started with Linux, and this has only happened to me with MPD, never before and never since. I don't know if this post was useful, but I hope you take care of this problem soon. It's a pain to keep having to reboot.

---

### Post by whatisdot on 2007-09-30
After some more searching, I believe I have [[COLOR="Blue"]_found a temporary solution_[/COLOR]]("http://ubuntuforums.org/showpost.php?p=3092820&postcount=15"), even though I don't know how or why...

After installing **asoundconf**, the problem has all but disappeared.  I think I have only had it happen once since installing it (several days ago) where the problem used to happen multiple times a day.  Don't understand it, but as long as it works fine, I really don't care!  Thanks to the community and to **mthei** for responding.  :)

---

### Post by whatisdot on 2007-10-08
Ok, the problem has resurfaced.  It is also coupled with inconsistencies with the file system that force me to run FSCK manually.  I get a weird display when the system's version of FSCK fails and tells me to run FSCK manually.  Once it fails again, I'll post the output.

---

### Post by MindFork on 2007-10-08
I have the same problem, but i am able to force quit the applications and reboot normally, which fixes the problem...for a while.

My sound device is an on motherboard Intel ICH5.

I'd like a way to just restart the sound drivers without rebooting, since I think it is a driver issue, and rebooting means reopening 20 windows of various apps that I use while working.

Anybody know an easy way to get sound working again without rebooting?

---

### Post by whatisdot on 2007-10-09
More info:

The problem happens, and I have to reboot.  I have to manually press the reset button on my case because the error sticks at "Shutting Down ALSA..."  I reboot and it says there are no problems, okay?  WELL, I forced a FSCK just to make sure when I rebooted and it gave me this:

```
/dev/hda1: UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY.
        (i.e., without -a or -p options)
fsck died with exit status 4
                                                                                    [[COLOR="Red"]fail[/COLOR]]
  [COLOR="Red"]*[/COLOR] An automatic file system check (fsck) of the root filesystem failed.
A manual fsck must be performed, then the system restarted.
The fsck should be performed in maintenance mode with the
root filesystem mounted in read-only mode.
  [COLOR="Orange"]*[/COLOR] The root filesystem is currently mounted in read-only mode.
A maintenance shell will now be started.
After performing system maintenance, press CONTROL-D
to terminate the maintenance shell and restart the system.
bash: no job control in this shell
bash: groups: command not found
bash: lesspipe: command not found
bash: The: command not found
The program 'apt-get' is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
bash: dircolors: command not found
bash: The: command not found
The program 'apt-get' is currently not installed.  You can install it by typing: apt-get install apt
bash: apt-get: command not found
root@ubuntu-comp:~#  _
```

I was confused why Ubuntu's own maintenance shell would be throwing errors at me (and weird errors, at that).  I run fsck manually.  It asks me all sorts of questions I don't know the answer to, to which I promptly press 'y'.  Most of them involve inodes, blocks and sizes.  (I honestly don't know why it requires you to run it manually if it gives you a bunch of verbose junk the average person won't understand anyway!)
I restart, it runs a check itself, which either succeeds or fails, in which case I have to run it manually again...Eventually it returns me to the login screen and we go through the whole mess again...

Thanks in advance to anyone daring enough to take on this issue!  :)

---

### Post by whatisdot on 2007-11-07
Ok, so I found out that my hard drive was acting up and eventually died.  =(
I got a nice new 300Gb SATA II hard drive, installed it with a fresh copy of Gutsy Gibbon.  I then followed the "Comprehensive sound problem" guide to get multiple voices with ALSA working, which was even easier than it used to be.  Everything was going fine, but I just noticed...

The problem persists...

I am quickly losing my faith in Ubuntu.  I want to believe, please help me believe...

---

