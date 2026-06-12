---
title: "Completely Lost on Audio"
date: 2006-09-03
forum: Multimedia &amp; Video
---

### Post by Tomtheman70 on 2006-09-03
Ok, I followed the thread on the top of this subsection about using ALSA and all of that, and I managed to get to step 4 and add my driver (snd-cs46xx) to the etc/modules/ then I tried getting the alsamixer using sudo apt-get install alsamixer-gui and I got a couple errors.

```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 2 during global destruction.

```
I don't know exactly what this means but my sound driver still doesn't work and nor does alsamixer. When I try and run it, it comes up with the error 'alsamixer: function snd_ctl_open failed for default: No such device' 

I believe my sound driver isn't working because when I try and use the Xfmedia to play some mp3 files they don't play, they don't even start, actually.


I've been working on this for about 2 days now and this is really starting to give me a headache, is there someone generous enough on this board to help me with my issue so I can get some sound on this laptop?


Also: I haven't gotten around to getting video to work either so when this problem is solved I'll be pleading for help again.

-Tom

---

### Post by foolsh on 2006-09-03
after you added the driver to modules did you reboot?
these modules will be loaded at boot time
to load the module "on the fly" use
```
sudo modprobe modulename
```
note to remove a module use 
```
sudo rmmod modulename
```
if you could, in a terminal, run the command lspci
and paste the output here for us to see please

---

### Post by Tomtheman70 on 2006-09-03
Ok, I rebooted, I hadn't done that yet. Now here is the lspci output code:```
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02)
0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12)
0000:06:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)

```
I still don't really know if the driver is working correctly or not because I have no codecs of any kind. Is there some big pack of them I can install?


EDIT: Now it would seem no matter what I try to get from 'sudo apt-get install xxxxxx' I always get this error:```
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 166
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 2 during global destruction.

```

---

### Post by foolsh on 2006-09-03
as far as codecs are concerned here is a link that will lead you in the right direction [http://ubuntuguide.org/wiki/Ubuntu_dapper](http://ubuntuguide.org/wiki/Ubuntu_dapper)

i get those same errors as well just ingnore them for the time being im sure someone will fix this in future releases 

i would like to know if you get any sound at all during startup or login anything at all?

---

### Post by Tomtheman70 on 2006-09-03
No sound at all, not even when booting. I know my hardware sound is not muted because the beeps coming from the motherboard are quite loud (Changing the volume on boot to see if the drivers are working)

---

### Post by foolsh on 2006-09-03
ok so how far did you get in the Comprehensive Sound Problem Solutions Guide 
give me details so i can follow along lets start with step 1
aplay -l 
post the output

---

### Post by Tomtheman70 on 2006-09-03
tom@laptop:~$ aplay -l
aplay: device_list:221: no soundcards found...
tom@laptop:~$


Thats an improvement though, because before I did all the steps, all that came up was '>'


Step 2: Type in lspci -v

```
tom@laptop:~$ lspci -v
0000:00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 02)
        Flags: bus master, medium devsel, latency 64
        Memory at 40000000 (32-bit, prefetchable) [size=64M]
        Capabilities: <available only to root>

0000:00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, 66MHz, medium devsel, latency 168
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=176
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: 70000000-dfffffff
        Prefetchable memory behind bridge: e0000000-f7ffffff

0000:00:02.0 CardBus bridge: Texas Instruments PCI1251A
        Subsystem: IBM: Unknown device 00eb
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50102000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=02, subordinate=05, sec-latency=176
        Memory window 0: 10000000-11fff000 (prefetchable)
        Memory window 1: 12000000-13fff000
        I/O window 0: 00001000-000010ff
        I/O window 1: 00001400-000014ff
        16-bit legacy interface ports at 0001

0000:00:02.1 CardBus bridge: Texas Instruments PCI1251A
        Subsystem: IBM: Unknown device 00eb
        Flags: bus master, medium devsel, latency 168, IRQ 11
        Memory at 50101000 (32-bit, non-prefetchable) [size=4K]
        Bus: primary=00, secondary=06, subordinate=09, sec-latency=176
        Memory window 0: 14000000-15fff000 (prefetchable)
        Memory window 1: 16000000-17fff000
        I/O window 0: 00001800-000018ff
        I/O window 1: 00001c00-00001cff
        16-bit legacy interface ports at 0001

0000:00:06.0 Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
        Subsystem: IBM CS4610 SoundFusion Audio Accelerator
        Flags: medium devsel, IRQ 11
        Memory at 50100000 (32-bit, non-prefetchable) [size=4K]
        Memory at 50000000 (32-bit, non-prefetchable) [size=1M]

0000:00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
        Flags: bus master, medium devsel, latency 0

0000:00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01) (prog-if 80 [Master])
        Flags: bus master, medium devsel, latency 48
        I/O ports at fcf0 [size=16]

0000:00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01) (prog-if 00 [UHCI])
        Flags: bus master, medium devsel, latency 48, IRQ 11
        I/O ports at 8400 [size=32]

0000:00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 02)
        Flags: medium devsel, IRQ 9

0000:01:00.0 VGA compatible controller: Neomagic Corporation NM2200 [MagicGraph 256AV] (rev 12) (prog-if 00 [VGA])
        Subsystem: IBM ThinkPad 570
        Flags: bus master, medium devsel, latency 128, IRQ 11
        Memory at e0000000 (32-bit, prefetchable) [size=16M]
        Memory at 70000000 (32-bit, non-prefetchable) [size=4M]
        Memory at 70400000 (32-bit, non-prefetchable) [size=1M]
        Capabilities: <available only to root>

0000:06:00.0 Ethernet controller: Xircom Cardbus Ethernet 10/100 (rev 03)
        Subsystem: Xircom Cardbus Ethernet 10/100
        Flags: bus master, medium devsel, latency 64, IRQ 11
        I/O ports at 1800 [size=128]
        Memory at 16000000 (32-bit, non-prefetchable) [size=2K]
        Memory at 16000800 (32-bit, non-prefetchable) [size=2K]
        Expansion ROM at 14000000 [disabled] [size=16K]
        Capabilities: <available only to root>

```So my card showing up, its the 'Multimedia audio controller: Cirrus Logic CS 4610/11 [CrystalClear SoundFusion Audio Accelerator]'

Step 3: [http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Cirrus+Logic&card=.&chip=CS4280%2C+CS4610%2C+CS4612%2C+CS4614%2C+CS4615%2C+CS4622%2C+CS4624%2C+CS4630&module=cs46xx](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Cirrus+Logic&card=.&chip=CS4280%2C+CS4610%2C+CS4612%2C+CS4614%2C+CS4615%2C+CS4622%2C+CS4624%2C+CS4630&module=cs46xx)

Found it. I don't know how to really install it though, this is where I spent the most of my time for the last two days asking on the IRC how to install the drivers... so I moved onto..

Step 4: My card was listed under the ```
sudo modprobe snd-
``` as snd-cs46xx. So I went to etc/modules/ and edited the file to have snd-cs46xx in it:
```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

lp
psmouse
snd-cs46xx

```
So.. everything should be working fine after a reboot.. right? Not.

---

### Post by foolsh on 2006-09-03
yes reboot and give it a try post back with the results please
if not check to see if any thing is muted this is a big problem sometimes overlooked
alsamixer

---

### Post by Tomtheman70 on 2006-09-03
Ok, rebooted.

Still no sound. I know nothing is muted because when I close the lid of my laptop my MOBO makes a little beeping sound in place of the speakers...

also, when I open alsamixer I get this error:
"Aslamixer: function snd_ctl_open failed for default: No such device'

---

### Post by foolsh on 2006-09-03
the beeping sound is most likely  not coming out of the speakers mother boards have an internal system speaker that well "beeps"

you have a tough one here my friend issue the command lsmod and paste the output here for all to see im going to hit google alittle harder this time and is it just me or is this forum reeaallyy ssllooww today

---

### Post by Tomtheman70 on 2006-09-03
```
tom@laptop:~$ lsmod
Module                  Size  Used by
nvram                   9224  1
uinput                  9088  1
apm                    21228  1
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
xircom_tulip_cb        18864  0
xircom_cb              11520  0
irtty_sir               8576  0
sir_dev                19628  1 irtty_sir
nsc_ircc               23948  0
irda                  187068  3 irtty_sir,sir_dev,nsc_ircc
analog                 12320  0
tsdev                   8000  0
crc_ccitt               2304  1 irda
ns558                   5636  0
pcmcia                 40508  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
rtc                    13492  0
floppy                 62148  0
snd_cs46xx             85704  0
gameport               15496  4 analog,ns558,snd_cs46xx
snd_rawmidi            25504  1 snd_cs46xx
snd_seq_device          8716  1 snd_rawmidi
snd_ac97_codec         93088  1 snd_cs46xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
i2c_piix4               9104  0
i2c_core               21904  1 i2c_piix4
snd_pcm                89864  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
psmouse                36100  0
snd                    55268  8 snd_cs46xx,snd_rawmidi,snd_seq_device,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_cs46xx,snd_pcm
serio_raw               7300  0
yenta_socket           28428  3
rsrc_nonstatic         13440  1 yenta_socket
pcmcia_core            42640  3 pcmcia,yenta_socket,rsrc_nonstatic
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  1 intel_agp
evdev                   9856  2
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
ide_disk               17664  3
piix                   11012  1
generic                 5124  0
processor              23360  0
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  72
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

```

And yes, the forums are TERRIBLY SLOW. Ahhh.


EDIT: ompaul on the IRC also told me to add this to the list of stuff: sudo lshw..

```
tom@laptop:~$ sudo lshw
Password:
laptop
    description: Notebook
    product: 264555U
    vendor: IBM
    version: Not Available
    serial: 78CGA49
    width: 32 bits
    capabilities: dmi-2.0
    configuration: chassis=notebook
  *-core
       description: Motherboard
       product: 264555U
       vendor: IBM
       physical id: 0
       version: Not Available
       serial: J180E6721CJ
     *-firmware
          description: BIOS
          vendor: IBM
          physical id: 0
          version: IHET46WW (09/11/99)
          size: 64KB
          capacity: 448KB
          capabilities: isa pci pcmcia pnp apm upgrade shadowing cdboot bootselect pcmciaboot edd int13floppy720 int13floppy2880 int5printscreen int9keyboard int14serial int17printer int10video biosbootspecification
     *-cpu
          description: CPU
          product: Pentium II (Deschutes)
          vendor: Intel Corp.
          physical id: 5
          bus info: cpu@0
          version: 6.5.2
          slot: Intel Processor Module
          size: 300MHz
          capacity: 300MHz
          width: 32 bits
          clock: 66MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 sep mtrr pge mca cmov pat pse36 mmx fxsr
        *-cache:0
             description: L1 cache
             physical id: 0
             size: 32KB
        *-cache:1
             description: L2 cache
             physical id: 1
             size: 512KB
     *-memory
          description: System memory
          product: DIMM SDRAM Memory Controller
          physical id: 6
          size: 192MB
          capacity: 768MB
        *-bank:0
             description: SDRAM
             physical id: 0
             slot: Base Memory
             size: 32MB
             capacity: 32MB
        *-bank:1
             description: DIMM SDRAM
             physical id: 1
             slot: DIMM Slot 1
             size: 32MB
             capacity: 32MB
        *-bank:2
             description: DIMM SDRAM
             physical id: 2
             slot: DIMM Slot 2
             size: 128MB
             capacity: 128MB
     *-cache:0 UNCLAIMED
          description: L1 cache
          physical id: a
          slot: Internal L1 Cache
          size: 32KB
          capacity: 32KB
          capabilities: synchronous internal write-back
     *-cache:1 UNCLAIMED
          description: L2 cache
          physical id: b
          slot: Internal L2 Cache
          size: 512KB
          capacity: 512KB
          capabilities: pipeline-burst external write-back
     *-pci
          description: Host bridge
          product: 440BX/ZX/DX - 82443BX/ZX/DX Host bridge
          vendor: Intel Corporation
          physical id: 40000000
          bus info: pci@00:00.0
          version: 02
          width: 32 bits
          clock: 33MHz
          resources: iomemory:40000000-43ffffff
        *-pci
             description: PCI bridge
             product: 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@00:01.0
             version: 02
             width: 32 bits
             clock: 66MHz
             capabilities: pci normal_decode bus_master
           *-display
                description: VGA compatible controller
                product: NM2200 [MagicGraph 256AV]
                vendor: Neomagic Corporation
                physical id: 0
                bus info: pci@01:00.0
                version: 12
                size: 16MB
                width: 32 bits
                clock: 33MHz
                capabilities: vga bus_master cap_list
                resources: iomemory:e0000000-e0ffffff iomemory:70000000-703fffff iomemory:70400000-704fffff irq:11
        *-pcmcia:0
             description: CardBus bridge
             product: PCI1251A
             vendor: Texas Instruments
             physical id: 2
             bus info: pci@00:02.0
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:50102000-50102fff irq:11
        *-pcmcia:1
             description: CardBus bridge
             product: PCI1251A
             vendor: Texas Instruments
             physical id: 2.1
             bus info: pci@00:02.1
             version: 00
             width: 32 bits
             clock: 33MHz
             capabilities: pcmcia bus_master cap_list
             configuration: driver=yenta_cardbus
             resources: iomemory:50101000-50101fff irq:11
        *-multimedia UNCLAIMED
             description: Multimedia audio controller
             product: CS 4610/11 [CrystalClear SoundFusion Audio Accelerator]
             vendor: Cirrus Logic
             physical id: 6
             bus info: pci@00:06.0
             version: 01
             width: 32 bits
             clock: 33MHz
             resources: iomemory:50100000-50100fff iomemory:50000000-500fffff irq:11
        *-bridge:0 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ISA
             vendor: Intel Corporation
             physical id: 7
             bus info: pci@00:07.0
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge bus_master
        *-ide
             description: IDE interface
             product: 82371AB/EB/MB PIIX4 IDE
             vendor: Intel Corporation
             physical id: 7.1
             bus info: pci@00:07.1
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=PIIX_IDE
             resources: ioport:fcf0-fcff
           *-ide:0
                description: IDE Channel 0
                physical id: 0
                bus info: ide@0
                logical name: ide0
                clock: 33MHz
              *-disk
                   description: ATA Disk
                   product: IBM-DBCA-206480
                   vendor: IBM
                   physical id: 0
                   bus info: ide@0.0
                   logical name: /dev/hda
                   version: BC4IA88F
                   serial: HR0RRQQ5736
                   size: 6149MB
                   capacity: 6149MB
                   capabilities: ata dma lba iordy smart security pm apm partitioned partitioned:dos
                   configuration: apm=off mode=udma2 smart=on
                 *-volume:0
                      description: Linux filesystem partition
                      physical id: 1
                      bus info: ide@0.0,1
                      logical name: /dev/hda1
                      capacity: 5859MB
                      capabilities: primary bootable
                 *-volume:1
                      description: Extended partition
                      physical id: 2
                      bus info: ide@0.0,2
                      logical name: /dev/hda2
                      capacity: 290MB
                      capabilities: extended partitioned partitioned:extended
           *-ide:1
                description: IDE Channel 1
                physical id: 1
                bus info: ide@1
                logical name: ide1
                clock: 33MHz
              *-cdrom
                   description: DVD reader
                   product: MATSHITADVD-ROM SR-8171
                   physical id: 0
                   bus info: ide@1.0
                   logical name: /dev/hdc
                   version: 067B
                   capabilities: packet atapi cdrom removable nonmagnetic dma lba iordy audio dvd
                 *-disc
                      physical id: 0
                      logical name: /dev/hdc
        *-usb
             description: USB Controller
             product: 82371AB/EB/MB PIIX4 USB
             vendor: Intel Corporation
             physical id: 7.2
             bus info: pci@00:07.2
             version: 01
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd
             resources: ioport:8400-841f irq:11
           *-usbhost
                product: UHCI Host Controller
                vendor: Linux 2.6.15-26-386 uhci_hcd
                physical id: 1
                bus info: usb@1
                logical name: usb1
                version: 2.06
                capabilities: usb-1.10
                configuration: driver=hub maxpower=0mA slots=2 speed=12.0MB/s
        *-bridge:1 UNCLAIMED
             description: Bridge
             product: 82371AB/EB/MB PIIX4 ACPI
             vendor: Intel Corporation
             physical id: 7.3
             bus info: pci@00:07.3
             version: 02
             width: 32 bits
             clock: 33MHz
             capabilities: bridge
             resources: irq:9
     *-network
          description: Ethernet interface
          product: Cardbus Ethernet 10/100
          vendor: Xircom
          physical id: 1
          bus info: pci@06:00.0
          logical name: eth0
          version: 03
          serial: 00:10:a4:f4:94:b3
          width: 32 bits
          clock: 33MHz
          capabilities: bus_master cap_list ethernet physical
          configuration: broadcast=yes driver=xircom_cb ip=192.168.1.110 multicast=yes
          resources: ioport:1800-187f iomemory:16000000-160007ff iomemory:16000800-16000fff irq:11

```

---

### Post by foolsh on 2006-09-03
i have read that strange things happen on laptops with sound cards 
for instance one poor soul states that the fast boot option must be disabled in the bios for his sound to work 
and [here ]("http://www.linuxquestions.org/questions/showthread.php?t=475438&highlight=snd-cs46xx") this guy has to disable acpi in his kernel boot options

from what i see in the output of lsmod all the modules look like they are loaded but it seems they are not grabbing a device.
i use kubuntu not ubuntu i know ubuntu "gnome" uses the enlighted sound deamon "esd" and kubuntu uses alsa from what i've read i looks like alsa has a better track record with this soound card.

what im getting at is this my friend i've been at this all day and it looks rather dismal im surprised no one else has chimed in on this subject im not saying your on your own its just that i dont think im at par with this problem wish i had it in my hands its so much easier when you can "see" whats happening 
my advise try some other distros like kubuntu or fedora even slackware but dont give up maybe even try plain old debian sarge im sure some out there has this same exact laptop with thier sound configured right

sorry mate i didn't have what it takes

---

