---
title: "Horrible 3d game rates."
date: 2008-03-03
forum: Multimedia &amp; Video
---

### Post by theaceoffire on 2008-03-03
I am a happy user of Ubuntu 7.10, however my computer has been having issues since I moved from Windows XP pro 2.

Specifically, before I was able to run UT2004 on highest settings with as many bots as I pleased, but after the OS swap I am unable to even run Nexuiz (link: [http://www.alientrap.org/nexuiz/]("http://www.alientrap.org/nexuiz/")) on lowest settings with a constant frame rate above 10. Highest frame rates I ever got on lowest settings facing a wall was 40. 

On lowest settings, 3d games are still sideshows when people appear, and this is just sad.

I am using an HP **Pavillion a1120n** media center computer, with a **Pentium 4 3.06 GHz** processor and **1.5 GB of DDR2** Ram. I have an** nVidia GeForce FX 5500**, PCI video card (No AGP or PCI Express slots available), and integrated onboard video. 

Now, I believe the problem *might* be due to conflicts between my onboard video card and my PCI one, but I am unable to disable my onboard video card in the bios (when I do my computer crashes during the Boot sequence). 
[SIZE="5"]
[COLOR="Indigo"]Please, if someone can help me, I would be willing to try anything. I am especially interested if anyone knows how to test to see what the problem might be.[/COLOR][/SIZE]

I will now give as much information as I can think of:

Output of "lspci -v"
```
00:00.0 Host bridge: Intel Corporation 82915G/P/GV/GL/PL/910GL Memory Controller Hub (rev 04)

00:02.0 VGA compatible controller: Intel Corporation 82915G/GV/910GL Integrated Graphics Controller (rev 04) (prog-if 00 [VGA])
        Subsystem: Hewlett-Packard Company Unknown device 2a08
        Flags: bus master, fast devsel, latency 0, IRQ 10
        Memory at baf80000 (32-bit, non-prefetchable) [disabled] [size=512K]
        I/O ports at c800 [disabled] [size=8]
        Memory at c0000000 (32-bit, prefetchable) [disabled] [size=256M]
        Memory at baf40000 (32-bit, non-prefetchable) [disabled] [size=256K]
        Capabilities: <access denied>

00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)

00:1c.0 PCI bridge: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) PCI Express Port 1 (rev 03) (prog-if 00 [Normal decode])

00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03) (prog-if 00 [UHCI])

00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03) (prog-if 00 [UHCI])

00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03) (prog-if 00 [UHCI])

00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03) (prog-if 00 [UHCI])

00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03) (prog-if 20 [EHCI])

00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev d3) (prog-if 01 [Subtractive decode])

00:1f.0 ISA bridge: Intel Corporation 82801FB/FR (ICH6/ICH6R) LPC Interface Bridge (rev 03)

00:1f.1 IDE interface: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) IDE Controller (rev 03) (prog-if 8a [Master SecP PriP])

00:1f.2 IDE interface: Intel Corporation 82801FB/FW (ICH6/ICH6W) SATA Controller (rev 03) (prog-if 8f [Master SecP SecO PriP PriO])

00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)

02:01.0 FireWire (IEEE 1394): VIA Technologies, Inc. IEEE 1394 Host Controller (rev 80) (prog-if 10 [OHCI])

02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)

02:03.0 VGA compatible controller: nVidia Corporation NV34 [GeForce FX 5500] (rev a1) (prog-if 00 [VGA])
        Flags: bus master, 66MHz, medium devsel, latency 248, IRQ 18
        Memory at be000000 (32-bit, non-prefetchable) [size=16M]
        Memory at d0000000 (32-bit, prefetchable) [size=256M]
        [virtual] Expansion ROM at bf000000 [disabled] [size=128K]
        Capabilities: <access denied>

02:04.0 Network controller: RaLink RT2500 802.11g Cardbus/mini-PCI (rev 01)

02:05.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)

02:05.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)

02:05.2 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [MPEG Port] (rev 05)

```

Output of "cat /etc/X11/xorg.conf"
```
Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "vesa"
        Busid           "PCI:2:3:0"
        Driver          "nvidia"
        Screen  0
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Samsung"
        Modelname       "Samsung SyncMaster 152MP/156MP/CX510MP/CX500MB"
        Horizsync       30-71
        Vertrefresh     56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
        Gamma   1.0
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1400    1050
                Modes           "1024x768@60"   "1152x864@75"   "1024x768@70"  "1280x960@60"    "1024x768@75"   "1280x1024@60"  "832x624@75"    "1400x1050@60" "800x600@60"     "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"   "640x480@72"     "640x480@60"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
EndSection
Section "device" #      
        Identifier      "device1"
        Boardname       "NVIDIA GeForce4 (generic)"
        Busid           "PCI:2:3:0"
        Driver          "nv"
        Screen  0
        Vendorname      "NVIDIA"
EndSection
Section "screen" #      
        Identifier      "screen1"
        Device          "device1"
        Defaultdepth    24
        Monitor         "monitor1"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"    "640x480@72"    "640x480@75"   "800x600@56"     "800x600@72"    "800x600@75"    "800x600@60"    "832x624@75"   "1024x768@75"    "1024x768@70"   "1024x768@60"   "1280x960@60"
        EndSubSection
EndSection
Section "monitor" #      
        Identifier      "monitor1"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
        Gamma   1.0
EndSection
Section "ServerFlags"
EndSection
Section "device" #   
        Identifier      "device2"
        Boardname       "Intel 915"
        Busid           "PCI:0:2:0"
        Driver          "i810"
        Screen  0
        Vendorname      "Intel"
EndSection
Section "screen" #   
        Identifier      "screen2"
        Device          "device2"
        Defaultdepth    24
        Monitor         "monitor2"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"
        EndSubSection
EndSection
Section "monitor" #   
        Identifier      "monitor2"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection
Section "device" #   
        Identifier      "device3"
        Boardname       "vesa"
        Busid           "PCI:2:3:0"
        Driver          "nvidia"
        Screen  1
EndSection
Section "screen" #   
        Identifier      "screen3"
        Device          "device3"
        Defaultdepth    24
        Monitor         "monitor3"
        SubSection "Display"
                Depth   24
                Modes           "640x480@60"
        EndSubSection
EndSection
Section "monitor" #   
        Identifier      "monitor3"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection
```

Output of "glxinfo"
```
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:{Whole bunch of stuff}
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:{Whole bunch of stuff}
GLX version: 1.3
GLX extensions:{Whole bunch of stuff}
OpenGL vendor string: NVIDIA Corporation
OpenGL renderer string: GeForce FX 5500/PCI/SSE2
OpenGL version string: 2.1.1 NVIDIA 100.14.19
OpenGL extensions: {Whole bunch of stuff}

```

Output of "lsmod"
```

Module                  Size  Used by
nls_iso8859_1           5120  1 
nls_cp437               6784  1 
vfat                   14080  1 
fat                    54300  1 vfat
xt_limit                3584  8 
xt_tcpudp               4224  10 
ipt_LOG                 7552  8 
ipt_MASQUERADE          4608  0 
ipt_TOS                 3200  0 
ipt_REJECT              5760  1 
nf_conntrack_irc        8088  0 
nf_conntrack_ftp       11136  0 
xt_state                3456  6 
af_packet              24840  2 
binfmt_misc            12936  1 
vboxdrv                61104  0 
ppdev                  10244  0 
speedstep_lib           6404  0 
cpufreq_conservative     8072  0 
cpufreq_userspace       5280  0 
cpufreq_stats           7232  0 
cpufreq_ondemand        9612  0 
freq_table              5792  2 cpufreq_stats,cpufreq_ondemand
cpufreq_powersave       2688  0 
container               5504  0 
ac                      6148  0 
button                  8976  0 
video                  18060  0 
sbs                    19592  0 
dock                   10656  0 
battery                11012  0 
jfs                   189412  1 
sbp2                   24072  0 
lp                     12580  0 
arc4                    2944  2 
ecb                     4608  2 
blkcipher               7556  1 ecb
rc80211_simple          6912  1 
cx88_blackbird         21636  0 
cx2341x                13316  1 cx88_blackbird
joydev                 11328  0 
snd_hda_intel         263712  5 
snd_seq_dummy           4740  0 
tuner                  63144  0 
cx88_alsa              14600  0 
snd_seq_oss            33152  0 
snd_pcm_oss            44672  0 
snd_mixer_oss          17664  1 snd_pcm_oss
snd_seq_midi            9600  0 
snd_rawmidi            25728  1 snd_seq_midi
rt2500pci              19072  0 
rt2x00pci              11520  1 rt2500pci
rt2x00lib              19584  2 rt2500pci,rt2x00pci
rfkill                  8208  1 rt2x00lib
mac80211              171016  4 rc80211_simple,rt2500pci,rt2x00pci,rt2x00lib
cfg80211                7304  1 mac80211
input_polldev           5896  1 rt2x00lib
crc_itu_t               3072  1 rt2x00lib
snd_pcm                80388  4 snd_hda_intel,cx88_alsa,snd_pcm_oss
serio_raw               8068  0 
cx8802                 19716  1 cx88_blackbird
nvidia               6221648  54 
cx8800                 34944  1 cx88_blackbird
cx88xx                 68132  4 cx88_blackbird,cx88_alsa,cx8802,cx8800
eeprom_93cx6            3200  1 rt2500pci
psmouse                39952  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
ir_common              35460  1 cx88xx
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
xpad                    9988  0 
agpgart                35016  1 nvidia
i2c_algo_bit            7428  1 cx88xx
compat_ioctl32          2304  1 cx8800
pcspkr                  4224  0 
usbhid                 29536  0 
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
hid                    28928  1 usbhid
tveeprom               16784  1 cx88xx
videodev               29312  3 cx88_blackbird,cx8800,cx88xx
v4l2_common            18432  6 cx88_blackbird,cx2341x,tuner,cx8800,cx88xx,videodev
v4l1_compat            15364  1 videodev
btcx_risc               5896  4 cx88_alsa,cx8802,cx8800,cx88xx
video_buf              26244  5 cx88_blackbird,cx88_alsa,cx8802,cx8800,cx88xx
usblp                  15104  0 
i2c_core               26112  5 tuner,nvidia,cx88xx,i2c_algo_bit,tveeprom
snd_seq                53232  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24324  3 snd_pcm,snd_seq
snd_seq_device          9228  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd                    54660  18 snd_hda_intel,cx88_alsa,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_hda_intel,snd_pcm
evdev                  11136  3 
iptable_nat             8708  0 
nf_nat                 20140  2 ipt_MASQUERADE,iptable_nat
nf_conntrack_ipv4      19724  8 iptable_nat
nf_conntrack           65288  7 ipt_MASQUERADE,nf_conntrack_irc,nf_conntrack_ftp,xt_state,iptable_nat,nf_nat,nf_conntrack_ipv4
nfnetlink               6936  3 nf_nat,nf_conntrack_ipv4,nf_conntrack
iptable_mangle          3840  0 
iptable_filter          3968  1 
ip_tables              13924  3 iptable_nat,iptable_mangle,iptable_filter
x_tables               16260  9 xt_limit,xt_tcpudp,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,xt_state,iptable_nat,ip_tables
usb_storage            73024  1 
ide_core              116804  1 usb_storage
libusual               18448  1 usb_storage
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sd_mod                 30336  6 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
8139too                27776  0 
ata_piix               17540  3 
8139cp                 25088  0 
mii                     6528  2 8139too,8139cp
ohci1394               36528  0 
ieee1394               96312  2 sbp2,ohci1394
ata_generic             8452  0 
libata                125168  2 ata_piix,ata_generic
scsi_mod              147084  6 sbp2,usb_storage,sg,sd_mod,sr_mod,libata
ehci_hcd               36492  0 
uhci_hcd               26640  0 
usbcore               138632  8 xpad,usbhid,usblp,usb_storage,libusual,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  1 thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

```

Well, that is all I can think of to add... if anyone has a clue of what I can try to do to fix this, let me know.

---

### Post by theaceoffire on 2008-03-06
So there are no ideas?
Does anyone need more info, or want me to try a tool or something?

---

### Post by Zorael on 2008-03-08
It looks like you're not using the accelerated proprietary nvidia driver. Have you installed the **nvidia-glx-new** package? (Alternatively just **nvidia-glx**, or **nvidia-glx-legacy** for older cards.)

If so, it hasn't configured your xorg.conf properly.
```
Section "device" #      
        Identifier      "device1"
        Boardname       "NVIDIA GeForce4 (generic)"
        Busid           "PCI:2:3:0"
        Driver          **"nvidia"**
        Screen  0
        Vendorname      "NVIDIA"
EndSection
```

Change it thusly. After which, the following command should output:
```
zorael@azrael:~$ lshw -C video
WARNING: you should run this program as super-user.
  *-display
       description: VGA compatible controller
       product: G70 [GeForce Go 7600] *(obviously the name of your card instead)*
       vendor: nVidia Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: driver=nvidia latency=0 module=**nvidia**
```

Then again, it did say 'direct rendering: Yes', so perhaps I'm misinterpreting things here.

Also, your xorg.conf looks like a bit of a mess, but perhaps all those failsafe entries are needed for the version of X you run? :>

---

### Post by theaceoffire on 2008-03-09
THANK YOU!
I don't know if this will fix it, but you are right, I WAS using the wrong version of Nvida's driver!


As for why my xorg.conf looks so bad, that is due to my weird system.

If I try to boot just through my video card, it crashes, so I had to boot through my onboard, disable it, and change the xorg it used to point at the right place... I just haven't cleaned it yet. 


I will let you know if you fixed my issue, but THANK YOU!

************************************************************
Output of "lshw -C video"
```
WARNING: you should run this program as super-user.
  *-display               
       description: VGA compatible controller
       product: 82915G/GV/910GL Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 32 bits
       clock: 33MHz
       capabilities: vga bus_master cap_list
       configuration: latency=0
  *-display
       description: VGA compatible controller
       product: NV34 [GeForce FX 5500]
       vendor: nVidia Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       version: a1
       width: 32 bits
       clock: 66MHz
       capabilities: vga bus_master cap_list
       configuration: driver=nvidia latency=248 maxlatency=1 mingnt=5 module=nvidia
```

WOOT! It is using the right driver! It is a lot better I think, but I am sure I can make it faster.

THANK YOU SO MUCH! This has really been bothering me.

---

