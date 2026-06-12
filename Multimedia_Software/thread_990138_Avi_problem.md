---
title: "Avi problem"
date: 2008-11-22
forum: Multimedia Software
---

### Post by Brennagan on 2008-11-22
I am new to ubuntu but i cant seem to get avis working for the life of me. I read a few threads tried to sticky at the top installed the ubuntu resticted thing and vlc is there anything else I need to do or am I doing something wrong? I have 5 different avi files to test on to make sure its not a wrong file, and im on 8.04.1 thanks in advance

---

### Post by SIGTERMer on 2008-11-22
vlc should do the trick, just make sure that vlc is the default program that handles this type of file. you can do this by right-clicking the avi file and choosing properties, then choose the "open with" tab. you should find vlc with them. if that isn't so, click add, then write "vlc" as a custom command.
hope this helps :)

---

### Post by Brennagan on 2008-11-22
Nope it plays the sound but just shows a black or occasionally blue screen.

---

### Post by Bruce M. on 2008-11-22
> **Brennagan said:**
> I am new to ubuntu but i cant seem to get avis working for the life of me. I read a few threads tried to sticky at the top installed the ubuntu resticted thing and vlc is there anything else I need to do or am I doing something wrong? I have 5 different avi files to test on to make sure its not a wrong file, and im on 8.04.1 thanks in advance

Try QuickStart in my signature and run option #11.

Keep me posted here.
Bruce

---

### Post by Brennagan on 2008-11-22
Doh im blind i found it get me a bit to run it and  such

---

### Post by Brennagan on 2008-11-22
Ok i installed it and ran option 11 and it seemed to download the codecs and such correctly but then i tried to view the movies with vlc xine and movie player to no avail still black or blue screen, even restarted hoping that would help.

---

### Post by Bruce M. on 2008-11-22
> **Brennagan said:**
> Ok i installed it and ran option 11 and it seemed to download the codecs and such correctly but then i tried to view the movies with vlc xine and movie player to no avail still black or blue screen, even restarted hoping that would help.

Hmmm, I was sure that would do it.
Dis you see this: [[SOLVED] .avi files don't play]("http://ubuntuforums.org/showthread.php?t=931892")

Bruce

---

### Post by Brennagan on 2008-11-22
I fixed it i just reinstalled linux and this time they worked right after the gstreamer codecs weird lol im happy now tho

---

### Post by Tomatz on 2008-11-22
Out of interest is your gpu an intel 9xx?

---

### Post by Brennagan on 2008-11-22
Not sure lol how could I check? Anyways i have another problem now i tried hooking it to my tv like usual and the vid would play on the tv but not on the laptop so i unplugged it and still not, and now if i try to open it with vlc it plays the sound but makes my whole screen go white and no movie. Thanks in advance, I think it may have something to do with my resolution

---

### Post by Brennagan on 2008-11-22
Any suggestions?

---

### Post by SIGTERMer on 2008-11-22
try this:
vlc --reset-config

---

### Post by Tomatz on 2008-11-23
First we will need to know what graphics card/gpu you have.


;)

---

### Post by Brennagan on 2008-11-23
vlc reset config doesnt work and how can i check what graphics card and such i have.

---

### Post by Tomatz on 2008-11-23
Open a terminal then type **lshw**.

Post the output of the command here.

---

### Post by Brennagan on 2008-11-23
```
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 0
          size: 1001MiB
     *-cpu
          product: Intel(R) Pentium(R) Dual  CPU  T2390  @ 1.86GHz
          vendor: Intel Corp.
          physical id: 1
          bus info: cpu@0
          version: 6.15.13
          serial: 0000-06FD-0000-0000-0000-0000
          size: 1867MHz
          capacity: 1867MHz
          width: 64 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe nx x86-64 constant_tsc arch_perfmon pebs bts pni monitor ds_cpl est tm2 ssse3 cx16 xtpr lahf_lm cpufreq
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
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel module=intel_agp
        *-display:0 UNCLAIMED
             description: VGA compatible controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list
             configuration: latency=0
        *-display:1 UNCLAIMED
             description: Display controller
             product: Mobile GM965/GL960 Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 0c
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: latency=0
        *-usb:0
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:1
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:2
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 02
             width: 64 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=HDA Intel latency=0 module=snd_hda_intel
        *-pci:0
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Ethernet interface
                product: 88E8040 PCI-E Fast Ethernet Controller
                vendor: Marvell Technology Group Ltd.
                physical id: 0
                bus info: pci@0000:09:00.0
                logical name: eth0
                version: 12
                serial: 00:21:9b:da:22:7a
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A ip=149.159.8.7 latency=0 module=sky2 multicast=yes
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
           *-network
                description: Wireless interface
                product: BCM4312 802.11b/g
                vendor: Broadcom Corporation
                physical id: 0
                bus info: pci@0000:0b:00.0
                logical name: eth1
                version: 01
                serial: 00:1f:e1:70:ca:5b
                width: 64 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=wl latency=0 module=wl multicast=yes wireless=IEEE 802.11
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master cap_list
             configuration: driver=pcieport-driver
        *-usb:3
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:4
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:5
             description: USB Controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0 module=uhci_hcd
        *-usb:6
             description: USB Controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0 module=ehci_hcd
        *-pci:3
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f2
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 9
                bus info: pci@0000:02:09.0
                version: 05
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=ohci1394 latency=64 maxlatency=4 mingnt=2 module=ohci1394
           *-system:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.1
                bus info: pci@0000:02:09.1
                version: 22
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: driver=sdhci latency=64 module=sdhci
           *-system:1 UNCLAIMED
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 9.2
                bus info: pci@0000:02:09.2
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
           *-system:2 UNCLAIMED
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 9.3
                bus info: pci@0000:02:09.3
                version: 12
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list
                configuration: latency=64
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0 module=ata_piix
        *-storage
             description: SATA controller
             product: 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: storage ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0 module=ahci
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 02
             width: 32 bits
             clock: 33MHz
             configuration: latency=0

```

---

### Post by Tomatz on 2008-11-23
Intel :)

To fix the problem you will probably have to run the video in X11 output. This is due to a bug with the intel driver.

You cant do this in gstreamer/totem but you can do it in mplayer and vlc.

To do this in **VLC**

Open **VLC**

In vlc click **settings** then **preferences**

Check **advanced options** (bottom rh)

Drop down **Video** (lh side)

Select **output modules**

Select **X11 video output** (in the dropdown box on the rh side **_NOT_** the lh side)

**Save** close and play your video 



Hope that helps  ;)

---

### Post by Brennagan on 2008-11-23
That worked thanks a ton lol

---

### Post by Tomatz on 2008-11-23
> **Brennagan said:**
> That worked thanks a ton lol


Thats cool :)

Its a long standing problem with the intel drivers. It should have been fixed by now to be honest.

---

