---
title: "I need lots of help with TV tuner Sabrent M501-1202"
date: 2008-01-11
forum: Multimedia &amp; Video
---

### Post by theophiles on 2008-01-11
I just bought this tuner:
[http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1951869&Tab=11&NoMapp=0&CMP=EMC-TIGEREMAIL&SRCCODE=WEBLET02L](http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=1951869&Tab=11&NoMapp=0&CMP=EMC-TIGEREMAIL&SRCCODE=WEBLET02L)

one of the reviewers said that he set it up with Ubuntu, but I am having no luck. 

I might need a pretty detailed explanation as to what to do. I have been using ubuntu for a few years, but can still be pretty dense sometimes.

---

### Post by xc3RnbFO8P on 2008-01-12
In terminal: **lspci -v**

Just copy / pasta in to termnal.

Show the output of that,

Something like this: 

02:04.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

---

### Post by theophiles on 2008-01-12
It seems to work from the video port, but the cable says "no signal" on TVTime.

thanks for the help

```
bcline@dell:~$ lspci -v
00:00.0 Host bridge: Intel Corporation 82P965/G965 Memory Controller Hub (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, fast devsel, latency 0
        Capabilities: <access denied>

00:01.0 PCI bridge: Intel Corporation 82P965/G965 PCI Express Root Port (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=01, subordinate=01, sec-latency=0
        I/O behind bridge: 0000d000-0000dfff
        Memory behind bridge: dc000000-dfefffff
        Prefetchable memory behind bridge: 00000000c0000000-00000000cfffffff
        Capabilities: <access denied>

00:19.0 Ethernet controller: Intel Corporation 82566DC Gigabit Network Connection (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, fast devsel, latency 0, IRQ 20
        Memory at dffe0000 (32-bit, non-prefetchable) [size=128K]
        Memory at dffdb000 (32-bit, non-prefetchable) [size=4K]
        I/O ports at ecc0 [size=32]
        Capabilities: <access denied>

00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Contoller #4 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 16
        I/O ports at ff20 [size=32]

00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff00 [size=32]

00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 21
        Memory at dffdac00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at dffdc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=02, subordinate=02, sec-latency=0
        Memory behind bridge: dbf00000-dbffffff
        Capabilities: <access denied>

00:1c.4 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 5 (rev 02) (prog-if 00 [Normal decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=03, subordinate=03, sec-latency=0
        Capabilities: <access denied>

00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 18
        I/O ports at ff80 [size=32]

00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 17
        I/O ports at ff60 [size=32]

00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02) (prog-if 00 [UHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 19
        I/O ports at ff40 [size=32]

00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02) (prog-if 20 [EHCI])
        Subsystem: Dell Unknown device 01db
        Flags: bus master, medium devsel, latency 0, IRQ 18
        Memory at ff980800 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev f2) (prog-if 01 [Subtractive decode])
        Flags: bus master, fast devsel, latency 0
        Bus: primary=00, secondary=04, subordinate=04, sec-latency=32
        Memory behind bridge: dbe00000-dbefffff
        Capabilities: <access denied>

00:1f.0 ISA bridge: Intel Corporation 82801HH (ICH8DH) LPC Interface Controller (rev 02)
        Flags: bus master, medium devsel, latency 0
        Capabilities: <access denied>

00:1f.2 RAID bus controller: Intel Corporation 82801 SATA RAID Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: bus master, 66MHz, medium devsel, latency 0, IRQ 22
        I/O ports at fe00 [size=8]
        I/O ports at fe10 [size=4]
        I/O ports at fe20 [size=8]
        I/O ports at fe30 [size=4]
        I/O ports at fec0 [size=32]
        Memory at ff970000 (32-bit, non-prefetchable) [size=2K]
        Capabilities: <access denied>

00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
        Subsystem: Dell Unknown device 01db
        Flags: medium devsel, IRQ 10
        Memory at dffdab00 (32-bit, non-prefetchable) [size=256]
        I/O ports at ece0 [size=32]

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8300 GS (rev a1) (prog-if 00 [VGA])
        Subsystem: nVidia Corporation Unknown device 0494
        Flags: bus master, fast devsel, latency 0, IRQ 16
        Memory at de000000 (32-bit, non-prefetchable) [size=16M]
        Memory at c0000000 (64-bit, prefetchable) [size=256M]
        Memory at dc000000 (64-bit, non-prefetchable) [size=32M]
        I/O ports at dc80 [size=128]
        [virtual] Expansion ROM at dfe00000 [disabled] [size=128K]
        Capabilities: <access denied>

04:04.0 Multimedia controller: Philips Semiconductors SAA7130 Video Broadcast Decoder (rev 01)
        Subsystem: Philips Semiconductors Unknown device 0000
        Flags: bus master, medium devsel, latency 64, IRQ 16
        Memory at dbeffc00 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <access denied>
```

---

### Post by xc3RnbFO8P on 2008-01-13
Did you scan channels?

---

### Post by theophiles on 2008-01-13
yes, they all come up with a blue screen.

---

### Post by xc3RnbFO8P on 2008-01-13
Like this: 1 or 2

In terminal:> lsmod

If dont see **videodev**, you have to install v4l drivers

>  sudo apt-get install mercurial linux-headers-$(uname -r) build-essential

>  hg clone [http://linuxtv.org/hg/v4l-dvb](http://linuxtv.org/hg/v4l-dvb)

>  cd v4l-dvb

> sudo make

> sudo make install

Start Tvtime see if it works.

---

### Post by theophiles on 2008-01-13
I did have this
> ir_common              35460  2 saa7134,ir_kbd_i2c
videodev               29312  1 saa7134
v4l2_common            18432  3 tuner,saa7134,videodev
v4l1_compat            15364  2 saa7134,videodev


---

### Post by theophiles on 2008-01-13
I went ahead and did the rest of the steps anyway, figuring, what do I have to lose, I am getting nothing. 
It continued not to work. I am betting that the problem is somewhere in here?
```
bcline@dell:~/v4l-dvb$ sudo make install
make -C /home/bcline/v4l-dvb/v4l install
make[1]: Entering directory `/home/bcline/v4l-dvb/v4l'
Stripping debug info from files
Usage: strip <option(s)> in-file(s)
 Removes symbols and sections from files
 The options are:
  -I --input-target=<bfdname>      Assume input file is in format <bfdname>
  -O --output-target=<bfdname>     Create an output file in format <bfdname>
  -F --target=<bfdname>            Set both input and output format to <bfdname>
  -p --preserve-dates              Copy modified/access timestamps to the output
  -R --remove-section=<name>       Remove section <name> from the output
  -s --strip-all                   Remove all symbol and relocation information
  -g -S -d --strip-debug           Remove all debugging symbols & sections
     --strip-unneeded              Remove all symbols not needed by relocations
     --only-keep-debug             Strip everything but the debug information
  -N --strip-symbol=<name>         Do not copy symbol <name>
  -K --keep-symbol=<name>          Do not strip symbol <name>
     --keep-file-symbols           Do not strip file symbol(s)
  -w --wildcard                    Permit wildcard in symbol comparison
  -x --discard-all                 Remove all non-global symbols
  -X --discard-locals              Remove any compiler-generated symbols
  -v --verbose                     List all object files modified
  -V --version                     Display this program's version number
  -h --help                        Display this output
     --info                        List object formats & architectures supported
  -o <file>                        Place stripped output into <file>
strip: supported targets: elf32-i386 a.out-i386-linux efi-app-ia32 elf32-little elf32-big elf64-x86-64 efi-app-x86_64 elf64-little elf64-big srec symbolsrec tekhex binary ihex trad-core
make[1]: *** [media-install] Error 1
make[1]: Leaving directory `/home/bcline/v4l-dvb/v4l'
make: *** [install] Error 2

```

---

### Post by xc3RnbFO8P on 2008-01-14
v4l2_common 18432 3 tuner,saa7134,videodev , a Hybrid Analog/Digital TV Tuner?

Can you list the output of lsmod, all of it.

---

### Post by theophiles on 2008-01-16
here it is. 

> bcline@dell:~$ lsmod
Module                  Size  Used by
nls_cp437               6784  1 
isofs                  36412  1 
udf                    87204  0 
ipv6                  273892  10 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
nvidia               6221648  24 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_conservative     8072  0 
video                  18060  0 
sbs                    19592  0 
button                  8976  0 
dock                   10656  0 
container               5504  0 
ac                      6148  0 
battery                11012  0 
parport_pc             37412  0 
lp                     12580  0 
parport                37448  3 ppdev,parport_pc,lp
saa7134_dvb            18188  0 
dvb_pll                15492  1 saa7134_dvb
video_buf_dvb           7812  1 saa7134_dvb
dvb_core               82216  1 video_buf_dvb
tda1004x               17028  1 saa7134_dvb
snd_hda_intel         291488  2 
snd_pcm_oss            43008  0 
snd_mixer_oss          17664  2 snd_pcm_oss
snd_pcm                80004  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
snd_hwdep              10244  1 snd_hda_intel
tuner                  63144  0 
snd_seq_dummy           4740  0 
snd_seq_oss            33152  0 
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
snd_seq                53360  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  2 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
saa7134               129100  2 saa7134_dvb
video_buf              26244  3 saa7134_dvb,video_buf_dvb,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872  1 saa7134
snd                    54788  12 snd_hda_intel,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_hwdep,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_common              35460  2 saa7134,ir_kbd_i2c
videodev               29312  2 saa7134
i2c_core               26112  7 nvidia,saa7134_dvb,dvb_pll,tda1004x,tuner,saa7134,ir_kbd_i2c
psmouse                39952  0 
v4l2_common            18432  3 tuner,saa7134,videodev
v4l1_compat            15364  2 saa7134,videodev
intel_agp              25620  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
serio_raw               8068  0 
pcspkr                  4224  0 
agpgart                35016  2 nvidia,intel_agp
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
soundcore               8800  2 snd
evdev                  11136  3 
ext3                  133896  2 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  1 
cdrom                  37536  1 sr_mod
sd_mod                 30336  4 
usbhid                 29536  0 
hid                    28928  1 usbhid
usb_storage            73024  0 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
ahci                   23300  4 
e1000                 126272  0 
uhci_hcd               26640  0 
ehci_hcd               36492  0 
usbcore               138632  6 usbhid,usb_storage,libusual,uhci_hcd,ehci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor
ata_piix               17540  0 
libata                125168  2 ahci,ata_piix
scsi_mod              147084  5 sg,sr_mod,sd_mod,usb_storage,libata
bcline@dell:~$ 


---

### Post by wolfen69 on 2008-01-16
if you can, return it (if you cant get it to work) and get a hauppauge pvr card.(pvr150/250/350) ubuntu comes with the required drivers.(all you need is ivtv-utils,which is in synaptic) it also works natively with mythtv. anyway, good luck.

---

### Post by xc3RnbFO8P on 2008-01-18
[http://gentoo-wiki.com/HARDWARE_saa7134](http://gentoo-wiki.com/HARDWARE_saa7134)

---

