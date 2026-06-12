---
title: "No sound in Dapper - YMF-744B"
date: 2006-07-04
forum: Multimedia &amp; Video
---

### Post by SUparJErk on 2006-07-04
Hi, I have a Compaq Presario 7118US with a fresh install of Dapper and all updates on it, and I have no audio. This machine has a Yamaha YMF-744B sound card, but Ubuntu won't use it. /dev/dsp doesn't exist, sound doesn't play, and there is an empty dropdown list for "default sound card" in System->Preferences->Sound. I am a relative newb when it comes to multimedia hardware and drivers in linux, so I don't know how to remedy this on my own.

Here is the output of some useful commands:

```

# lspci
0000:00:00.0 Host bridge: Intel Corporation 82850 850 (Tehama) Chipset Host Bridge (MCH) (rev 02)
0000:00:01.0 PCI bridge: Intel Corporation 82850 850 (Tehama) Chipset AGP Bridge (rev 02)
0000:00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 04)
0000:00:1f.0 ISA bridge: Intel Corporation 82801BA ISA Bridge (LPC) (rev 04)
0000:00:1f.1 IDE interface: Intel Corporation 82801BA IDE U100 (rev 04)
0000:00:1f.2 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #1) (rev 04)0000:00:1f.3 SMBus: Intel Corporation 82801BA/BAM SMBus (rev 04)
0000:00:1f.4 USB Controller: Intel Corporation 82801BA/BAM USB (Hub #2) (rev 04)0000:01:00.0 VGA compatible controller: nVidia Corporation NV25 [GeForce4 Ti 4400] (rev a3)
0000:02:09.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0000:02:0a.0 Multimedia audio controller: Yamaha Corporation YMF-744B [DS-1S Audio Controller] (rev 02)
0000:02:0b.0 USB Controller: NEC Corporation USB (rev 43)
0000:02:0b.1 USB Controller: NEC Corporation USB (rev 43)
0000:02:0b.2 USB Controller: NEC Corporation USB 2.0 (rev 04)
0000:02:0c.0 Ethernet controller: Linksys NC100 Network Everywhere Fast Ethernet 10/100 (rev 11)
0000:02:0d.0 Modem: PCTel Inc HSP MicroModem 56 (rev 02)

# lshw
[...]
*-multimedia UNCLAIMED
                description: Multimedia audio controller
                product: YMF-744B [DS-1S Audio Controller]
                vendor: Yamaha Corporation
                physical id: a
                bus info: pci@02:0a.0
                version: 02
                width: 32 bits
                clock: 33MHz
                capabilities: cap_list
                resources: iomemory:feaf0000-feaf7fff ioport:df00-df3f ioport:dff4-dff7 irq:11
[...]

# lsmod
Module                  Size  Used by
ipv6                  265728  6
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
speedstep_lib           4484  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
video                  16260  0
tc1100_wmi              6916  0
sony_acpi               5644  0
pcc_acpi               12416  0
hotkey                 11556  0
dev_acpi               11140  0
container               4608  0
button                  6672  0
acpi_sbs               19980  0
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
sg                     37920  0
sd_mod                 19984  0
nls_utf8                2176  2
ntfs                  103536  2
af_packet              22920  4
dm_mod                 58936  1
md_mod                 72532  0
sr_mod                 16932  0
sbp2                   24196  0
lp                     11844  0
usb_storage            74176  0
scsi_mod              139496  5 sg,sd_mod,sr_mod,sbp2,usb_storage
rt2570                181184  1
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
snd_ymfpci             60864  0
gameport               15496  1 snd_ymfpci
snd_ac97_codec         92704  1 snd_ymfpci
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_ymfpci,snd_ac97_codec,snd_pcm_oss
snd_opl3_lib           10624  1 snd_ymfpci
snd_timer              25220  3 snd_ymfpci,snd_pcm,snd_opl3_lib
snd_hwdep               9376  1 snd_opl3_lib
snd_page_alloc         10632  2 snd_ymfpci,snd_pcm
snd_mpu401_uart         7808  1 snd_ymfpci
snd_rawmidi            25504  1 snd_mpu401_uart
snd_seq_device          8716  2 snd_opl3_lib,snd_rawmidi
floppy                 62148  0
pcspkr                  2180  0
snd                    55268  13 snd_ymfpci,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_opl3_lib,snd_timer,snd_hwdep,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
tulip                  51744  0
nvidia               4550772  0
i2c_core               21904  2 i2c_acpi_ec,nvidia
rtc                    13492  0
psmouse                36100  0
serio_raw               7300  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
evdev                   9856  1
tsdev                   8000  0
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
usbhid                 39904  0
ehci_hcd               34184  0
ohci_hcd               21892  0
ohci1394               35124  0
ieee1394              299832  2 sbp2,ohci1394
uhci_hcd               33680  0
usbcore               130692  7 usb_storage,rt2570,usbhid,ehci_hcd,ohci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  2 sr_mod,ide_cd
ide_disk               17664  6
piix                   11012  1
generic                 5124  0
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
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

I do see the module snd_ymfpci listed in there, but it doesn't seem to be being used by anything(??). I thought this particular chipset was supposed to be natively supported in Ubuntu with no extra effort, so I'm confused as to why this isn't working. Any help would be much appreciated.

---

### Post by LordRaiden on 2006-07-05
Hi,

Have a look at my guide in my signature. Post back if you get stuck somewhere.

---

### Post by SUparJErk on 2006-07-05
:( Thanks for the guide, but I followed it all the way through and had no success.

aplay -l listed no soundcards
lspci displays that a Yamaha YMF-744B is there
alsa-project does include a driver for it
modprobe snd-ymfpci executes without an error, but doesn't bring my sound up
I successfully recompiled the alsa driver
modprobe snd-ymfpci again executes without error, but doesn't bring my sound up.

What now? :(

---

### Post by LordRaiden on 2006-07-06
Try playing something out of a music player and look at the visualizations/play timer. If it looks as if something is being played but you aren't hearing anything, then it could be that something is muted/should be muted in alsamixer.

---

### Post by SUparJErk on 2006-07-06
The problem is most definitely not that something is muted. There is no audio device to mute or unmute. 

Launching XMMS and pressing play, for example, gives me an error dialog with the following:
"Couldn't open audio"
"Please check that:

Your soundcard is configured properly
You have the correct output plugin selected
No other program is blocking the soundcard"

Launching alsamixer from a console gives me the following:
"alsamixer: function snd_ctl_open failed for default: No such device"

I will also direct your attention to my lshw output, where it shows "*-multimedia UNCLAIMED". The hardware is there, but no driver is associated with it.

---

### Post by SUparJErk on 2006-07-07
As much as I hate to say it, I'm going to be forced to abandon Ubuntu on this particular box... No sound is no desktop machine.

---

### Post by LordRaiden on 2006-07-07
If you installed the module, then there should be some indication if the module binds to that card. No idea about the card, but a hardware revision might be confusing the module to think that it does not go with this card. File a bug report with  [https://bugtrack.alsa-project.org]("https://bugtrack.alsa-project.org/") . You will get better idea of what exactly is wrong.

---

