---
title: "No sound with VT8237"
date: 2006-07-05
forum: Multimedia &amp; Video
---

### Post by nikjen on 2006-07-05
Hi.

I have a sound problem that I cannot figure out how to solve  :-(

I installed Dapper Beta 2 and have just kept updating it, but sound has never worked. Hopefully someone here has an idea to get it working...

The machine is using a VIA VT8237 southbridge wich should have a standard AC97 "soundcard".

The soundcard is detected and the driver loaded (as far as I can see), this is the output of lsmod:
Module                  Size  Used by
acpi_sbs               19980  0
i2c_acpi_ec             5120  1 acpi_sbs
battery                 9988  1 acpi_sbs
ac                      5252  1 acpi_sbs
thermal                13576  0
processor              23360  1 thermal
fan                     4868  0
button                  6672  0
skge                   38800  0
nls_utf8                2176  0
nls_cp437               5888  0
vfat                   13440  0
fat                    53020  1 vfat
binfmt_misc            12296  1
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
radeon                116000  1
drm                    73236  2 radeon
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
reiserfs              268016  1
ipv6                  265728  10
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
it87                   20900  0
hwmon_vid               2816  1 it87
eeprom                  7056  0
i2c_isa                 4992  1 it87
lp                     11844  0
snd_seq_dummy           3844  0
snd_seq_oss            33536  0
snd_seq_midi            9376  0
snd_seq_midi_event      7552  2 snd_seq_oss,snd_seq_midi
snd_seq                51984  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
spca5xx               630928  0
videodev                9856  1 spca5xx
analog                 12320  0
snd_via82xx            28824  1
gameport               15496  2 analog,snd_via82xx
snd_ac97_codec         92704  1 snd_via82xx
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_via82xx,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  2 snd_seq,snd_pcm
snd_page_alloc         10632  2 snd_via82xx,snd_pcm
snd_mpu401_uart         7808  1 snd_via82xx
snd_rawmidi            25504  2 snd_seq_midi,snd_mpu401_uart
snd_seq_device          8716  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq,snd_rawmidi
psmouse                36100  0
usblp                  13056  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
serio_raw               7300  0
snd                    55268  13 snd_seq_oss,snd_seq,snd_via82xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401_uart,snd_rawmidi,snd_seq_device
soundcore              10208  1 snd
i2c_viapro              8980  0
i2c_core               21904  5 i2c_acpi_ec,it87,eeprom,i2c_isa,i2c_viapro
pcspkr                  2180  0
rtc                    13492  0
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sk98lin               164832  0
via_agp                 9856  1
agpgart                34888  2 drm,via_agp
evdev                   9856  1
tsdev                   8000  0
sg                     37920  0
ext3                  135688  2
jbd                    58772  1 ext3
usbhid                 39904  0
usb_storage            74176  0
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33680  0
usbcore               130692  7 spca5xx,usblp,usbhid,usb_storage,ehci_hcd,uhci_hcd
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
via82cxxx               9988  0 [permanent]
generic                 5124  0
sd_mod                 19984  6
sata_via                8964  10
libata                 78992  1 sata_via
scsi_mod              139496  4 sg,usb_storage,sd_mod,libata
capability              5000  0
commoncap               7296  1 capability
vga16fb                13704  1
vgastate               10368  1 vga16fb
fbcon                  42784  73
tileblit                2816  1 fbcon
font                    8320  1 fbcon
bitblit                 6272  1 fbcon
softcursor              2304  1 bitblit

And aplay -l also returns something:
**** List of PLAYBACK Hardware Devices ****
card 1: V8237 [VIA 8237], device 0: VIA 8237 [VIA 8237]
  Subdevices: 4/4
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
card 1: V8237 [VIA 8237], device 1: VIA 8237 [VIA 8237]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

In sound preferences the "VIA 8237" is selected. I can switch ESD on and off, but that does not make any difference.

I have turned up the volume in alsamixer, but I have to use "alsamixer -c 1" for it to work. It is possible to change the card number or set a default card number?

But still no sound  :-(

Totem says "could not establish connection to sound server" and Banshee & Rhythmbox just doesn't do anything.

Heeeelp  :-)

- Nikjen

---

### Post by nikjen on 2006-07-06
Anyone?

---

