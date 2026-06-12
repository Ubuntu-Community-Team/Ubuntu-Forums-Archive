---
title: "Dell Dimension 3000 Integrated sound card does not work!"
date: 2007-10-06
forum: Multimedia &amp; Video
---

### Post by dont_tas_me_bro on 2007-10-06
Hey guys,

Glad to be part of this group!

Am running Ubuntu on a Dell Dimension 3000 which has a integrated sound card. However I get no sound out of it. 
here is out put from my lsmod
Module                  Size  Used by
nls_cp437               5888  1
isofs                  37688  1
udf                    88580  0
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              50020  4 rfcomm,l2cap
ppdev                   9220  0
i915                   20608  1
drm                    73236  2 i915
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
i2c_acpi_ec             5120  1 acpi_sbs
i2c_core               21904  1 i2c_acpi_ec
ac                      5252  1 acpi_sbs
ipv6                  265728  6
dm_mod                 58936  1
af_packet              22920  2
md_mod                 72532  0
lp                     11844  0
snd_intel8x0           33692  1
snd_ac97_codec         93216  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
e100                   40580  0
mii                     5888  1 e100
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
tsdev                   8000  0
pcspkr                  2180  0
snd                    55268  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
usbhid                 39904  0
floppy                 62148  0
psmouse                36100  0
serio_raw               7300  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
rtc                    13492  0
intel_agp              22940  1
agpgart                34888  3 drm,intel_agp
evdev                   9856  2
ext3                  135816  1
jbd                    58772  1 ext3
ide_generic             1536  0
ehci_hcd               34184  0
uhci_hcd               33808  0
usbcore               130820  4 usbhid,ehci_hcd,uhci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  3
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


and when i run Alsamixer I do see the vertical bars and have uncommented evertyhing but still no luck. :(
When I go to Preferences-> System -> Sound  the default sound card is shown as Intel ICH5...guess thats the i/o controller..I donno why it does not list the actual integrated audio chip (AD something)...

Here is the output of  cat /proc/asound/cards
0 [ICH5           ]: ICH4 - Intel ICH5
                     Intel ICH5 with AD1980 at 0xfeb7fa00, irq 209
I totally confused...is the sound card even detected?!

Please help and oblige...

Thanks in advance



PS: Is this sound card problem with Ubuntu an Urban legend or a reality!!!

---

