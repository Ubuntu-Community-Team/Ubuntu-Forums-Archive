---
title: "Need Capture Card Help!!!!!"
date: 2006-12-26
forum: Multimedia &amp; Video
---

### Post by aglc2005 on 2006-12-26
Hi, I have a KWORLD TV Time Expert with a Saa7133 chip. I was wondering if there is indeed any way to get this tv tuner working in Dapper?

---

### Post by aglc2005 on 2006-12-27
Bump....can someone help me, I don't want to have to resort to Windows

---

### Post by aglc2005 on 2006-12-31
Does anyone know how I can get this working?

---

### Post by pseudonym on 2006-12-31
Hi, have you installed the card? According to [Linux TV]("http://www.linuxtv.org/wiki/index.php/PCI_devices_DVB-T"), your online resource for DVB/TV/Capture cards in Linux, a similar card is supported.

If you already have the card installed, can you open a console and type these commands - ```
lsmod
sudo cat /var/log/messages | grep saa
``` and post the output...

---

### Post by aglc2005 on 2007-01-01
Hi, ok when I input lsmod this is the output

```
Module                  Size  Used by
isofs                  38496  1
udf                    94756  0
rfcomm                 43604  0
l2cap                  28192  5 rfcomm
bluetooth              54212  4 rfcomm,l2cap
ppdev                   9668  0
powernow_k8            14304  1
cpufreq_userspace       6496  1
cpufreq_stats           6688  0
freq_table              4928  2 powernow_k8,cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        7752  0
cpufreq_conservative     9000  0
video                  16324  0
tc1100_wmi              6884  0
sony_acpi               5580  0
pcc_acpi               12416  0
hotkey                 11492  0
dev_acpi               11236  0
container               4608  0
button                  6704  0
acpi_sbs               20172  0
battery                 9988  1 acpi_sbs
ac                      5220  1 acpi_sbs
i2c_acpi_ec             5120  1 acpi_sbs
nls_iso8859_1           4224  1
nls_cp437               5888  2
vfat                   14496  1
fat                    55548  1 vfat
nls_utf8                2240  1
ntfs                  111728  1
dm_mod                 63256  1
md_mod                 76052  0
parport_pc             37988  0
lp                     12356  0
parport                39400  3 ppdev,parport_pc,lp
ipv6                  286976  20
saa7134_alsa           14400  0
af_packet              24520  2
snd_intel8x0           35772  3
saa7134               120672  1 saa7134_alsa
snd_ac97_codec        100224  1 snd_intel8x0
snd_ac97_bus            2400  1 snd_ac97_codec
nvidia               4552916  20
agpgart                36784  1 nvidia
i2c_nforce2             7104  0
snd_pcm_oss            56448  0
snd_mixer_oss          20544  1 snd_pcm_oss
video_buf              22724  2 saa7134_alsa,saa7134
v4l2_common             6080  1 saa7134
v4l1_compat            15204  1 saa7134
ir_kbd_i2c              8876  1 saa7134
ir_common               9892  2 saa7134,ir_kbd_i2c
snd_pcm                96708  5 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss
videodev               10144  1 saa7134
i2c_core               22848  5 i2c_acpi_ec,saa7134,nvidia,i2c_nforce2,ir_kbd_i2c
snd_timer              26884  2 snd_pcm
shpchp                 49504  0
pci_hotplug            30788  1 shpchp
snd                    60004  11 saa7134_alsa,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10784  1 snd
snd_page_alloc         11304  2 snd_intel8x0,snd_pcm
psmouse                40004  0
serio_raw               7748  0
pcspkr                  2244  0
floppy                 64676  0
sg                     40160  0
sr_mod                 17988  1
evdev                  10176  3
sd_mod                 20448  2
tsdev                   8032  0
ext3                  148296  3
jbd                    65876  1 ext3
usbhid                 42752  0
usb_storage            79648  3
ide_generic             1504  0
ehci_hcd               36104  0
forcedeth              32908  0
ohci_hcd               22724  0
usbcore               139172  5 usbhid,usb_storage,ehci_hcd,ohci_hcd
ide_disk               19136  7
ide_cd                 35780  0
cdrom                  41408  2 sr_mod,ide_cd
generic                 5124  0
amd74xx                15228  0 [permanent]
sata_nv                10020  0
libata                 83440  1 sata_nv
scsi_mod              145960  5 sg,sr_mod,sd_mod,usb_storage,libata
thermal                13768  0
processor              26888  2 powernow_k8,thermal
fan                     4836  0
capability              4968  0
commoncap               7328  1 capability
vga16fb                13992  1
vgastate               10208  1 vga16fb
fbcon                  43904  72
tileblit                2784  1 fbcon
font                    8320  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2304  1 bitblit

```

And for sudo cat /var/log/messages | grep saa nothing is returned.

If it helps any I have tried VLC, TV Time Television Viewer, and kdetv. I believe they all recognize my card, because I get a black screen, but I do not know how to change the input to see if it is just on like say S-Video or Composite in.

---

### Post by pseudonym on 2007-01-01
It looks like the 'saa7134' modules are being loaded, so that's a start.

Does the card support digital TV? I couldn't find that model on a quick check of google...

---

### Post by aglc2005 on 2007-01-02
No, I don't think it does. Here's the specs that I found on it. The manufactures website doesn't list the specific card, they just list the Saa713x which covers both their Saa7133 and Saa7134 card (which the Saa7134 does have digital support)

> Model
Brand 	KWORLD
Model 	VS-TV7133 3DYC
Specifications
TV Tuner 	Yes
FM Tuner 	No
Remote Control 	Yes
Interface 	PCI
Video Display 	NTSC/PAL/SECAM
Video Format 	Mpeg4/2/1
Image Format 	JPEG/BMP
Ports In 	S-Video Input 4-pin Mini-Din
Composite Input RCA Jack

Audio Input 3.5 mm Audio Phone Jack Input from external Audio Device
Ports Out 	Audio Output 3.5mm Audio Phone Jack Output To Sound Card Line-In
Operating Systems Supported 	Windows 98SE/ME/2000/XP
System Requirements 	Pentium-III 800 MHz or higher recommended
128 MB of system memory (256 MB is recommended)
PCI 2.2 Compliant Slot
Graphics Card (Must support Microsoft DirectX 9.0 or above)
Sound Card (AC97 compatible sound card )
1GB Free HD Space
CD-ROM Drive (For software installation)
Microsoft DirectX 9.0
Specifications 	TV Tuner: 75 Ohm (UHF/VHF)
TV Frequency: 55.25 – 855.25 MHz (NTSC) (In fact, it depends on tuner type)
Video: NTSC M, NTSC M/J
Audio: Mono, Stereo (BTSC, EIAJ etc)
Features
Features 	1. With PVR-TV 7133 3DYC card, you can really enjoy watching (or recording) High quality
Analog TV on your computer.

2. With TVR application included in PVR PLUS software, you can pause live TV and continue
from where you left with the Time-Shifting function. Scheduled Recording function allows
users not to miss any TV show, especially it provides a powerful function - S.R.P.O.
(Scheduled Recording in Power-Off Mode).

3. KWorld PVR-TV 7133 3DYC adopts advanced NEC 3DY/C chipset to separate video inputs
into Luminance and Chrominance from TV signal and reduce video noise from TV signals
and sharpen text and brighten the live programs.

4. With KWorld bundled software, you can easily convert any video files from avi, mpg, etc
with MPEG Converter and then edit your favorite video files with MPEG Editor. After that,
you can burn a DVD/VCD/SVCD with DVD Burn.

5. KWorld PVR-TV 7133 3DYC also includes a fully featured Infrared Remote Control that
lets you access every feature with a simple press of a button, especially you can easily
shut-down your PC via the remote controller.

---

### Post by Yfrwlf on 2007-01-18
You say that you're seeing a black screen like maybe it's getting video input from the card?  My video capture card has two channels as well, composite and co-ax.  I installed TVTime Television Viewer from the repositories.  If you right click and bring up the menu, you can select the video input.  It allows me to change to composite.  Composite will also sometimes be called "channel 1" with some programs, while "channel 0" is the co-ax.  If your card is recognized and you see something on the default channel (0) there may be a good chance you just need to turn it to channel 1 to see your input, that worked for me.

I love how so many drivers are built into the kernel and so many things will just work out of the box.

Now if I could just figure out how to capture video things would be great.  So far programs like Kino try to use that raw module which is just frustrating since I'm already getting video feed, I just need something that can listen to /dev/video0 I think like several of my viewer programs can.  Let me know if you get yours working. :rolleyes:

---

