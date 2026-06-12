---
title: "choppy DVD"
date: 2007-11-29
forum: Multimedia &amp; Video
---

### Post by Lary Grant on 2007-11-29
My DVD playback is choppy in Gutsy, whereas is fine in Dapper on the same machine.  Any way to attack this problem?

---

### Post by Whiffle on 2007-11-29
I'd check whether or not DMA is enabled on your dvd drive

do

sudo hdparm -d /path/to/dvd/device

---

### Post by Lary Grant on 2007-11-29
When I do "mount" I get
```
/dev/scd1 on /media/cdrom1 type udf (ro,nosuid,nodev,user=larry)
```for the DVD drive, whereas from Dapper (which installed on the same machine) it mounts as "dev/hdd". I am able to do "hdparm" from Dapper, but from Gutsy, I get:
```
larry@dt:~$ sudo hdparm -d /dev/scd1

/dev/scd1:
larry@dt:~$ sudo hdparm -d1 /dev/scd1

/dev/scd1:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device
larry@dt:~$ sudo hdparm -d /dev/scd1

/dev/scd1:
```

---

### Post by Whiffle on 2007-11-29
could you post the output of 

lspci -v 

and 

lsmod

---

### Post by tgalati4 on 2007-11-29
I've got the same problem on both of my drives (CDRW and DVD reader).  Worked under Dapper, but can't set DMA mode in Gutsy.

---

### Post by Lary Grant on 2007-12-02
```
larry@dt:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, fast devsel, latency 0
        Memory at f0000000 (32-bit, prefetchable) [size=128M]
        Capabilities: <access denied>

00:02.0 VGA compatible controller: Intel Corporation 82865G Integrated Graphics Controller (rev 02) (prog-if 00 [VGA])
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at e8000000 (32-bit, prefetchable) [size=128M]
        Memory at feb80000 (32-bit, non-prefetchable) [size=512K]
        I/O ports at ed98 [size=8]
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff60 [size=32]

00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff20 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01d5
        Flags: medium devsel, IRQ 20
        Memory at ffa80800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=32
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: fea00000-feafffff

00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
        Flags: bus master, medium devsel, latency 0

00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02) (prog-if 8a [Master SecP PriP])
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at 01f0 [size=8]
        I/O ports at 03f4 [size=1]
        I/O ports at 0170 [size=8]
        I/O ports at 0374 [size=1]
        I/O ports at ffa0 [size=16]
        Memory at feb7fc00 (32-bit, non-prefetchable) [size=1K]

00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01d5
        Flags: medium devsel, IRQ 3
        I/O ports at eda0 [size=32]

00:1f.5 Multimedia audio controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) AC'97 Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, medium devsel, latency 0, IRQ 21
        I/O ports at ee00 [size=256]
        I/O ports at edc0 [size=64]
        Memory at feb7fa00 (32-bit, non-prefetchable) [size=512]
        Memory at feb7f900 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

01:01.0 Modem: Intel Corporation FA82537EP 56K V.92 Data/Fax Modem PCI (rev 04) (prog-if 00 [Generic])
        Subsystem: Dell Unknown device 1000
        Flags: bus master, stepping, medium devsel, latency 64, IRQ 16
        Memory at feafd000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at de00 [size=256]
        Capabilities: <access denied>

01:02.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61) (prog-if 10 [OHCI])
        Subsystem: Adaptec Unknown device 0034
        Flags: bus master, medium devsel, latency 64, IRQ 21
        Memory at feafe000 (32-bit, non-prefetchable) [size=4K]
        Capabilities: <access denied>

01:08.0 Ethernet controller: Intel Corporation 82562EZ 10/100 Ethernet Controller (rev 02)
        Subsystem: Dell Unknown device 01d5
        Flags: bus master, medium devsel, latency 64, IRQ 22
        Memory at feaff000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ddc0 [size=64]
        Capabilities: <access denied>

larry@dt:~$ lsmod
Module                  Size  Used by
isofs                  36412  0 
udf                    87204  1 
binfmt_misc            12936  1 
i915                   25856  2 
drm                    83348  3 i915
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
nfsd                  220912  13 
exportfs                7040  1 nfsd
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_ondemand        9612  0 
cpufreq_conservative     8072  0 
cpufreq_powersave       2688  0 
cpufreq_stats           7232  0 
cpufreq_userspace       5280  0 
freq_table              5792  2 cpufreq_ondemand,cpufreq_stats
button                  8976  0 
container               5504  0 
ac                      6148  0 
sbs                    19592  0 
video                  18060  0 
dock                   10656  0 
battery                11012  0 
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
sbp2                   24072  0 
lp                     12580  0 
snd_intel8x0           34972  3 
snd_ac97_codec        100644  1 snd_intel8x0
ipv6                  273892  14 
ac97_bus                3200  1 snd_ac97_codec
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_pcm                80388  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
nfs                   245868  1 
lockd                  67592  3 nfsd,nfs
snd_seq_midi            9600  0 
sunrpc                172412  10 nfsd,nfs,lockd
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
serio_raw               8068  0 
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
iTCO_wdt               11940  0 
snd                    54660  14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
psmouse                39952  0 
pcspkr                  4224  0 
iTCO_vendor_support     4868  1 iTCO_wdt
intel_agp              25620  1 
agpgart                35016  3 drm,intel_agp
evdev                  11136  3 
ext3                  133896  3 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  10 
floppy                 60004  0 
ata_piix               17540  0 
e100                   37644  0 
mii                     6528  1 e100
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
uhci_hcd               26640  0 
usbcore               138632  5 usbhid,usb_storage,libusual,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  3 
apparmor               40728  0 
commoncap               8320  1 apparmor
ata_generic             8452  9 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,usb_storage,sg,sr_mod,sd_mod,libata
larry@dt:~$ 

```

---

### Post by Lary Grant on 2007-12-12
I am still having this problem :(

---

### Post by Whiffle on 2007-12-12
The problem (i think), the new kernels are using a different driver for your ide/sata devices, and its not working quite right with your dvd drive.  I think this is the fix:

```

sudo echo options libata atapi_enabled=1>/etc/modprobe.d/atapienable && update-initramfs -u

```

and then reboot.  I had the same thing on my thinkpad..

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive)

Sorry i missed your replies, i typically do not subscribe to threads.  Feel free to PM me if it looks like I've forgotten about something I've posted.

---

### Post by buntunub on 2007-12-13
> **Whiffle said:**
> The problem (i think), the new kernels are using a different driver for your ide/sata devices, and its not working quite right with your dvd drive.  I think this is the fix:

```

sudo echo options libata atapi_enabled=1>/etc/modprobe.d/atapienable && update-initramfs -u

```

and then reboot.  I had the same thing on my thinkpad..

[http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive](http://www.thinkwiki.org/wiki/Problems_with_SATA_and_Linux#No_DMA_on_DVD_drive)

Sorry i missed your replies, i typically do not subscribe to threads.  Feel free to PM me if it looks like I've forgotten about something I've posted.

tried this and got:

bash: /etc/modprobe.d/atapienable: Permission denied

---

### Post by Lary Grant on 2007-12-14
I got that too... I think there's some quotation marks missing that would make that command work as a "1-liner".  I got it to work by splitting it into several commands.

```
sudo bash
echo options libata atapi_enabled=1 > /etc/modprobe.d/atapienable && update-initramfs -u
exit

```

However, it didn't solve my problem :(

---

### Post by Whiffle on 2007-12-14
Yeah I don't think yall are the only ones...

[http://ubuntuforums.org/showthread.php?t=508728&highlight=libata+dma&page=2](http://ubuntuforums.org/showthread.php?t=508728&highlight=libata+dma&page=2)

I don't have time to mess with it right now, but I do think that is your problem, as described in that thinkwiki page.  I had this issue on my thinkpad when I installed slackware, and I just recompiled hte kernel without any ide drivers, and then have to pass a command to the kernel when it boots so that libata will do atapi devices.  Hopefully they'll get this sorted out in the next kernel release, its really annoying.  :/

---

### Post by Lary Grant on 2007-12-15
Well, I'm really wondering if it will ever be fixed, because I've been having the problem since Feisty.

---

### Post by buntunub on 2007-12-20
I fixed this issue by enabling dma, which does not come enabled by default. Cant remember offhand the guide I used but it was on the community docs section as I searched for dma.

---

### Post by Lary Grant on 2007-12-20
See earlier in the thread where I said I cannot turn on DMA

---

### Post by mc4man on 2007-12-22
I may be wrong but I think dma is already enabled
you could run 
sudo hdparm -i /dev/scd1  (or scd0) to check

---

### Post by buntunub on 2007-12-28
In Gutsy, it is not. Enabling it is quite simple however. Do a search under "dma" in the Community Docs section for all the answers.

---

### Post by Bartender on 2008-01-02
Interesting - I found the DMA Community Document.
It says to look at hdparm.conf

Every single line is commented out, except one - 

quiet

I still can't figure out if DMA is working (or even should be working) on my new Acer 5920!

---

### Post by mc4man on 2008-01-03
> In Gutsy, it is not
I've yet to see in a _fresh_ Gutsy install where dma is not enabled (when hardware supports)
for example just installed did nothing else
```
sudo hdparm -i /dev/scd0
[sudo] password for doug:

/dev/scd0:

 Model=PLEXTOR DVDR   PX-716AL                 , FwRev=1.02    , SerialNo=            
 Config={ Fixed Removeable DTR<=5Mbs DTR>10Mbs nonMagnetic }
 RawCHS=0/0/0, TrkSize=0, SectSize=0, ECCbytes=0
 BuffType=unknown, BuffSize=0kB, MaxMultSect=0
 (maybe): CurCHS=0/0/0, CurSects=0, LBA=yes, LBAsects=0
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 *udma4 
 AdvancedPM=no
 Drive conforms to: Unspecified:  ATA/ATAPI-3,4,5,6

 * signifies the current active mode

```
i would think that the first thing to look at for odd or unexpected behavior is whether one has a fresh or updated install

---

### Post by Bartender on 2008-01-05
You've never seen DMA not enabled?


bill@frog:~$ sudo hdparm -i /dev/sda

/dev/sda:

 Model=Hitachi HTS542525K9SA00                 , FwRev=BBFOC31P, SerialNo=071013BB0F00WDGBHWMC
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=4
 BuffType=DualPortCache, BuffSize=7229kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=268435455
 IORDY=on/off, tPIO={min:120,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 udma5 
 AdvancedPM=yes: mode=0x80 (128) WriteCache=enabled
 Drive conforms to: unknown:  ATA/ATAPI-2,3,4,5,6,7
 * signifies the current active mode

DVD's are unwatchable.  Any ideas most welcome

I tried installing sdparm but it doesn't appear to work either

---

### Post by buntunub on 2008-01-05
I have 4 machines at home, all with fresh installs of Gutsy (various flavors) and not one single one of those had DMA enabled by default. I had to follow the instructions on the community docs section to get them to do so. Four boxes.

---

### Post by Bartender on 2008-01-05
You mean this?
[https://help.ubuntu.com/community/DMA?highlight=%28dma%29](https://help.ubuntu.com/community/DMA?highlight=%28dma%29)

Step 3:
bill@frog:~$ sudo hdparm -d1 /dev/hdc
/dev/hdc: No such file or directory

Expected that:  fstab says my optical is scd0

bill@frog:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

OK, let's try the main drive

bill@frog:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Those instructions don't work for me, and nobody seems to know what "ioctl" means

Sure would like to find a resolution or if one exists

---

### Post by buntunub on 2008-01-06
> **Bartender said:**
> You mean this?
[https://help.ubuntu.com/community/DMA?highlight=%28dma%29](https://help.ubuntu.com/community/DMA?highlight=%28dma%29)

Step 3:
bill@frog:~$ sudo hdparm -d1 /dev/hdc
/dev/hdc: No such file or directory

Expected that:  fstab says my optical is scd0

bill@frog:~$ sudo hdparm -d1 /dev/scd0

/dev/scd0:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

OK, let's try the main drive

bill@frog:~$ sudo hdparm -d1 /dev/sda

/dev/sda:
 setting using_dma to 1 (on)
 HDIO_SET_DMA failed: Inappropriate ioctl for device

Those instructions don't work for me, and nobody seems to know what "ioctl" means

Sure would like to find a resolution or if one exists

try

[PHP]sudo hdparm -d1 /dev/hda[/PHP]

That should do 'er

and then to keep it on after reboots do

sudo hdparm -d1 -k1 /dev/hda

That guide needs to be updated somewhat, although I faced the same dilemma you have here but just futzed around and figured it out. Sometimes these guides just cant cover everyones specific configurations so some interpretation becomes necessary.

---

