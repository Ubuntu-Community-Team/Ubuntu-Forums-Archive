---
title: "how do i install this theme?"
date: 2010-10-22
forum: Multimedia Software
---

### Post by catlover2 on 2010-10-22
hi,

i installed this theme called BlueSpace ll,([http://gnome-look.org/content/show.php/BlueSpace+II?content=78633](http://gnome-look.org/content/show.php/BlueSpace+II?content=78633))

and i am wondering  how to get the transparency enabled.

i included a screenshot of what i have so far.

thanks,

catlover

---

### Post by rattamayhorka on 2010-10-22
is needed more data about your problem: do you have installed compiz? do you have 3d ecceleration card? run this command in the gnome-terminal and post the result (this is to know about your hardware):
lshw

---

### Post by catlover2 on 2010-10-23
Hi, and thanks for the response.

No, I do not have compiz installed.

lshw:
```
reed@reeds-Satellite-M30X-laptop:~$ lshw
WARNING: you should run this program as super-user.
reeds-satellite-m30x-laptop
    description: Computer
    width: 32 bits
  *-core
       description: Motherboard
       physical id: 0
     *-memory
          description: System memory
          physical id: 1
          size: 463MiB
     *-cpu
          product: Intel(R) Celeron(R) M processor         1.40GHz
          vendor: Intel Corp.
          physical id: 2
          bus info: cpu@0
          version: 6.13.8
          size: 1400MHz
          width: 32 bits
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe up bts
     *-pci
          description: Host bridge
          product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          configuration: driver=agpgart-intel
          resources: irq:0
        *-generic:0 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.1
             bus info: pci@0000:00:00.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-generic:1 UNCLAIMED
             description: System peripheral
             product: 82852/82855 GM/GME/PM/GMV Processor to I/O Controller
             vendor: Intel Corporation
             physical id: 0.3
             bus info: pci@0000:00:00.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master
             configuration: latency=0
        *-display:0
             description: VGA compatible controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:16 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:1820(size=32)
        *-usb:1
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:19 ioport:1840(size=32)
        *-usb:2
             description: USB Controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:1860(size=32)
        *-usb:3
             description: USB Controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:23 memory:e0100000-e01003ff
        *-pci
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: 83
             width: 32 bits
             clock: 33MHz
             capabilities: pci normal_decode bus_master
             resources: ioport:3000(size=4096) memory:e0200000-e02fffff memory:20000000-23ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
                vendor: VIA Technologies, Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                version: 80
                width: 32 bits
                clock: 33MHz
                capabilities: ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=32
                resources: irq:20 memory:e0210000-e02107ff ioport:3400(size=128)
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 1
                bus info: pci@0000:02:01.0
                logical name: eth0
                version: 10
                serial: 00:0f:b0:9a:e0:e3
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical
                configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=32 maxlatency=64 mingnt=32 multicast=yes
                resources: irq:21 ioport:3000(size=256) memory:e0210800-e02108ff
           *-network:1
                description: Wireless interface
                product: Atheros AR5001X+ Wireless Network Adapter
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: wlan0
                version: 01
                serial: 00:11:f5:7e:70:64
                width: 32 bits
                clock: 33MHz
                capabilities: bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=ath5k driverversion=2.6.35-22-generic firmware=N/A ip=192.168.2.1 latency=168 maxlatency=28 mingnt=10 multicast=yes wireless=IEEE 802.11bg
                resources: irq:22 memory:e0200000-e020ffff
           *-pcmcia
                description: CardBus bridge
                product: CB1410 Cardbus Controller
                vendor: ENE Technology Inc
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 01
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5
                resources: irq:16 memory:e0211000-e0211fff ioport:3800(size=256) ioport:3c00(size=256) memory:20000000-23ffffff memory:28000000-2bffffff
        *-isa
             description: ISA bridge
             product: 82801DBM (ICH4-M) LPC Interface Bridge
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master
             configuration: latency=0
        *-ide
             description: IDE interface
             product: 82801DBM (ICH4-M) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:18 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:24000000-240003ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: ioport:1880(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: bus_master cap_list
             configuration: driver=Intel ICH latency=0
             resources: irq:17 ioport:1c00(size=256) ioport:18c0(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-usb:0
          description: USB Controller
          product: VT82xxxxx UHCI USB 1.1 Controller
          vendor: VIA Technologies, Inc.
          physical id: 0
          bus info: pci@0000:03:00.0
          version: 62
          width: 32 bits
          clock: 33MHz
          capabilities: uhci bus_master cap_list
          configuration: driver=uhci_hcd latency=22
          resources: irq:16 ioport:3880(size=32)
     *-usb:1
          description: USB Controller
          product: USB 2.0
          vendor: VIA Technologies, Inc.
          physical id: 0.2
          bus info: pci@0000:03:00.2
          version: 65
          width: 32 bits
          clock: 33MHz
          capabilities: ehci bus_master cap_list
          configuration: driver=ehci_hcd latency=22
          resources: irq:16 memory:28000800-280008ff
     *-firewire
          description: FireWire (IEEE 1394)
          product: VT6306/7/8 [Fire II(M)] IEEE 1394 OHCI Controller
          vendor: VIA Technologies, Inc.
          physical id: 0.3
          bus info: pci@0000:03:00.3
          version: 80
          width: 32 bits
          clock: 33MHz
          capabilities: ohci bus_master cap_list
          configuration: driver=firewire_ohci latency=64 maxlatency=32
          resources: irq:16 memory:28000000-280007ff ioport:3800(size=128)
  *-scsi:0
       physical id: 1
       bus info: scsi@2
       logical name: scsi2
       capabilities: scsi-host
       configuration: driver=usb-storage
  *-scsi:1
       physical id: 2
       bus info: scsi@3
       logical name: scsi3
       capabilities: scsi-host
       configuration: driver=usb-storage
reed@reeds-Satellite-M30X-laptop:~$ 

```

---

### Post by rattamayhorka on 2010-10-23
look at this post [http://ubuntuforums.org/showthread.php?t=1464239]("http://ubuntuforums.org/showthread.php?t=1464239") they talk about how to configure your graphics card

you can enable the transpaency with compiz and only if you have 3d acceleration card installed properly

---

### Post by catlover2 on 2010-10-23
hi, 
can you give me some instructions on how to install the driver?

thanks,

catlover

---

### Post by rattamayhorka on 2010-10-24
> **catlover2 said:**
> hi, 
can you give me some instructions on how to install the driver?

thanks,

catlover

the link is this sorry about it

[http://ubuntuforums.org/showthread.php?t=1464239](http://ubuntuforums.org/showthread.php?t=1464239)

in that post explain how to install it...

you need to add a ppa repository to get the drivers for this, run this command in a terminal:

sudo add-apt-repository ppa:glasen/intel-driver

Step 2: Open a terminal and enter:

Your system will now fetch the PPA's key. This enables your Ubuntu system to verify that the packages in the PPA have not been interfered with since they were built.

Step 3: Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:

sudo apt-get update

Now you need to add that key to your system so Ubuntu can verify the packages from the PPA. In your terminal, enter:

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 066ADE1D

This will now pull down the PPA's key and add it to your system.

Step 7: Now, as a one-off, you should tell your system to pull down the latest list of software from each archive it knows about, including the PPA you just added:

sudo apt-get update

Now you're ready to start installing software from the PPA!

for update your packages run this in the terminal:

sudo apt-get upgrade

---

### Post by catlover2 on 2010-10-24
ok,

is there any way to verify that the driver is installed?

and in CompizConfig settings manager, how do i enable transparency?

thanks,
catlover

---

### Post by rattamayhorka on 2010-10-24
run this command to see in the xorg·conf the driver you have

cat /etc/X11/xorg.conf | grep Driver

if not look at this xorg log: 
sistema > administracion > sucesos del sistema > xorg.0.log (in the left dropdown menu)

for the transparency in the CompizConfig settings manager you need  to enable it like the screenshots, the second is for expecified windows transparency

---

### Post by catlover2 on 2010-10-24
when i run the command i get this:
```
reed@reeds-Satellite-M30X-laptop:~$ cat /etc/X11/xorg.conf | grep Driver
cat: /etc/X11/xorg.conf: No such file or directory
reed@reeds-Satellite-M30X-laptop:~$ 

```

and i see no "System Events in the admin menu.

muchas gracias!

catlover

---

