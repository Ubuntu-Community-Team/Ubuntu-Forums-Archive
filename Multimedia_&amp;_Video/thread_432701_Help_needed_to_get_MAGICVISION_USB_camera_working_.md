---
title: "Help needed to get MAGICVISION USB camera working on Edgy"
date: 2007-05-04
forum: Multimedia &amp; Video
---

### Post by kopardev on 2007-05-04
I am trying to get MAGICVISION USB CAMERA to work with edgy.
I have the spca5xx drivers installed. The camera is on all the time and when I try to view the camera using xawtv or gyachi I get only top 10% of the image. Can anyone help me fix this. I am newbie to ubuntu/linux.
Here r some of the command outputs that might help.

$ lsusb
Bus 005 Device 001: ID 0000:0000  
Bus 001 Device 007: ID 045e:006e Microsoft Corp. MN510 802.11b Adapter
Bus 001 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 004: ID 0af9:0011 Hama, Inc. Micro Innovations IC50C WebCam
Bus 002 Device 003: ID 043d:0072 Lexmark International, Inc. X6170 Printer
Bus 002 Device 001: ID 0000:0000  


**********************************************************
$ lsmod
Module                  Size  Used by
snd_rtctimer            3340  0 
binfmt_misc            12296  1 
rfcomm                 40216  0 
hidp                   31744  2 
l2cap                  26244  10 rfcomm,hidp
bluetooth              50020  5 rfcomm,hidp,l2cap
ipv6                  265728  8 
capability              5000  0 
commoncap               7296  1 capability
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
nls_utf8                2176  3 
nls_cp437               5888  2 
dm_mod                 58936  1 
md_mod                 72532  0 
snd_seq_dummy           3844  0 
snd_seq_oss            33536  0 
af_packet              22920  4 
snd_seq_midi            9376  0 
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ndiswrapper           177364  0 
fuse                   38412  4 
snd_via82xx            28824  1 
gameport               15496  1 snd_via82xx
snd_ac97_codec         93216  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
sbp2                   24196  0 
snd_pcm_oss            53664  0 
snd_mixer_oss          18688  1 snd_pcm_oss
tsdev                   8000  0 
spca5xx               630928  0 
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  3 snd_rtctimer,snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
lp                     11844  0 
videodev                9856  1 spca5xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
via_rhine              23940  0 
usbhid                 39904  0 
evdev                   9856  1 
shpchp                 45632  0 
pci_hotplug            29236  1 shpchp
via_agp                 9856  1 
serio_raw               7300  0 
pcspkr                  2180  0 
psmouse                36100  0 
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
agpgart                34888  1 via_agp
i2c_viapro              8980  0 
rtc                    13492  1 snd_rtctimer
parport_pc             35780  1 
parport                36296  2 lp,parport_pc
ext3                  135816  1 
jbd                    58772  1 ext3
ide_generic             1536  0 
ehci_hcd               34184  0 
uhci_hcd               33808  0 
ohci1394               35124  0 
ide_cd                 33028  0 
ide_disk               17664  9 
via82cxxx               9988  0 [permanent]
sata_via               10116  0 
libata                 78992  1 sata_via
generic                 5124  0 
thermal                13576  0 
processor              23360  1 thermal
fan                     4868  0 
vga16fb                13704  0 


**********************************************************
$ v4l-info

### video4linux device info [/dev/video0] ###
general info
    VIDIOCGCAP
        name                    : "Hama USB Sightcam 100 (2)"
        type                    : 0x1 [CAPTURE]
        channels                : 1
        audios                  : 0
        maxwidth                : 352
        maxheight               : 288
        minwidth                : 160
        minheight               : 120

channels
    VIDIOCGCHAN(0)
        channel                 : 0
        name                    : "SPCA508"
        tuners                  : 0
        flags                   : 0x0 []
        type                    : CAMERA
        norm                    : 0

tuner
ioctl VIDIOCGTUNER: Invalid argument

audio
ioctl VIDIOCGAUDIO: Invalid argument

picture
    VIDIOCGPICT
        brightness              : 0
        hue                     : 0
        colour                  : 0
        contrast                : 0
        whiteness               : 0
        depth                   : 24
        palette                 : RGB24

buffer
    VIDIOCGFBUF
        base                    : (nil)
        height                  : 0
        width                   : 0
        depth                   : 0
        bytesperline            : 0

window
    VIDIOCGWIN
        x                       : 0
        y                       : 0
        width                   : 160
        height                  : 120
        chromakey               : 0
        flags                   : 0

**********************************************************
$ v4l-conf
v4l-conf: using X11 display :0.0
dga: version 2.0
mode: 1280x1024, depth=24, bpp=32, bpl=5120, base=0xe0000000
/dev/video0 [v4l2]: ioctl VIDIOC_QUERYCAP: Invalid argument
/dev/video0 [v4l]: no overlay support

---

