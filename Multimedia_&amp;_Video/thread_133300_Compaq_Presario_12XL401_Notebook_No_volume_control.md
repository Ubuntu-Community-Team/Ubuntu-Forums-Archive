---
title: "Compaq Presario 12XL401 Notebook No volume control elements and/or devices found"
date: 2006-02-19
forum: Multimedia &amp; Video
---

### Post by linuxusr50 on 2006-02-19
All,

I am having sound problems on a first time install of unbuntu on a Compaq Persario 12XL401 Notebook.

The kernel appears to have detected the sound device but nothing detects it.  I have noticed there is no /dev/dsp  or /dev/audio.  I have tried to create the devices with /dev/MAKEDEV with no success.

Any application I try to run that requires sound reports that no sound device is present.Sound server informational message:

**Here is the error when trying to run amorak:**
Error while initializing the sound driver:
device /dev/dsp can't be opened (No such file or directory)
The sound server will continue, using the null output device.

**Here is the error I get when clicking the volume control on the launcher:**
No volume control elements and/or devices found.

I am including information I believe will be pertinant to the post.  I anyone needs additional info let me know.

**lsmod**
....<snip>
snd_seq_dummy           3844  0
snd_seq_oss            29440  0
snd_seq_midi            8608  0
snd_seq_midi_event      6656  2 snd_seq_oss,snd_seq_midi
snd_seq                44688  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_via82xx            25792  0
gameport               14472  1 snd_via82xx
snd_ac97_codec         72188  1 snd_via82xx
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_seq,snd_pcm
snd_page_alloc         10120  2 snd_via82xx,snd_pcm
snd_mpu401_uart         6784  1 snd_via82xx
snd_rawmidi            22816  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8204  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
snd                    48644  11 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore               9184  1 snd
via686a                17816  0
<snip>.....


**dmesg**
.....<snip>
[4294720.843000] AC'97 0 access is not valid [0xffffffff], removing mixer.
[4294720.843000] ACPI: PCI interrupt for device 0000:00:07.5 disabled
[4294720.843000] VIA 82xx Audio: probe of 0000:00:07.5 failed with error -5
<snip>.....



**lshw**
    description: Notebook
    product: Presario 12XL401 470009-230
    vendor: Compaq
    version: 0F08
    serial: 6D11JC523116
    width: 32 bits
    capabilities: smbios-2.3 dmi-2.3
    configuration: chassis=notebook
  *-core
       description: Motherboard
       product: 06E0h
       vendor: Compaq
       physical id: 0
       version: Rev.A
       serial: None
     *-firmware
          description: BIOS
          vendor: Phoenix Technologies LTD
          physical id: 0
          version: 4.06 (12/08/2000)
          size: 85KB
          capacity: 448KB
          capabilities: pci pcmcia pnp upgrade shadowing cdboot bootselect int5printscreen int9keyboard int14serial int17printer int10video acpi agp biosbootspecification
     *-cpu
          description: CPU
          product: Celeron (Coppermine)
          vendor: Intel Corp.
          physical id: 4
          bus info: cpu@0
          version: 6.8.6
          slot: Socket 370
          size: 700MHz
          capacity: 850MHz
          width: 32 bits
          clock: 100MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep
mtrr pge mca cmov pat pse36 mmx fxsr sse
        *-cache:0
             description: L1 cache
             physical id: 8
             slot: L1 Cache
             size: 32KB
             capacity: 128KB
             capabilities: asynchronous internal write-back
        *-cache:1
             description: L2 cache
             physical id: 9
             slot: L2 Cache
             size: 128KB
             capacity: 1MB
             capabilities: burst internal write-through
     *-memory
          description: System Memory
          physical id: b
          slot: System board or motherboard
          size: 192MB
          capacity: 384MB
        *-bank:0
             description: DIMM DRAM Synchronous
             physical id: 0
             slot: M1
             size: 64MB
             width: 32 bits
        *-bank:1
             description: DIMM DRAM Synchronous
             physical id: 1
             slot: M2
             size: 128MB
             width: 32 bits
     *-pci
          description: Host bridge
          product: VT8601 [Apollo ProMedia]
          vendor: VIA Technologies, Inc.
          physical id: f8000000
          bus info: pci@00:00.0
          version: 05
          width: 32 bits
          clock: 33MHz
          resources: iomemory:f8000000-fbffffff
        *-pci
             description: PCI bridge
             product: VT8601 [Apollo ProMedia AGP]
             vendor: VIA Technologies, Inc.
             physical id: 1
             bus info: pci@00:01.0
             version: 00
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master cap_list
           *-display
                description: VGA compatible controller
                product: CyberBlade i1
                vendor: Trident Microsystems
                physical id: 0
                bus info: pci@01:00.0
                version: 6a
                size: 8MB
                width: 32 bits
                clock: 66MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:f5000000-f57fffff iomemory:f4100000-f411ffff iomemory:f4800000-f4ffffff irq:9
        *-isa
             description: ISA bridge
             product: VT82C686 [Apollo Super South]
             vendor: VIA Technologies, Inc.
             physical id: 7
             bus info: pci@00:07.0
             version: 22
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=parport_pc
        *-ide
             description: IDE interface
             product: VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE
             vendor: VIA Technologies, Inc.
             physical id: 7.1
             bus info: pci@00:07.1
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master cap_list
             configuration: driver=VIA_IDE
             resources: ioport:1420-142f
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: HITACHI_DK23BA-15
                   vendor: Hitachi
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: 00E1A0A0
                   serial: 10C6ZU
                   size: 14GB
                   capacity: 14GB
                   capabilities: ata dma lba iordy smart security pm apm
                   configuration: apm=off mode=udma2 smart=on
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: TOSHIBA DVD-ROM SD-C2502
                   vendor: Toshiba
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 1007
                   serial: Z000204319
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
        *-usb
             description: USB Controller
             product: VT82xxxxx UHCI USB 1.1 Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.2
             bus info: pci@00:07.2
             version: 10
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master cap_list
             configuration: driver=uhci_hcd
             resources: ioport:1400-141f irq:11
           *-usbhost
                product: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller
                vendor: Linux 2.6.12-10-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge UNCLAIMED
             description: Bridge
             product: VT82C686 [Apollo Super ACPI]
             vendor: VIA Technologies, Inc.
             physical id: 7.4
             bus info: pci@00:07.4
             version: 30
             width: 32 bits
             clock: 33MHz
             capabilities: bridge cap_list
             resources: irq:10
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: VT82C686 AC97 Audio Controller
             vendor: VIA Technologies, Inc.
             physical id: 7.5
             bus info: pci@00:07.5
             version: 20
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: ioport:1000-10ff ioport:1434-1437 ioport:1430-1433 irq:9        *-communication UNCLAIMED
             description: Communication controller
             product: HSF 56k Data/Fax Modem
             vendor: Conexant
             physical id: 9
             bus info: pci@00:09.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: cap_list
             resources: iomemory:f4000000-f400ffff ioport:1438-143f irq:11
        *-pcmcia
             description: CardBus bridge
             product: PCI1410 PC card Cardbus Controller
             vendor: Texas Instruments
             physical id: b
             bus info: pci@00:0b.0
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:bc00000-bc00fff irq:11
           *-network
                description: Instant Wireless Network PC Card
                product: ISL37300P
                vendor: The Linksys Group, Inc.
                physical id: 0
                version: RevA
                slot: Socket 0
                resources: irq:3
  *-network
       description: Wireless interface
       physical id: 1
       logical name: eth0
       serial: 00:06:25:18:8b:d4
       capabilities: ethernet physical wireless
       configuration: broadcast=yes ip=10.8.26.100 multicast=yes wireless=IEEE 802.11-DS
(END)

---

### Post by Ptero-4 on 2006-02-19
By the dmesg description I can tell that your PC is incorrectly reporting it's soundcard port and the ubuntu kernel is having troubles locating where the soundcard is and can't load it.

---

### Post by linuxusr50 on 2006-02-19
**Update:**

uname -sr **Linux 2.6.12-10-386**


I was able to create a /dev/audio and /dev/dsp however it has not made any improvement.  Shows "no such device" when trying to direct any file to the device.
example:  cat [path]/[file name] > /dev/audio
or cat [path]/[file name] > /dev/dsp

I do have the have the multimedia systems selector set to dsp and when I test I get the following error:

Failed to construct test pipeline for 'ESD - Enlightenment Sound Daemon'

I get similar errors when trying ALSA and OSS.

Thanks for any help,
Dan

---

