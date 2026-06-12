---
title: "Network Manager blank"
date: 2013-05-14
forum: Networking &amp; Wireless
---

### Post by cregy on 2013-05-14
Hi All

A couple of days ago wireless and wired networks were running fine. Now nothing works. The applet is blank. When I click on it, it shows a box that is ticked saying enable networking and also the word edit. The word information is greyed out. 

I ran iwconfig and it now shows no wireless extensions. They were running fine.

Thanks

Rich

---

### Post by praseodym on 2013-05-14
Start the applet from terminal with "gksu nm-connection-editor"

---

### Post by cregy on 2013-05-14
Thanks for the reply. I started the editor as suggested but that doesn't allow me to connect to any networks. It just allows me to edit the connections i have already made.

Here are some terminal results:

wild-woods@wildwoods-Satellite:~$ sudo ifconfig -a
[sudo] password for wild-woods: 
eth0      Link encap:Ethernet  HWaddr 00:c0:9f:c9:a5:d7  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2144 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2144 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:170416 (170.4 KB)  TX bytes:170416 (170.4 KB)

wild-woods@wildwoods-Satellite:~$ sudo lsmod
Module                  Size  Used by
joydev                 17162  0 
snd_intel8x0           33107  2 
snd_ac97_codec        105652  1 snd_intel8x0
ac97_bus               12671  1 snd_ac97_codec
snd_pcm                80235  2 snd_intel8x0,snd_ac97_codec
snd_seq_midi           13133  0 
snd_rawmidi            25383  1 snd_seq_midi
snd_seq_midi_event     14476  1 snd_seq_midi
snd_seq                51281  2 snd_seq_midi,snd_seq_midi_event
parport_pc             31969  0 
pcmcia                 39545  0 
snd_timer              24412  2 snd_pcm,snd_seq
ppdev                  12818  0 
rfcomm                 37277  0 
microcode              18210  0 
snd_seq_device         14138  3 snd_seq_midi,snd_rawmidi,snd_seq
bnep                   17708  2 
bluetooth             183270  10 rfcomm,bnep
snd                    62146  11 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
binfmt_misc            17261  1 
soundcore              14600  1 snd
psmouse                84878  0 
snd_page_alloc         14037  2 snd_intel8x0,snd_pcm
serio_raw              13032  0 
sbs                    13336  0 
yenta_socket           27096  0 
pcmcia_rsrc            18192  1 yenta_socket
pcmcia_core            21506  3 pcmcia,yenta_socket,pcmcia_rsrc
sbshc                  13515  1 sbs
i915                  457241  2 
mac_hid                13038  0 
drm_kms_helper         47304  1 i915
ext2                   67205  1 
lpc_ich                16926  0 
drm                   238811  3 i915,drm_kms_helper
i2c_algo_bit           13198  1 i915
shpchp                 32190  0 
video                  18895  1 i915
lp                     13300  0 
parport                40754  3 parport_pc,ppdev,lp
8139too                23072  0 
8139cp                 26620  0 
wild-woods@wildwoods-Satellite:~$ sudo lshw
wildwoods-satellite       
    description: Notebook
    product: Satellite PRO L10
    vendor: TOSHIBA
    version: PSL15E-00U003EN
    serial: 95030292W
    width: 32 bits
    capabilities: smbios-2.31 dmi-2.31
    configuration: boot=oem-specific chassis=notebook uuid=00C8D2FE-A789-D811-AC93-00C09FC9A5D7
  *-core
       description: Motherboard
       product: Satellite PRO L10
       vendor: TOSHIBA
       physical id: 0
       version: Rev 1.0
       serial: 95030292W
     *-firmware
          description: BIOS
          vendor: TOSHIBA
          physical id: 0
          version: V2.40
          date: 06/22/2005
          size: 107KiB
          capacity: 448KiB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing escd cdboot int13floppy720 int5printscreen int9keyboard int14serial int17printer acpi usb smartbattery biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Celeron(R) M processor         1.60GHz
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.13.8
          slot: uFCPGA2
          size: 1600MHz
          capacity: 1600MHz
          width: 32 bits
          clock: 400MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov clflush dts acpi mmx fxsr sse sse2 ss tm pbe nx up bts
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KiB
             capacity: 32KiB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 1MiB
             capacity: 1MiB
             capabilities: burst external write-back
     *-memory
          description: System Memory
          physical id: 10
          slot: System board or motherboard
          size: 1GiB
          capacity: 3GiB
        *-bank:0
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 0
             slot: DIMM 0
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
        *-bank:1
             description: DIMM SRAM Synchronous 333 MHz (3.0 ns)
             physical id: 1
             slot: DIMM 1
             size: 512MiB
             width: 64 bits
             clock: 333MHz (3.0ns)
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
             capabilities: pm vga_controller bus_master cap_list rom
             configuration: driver=i915 latency=0
             resources: irq:6 memory:e8000000-efffffff memory:e0000000-e007ffff ioport:1800(size=8)
        *-display:1 UNCLAIMED
             description: Display controller
             product: 82852/855GM Integrated Graphics Device
             vendor: Intel Corporation
             physical id: 2.1
             bus info: pci@0000:00:02.1
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0
             resources: memory:f0000000-f7ffffff memory:e0080000-e00fffff
        *-usb:0
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:6 ioport:1820(size=32)
        *-usb:1
             description: USB controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:6 ioport:1840(size=32)
        *-usb:2
             description: USB controller
             product: 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci_hcd latency=0
             resources: irq:10 memory:e0100000-e01003ff
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
             resources: ioport:3000(size=4096) memory:e0200000-e04fffff memory:40000000-43ffffff
           *-pcmcia
                description: CardBus bridge
                product: PCI1410 PC card Cardbus Controller
                vendor: Texas Instruments
                physical id: 1
                bus info: pci@0000:02:01.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=192
                resources: irq:10 memory:e0400000-e0400fff ioport:3000(size=256) ioport:3400(size=256) memory:40000000-43ffffff memory:48000000-4bffffff
           *-network:0
                description: Ethernet interface
                product: RTL-8139/8139C/8139C+
                vendor: Realtek Semiconductor Co., Ltd.
                physical id: 2
                bus info: pci@0000:02:02.0
                logical name: eth0
                version: 10
                serial: 00:c0:9f:c9:a5:d7
                size: 10Mbit/s
                capacity: 100Mbit/s
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
                configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=64 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10Mbit/s
                resources: irq:6 ioport:3800(size=256) memory:e0401800-e04018ff
           *-network:1 UNCLAIMED
                description: Ethernet controller
                product: IPN 2220 802.11g
                vendor: InProComm Inc.
                physical id: 4
                bus info: pci@0000:02:04.0
                version: 00
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: latency=64 maxlatency=32 mingnt=32
                resources: ioport:3c00(size=32) memory:e0401c00-e0401c1f memory:e0401000-e04017ff
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
             resources: irq:6 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1810(size=16) memory:44000000-440003ff
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
             resources: ioport:1860(size=32)
        *-multimedia
             description: Multimedia audio controller
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: driver=snd_intel8x0 latency=0
             resources: irq:11 ioport:1c00(size=256) ioport:1880(size=64) memory:e0100c00-e0100dff memory:e0100800-e01008ff
        *-communication UNCLAIMED
             description: Modem
             product: 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller
             vendor: Intel Corporation
             physical id: 1f.6
             bus info: pci@0000:00:1f.6
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm generic cap_list
             configuration: latency=0
             resources: ioport:2400(size=256) ioport:2000(size=128)
     *-scsi:0
          physical id: 1
          logical name: scsi0
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: TOSHIBA MK4025GA
             vendor: Toshiba
             physical id: 0.0.0
             bus info: scsi@0:0.0.0
             logical name: /dev/sda
             version: KA10
             serial: 85OP6126T
             size: 37GiB (40GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000c4562
           *-volume:0
                description: Linux filesystem partition
                vendor: Linux
                physical id: 1
                bus info: scsi@0:0.0.0,1
                logical name: /dev/sda1
                logical name: /boot
                version: 1.0
                serial: 0d1e28bb-d7b0-407f-82b5-56755d6adf92
                size: 243MiB
                capacity: 243MiB
                capabilities: primary bootable ext2 initialized
                configuration: filesystem=ext2 modified=2013-05-14 18:37:55 mount.fstype=ext2 mount.options=rw,relatime,errors=continue state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@0:0.0.0,2
                logical name: /dev/sda2
                size: 37GiB
                capacity: 37GiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux LVM Physical Volume partition
                   physical id: 5
                   logical name: /dev/sda5
                   serial: KHWimo-eAhj-3nXY-17gF-wX3v-2vq2-OOGJM3
                   size: 37GiB
                   capacity: 37GiB
                   capabilities: multi lvm2
     *-scsi:1
          physical id: 2
          logical name: scsi1
          capabilities: emulated
        *-cdrom
             description: DVD reader
             product: UJDA760 DVD/CDRW
             vendor: MATSHITA
             physical id: 0.0.0
             bus info: scsi@1:0.0.0
             logical name: /dev/cdrom
             logical name: /dev/cdrw
             logical name: /dev/dvd
             logical name: /dev/sr0
             version: 1.51
             capabilities: removable audio cd-r cd-rw dvd
             configuration: ansiversion=5 status=nodisc
  *-battery
       description: Lithium-Ion Battery
       product: Sanyo
       vendor: Sanyo
       physical id: 1
       slot: Right Side
       capacity: 4400mWh
       configuration: voltage=14.8V
wild-woods@wildwoods-Satellite:~$ 

Thanks

Rich

---

### Post by praseodym on 2013-05-14
There are two drivers loaded for LAN:
```

sudo modprobe -rfv 8139too
sudo modprobe -rfv 8139cp
sudo modprobe -v 8139too
echo "blacklist 8139cp" | sudo tee -a /etc/modprobe.d/blacklist.conf
```
There is no wireless device shown. Please show:
```

lspci -nnk
lsusb
pccardctl info
```

---

### Post by cregy on 2013-05-15
Hi

Thanks so much for the help. Your reply help me realise that ndiswrapper was not working. I had loaded 1.58 beta and an upgrade had overwritten this and put it back to 1.57. I therefore reinstalled 1.58 and all is fine now.

Rich

---

