---
title: "Sound with games: need of double run"
date: 2006-01-23
forum: Multimedia &amp; Video
---

### Post by denisliber on 2006-01-23
Hello!
I have a anoying problem:
The sound is working well for all applications exept the games :(
When launching from the menu the sound is missing (for any game), when lauching by typing in terminal the sound appears on second lounch of the same game (all further launches have sound also). At the first launch the /dev/dsp appears buissy by some other aplication :( and it is released on the second launch.... strange.
P.S. I use Nvidia chipset with Alsa drivers (or the Nvidia drivers - the same strange things are happening). here is my lsmod:

```
Module                  Size  Used by
rfcomm                 34972  0
l2cap                  22404  5 rfcomm
bluetooth              43012  4 rfcomm,l2cap
cpufreq_userspace       4444  0
cpufreq_stats           5124  0
freq_table              4484  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        5916  0
cpufreq_conservative     6820  0
video                  16004  0
tc1100_wmi              6916  0
sony_acpi               5516  0
pcc_acpi               11392  0
hotkey                  9508  0
dev_acpi               11396  0
i2c_acpi_ec             5760  0
button                  6672  0
battery                 9604  0
container               4608  0
ac                      4996  0
ipv6                  217408  6
floppy                 52692  0
pcspkr                  3652  0
rtc                    11832  0
tda9887                13208  0
tuner                  24488  0
cx8800                 28812  0
cx88xx                 50976  1 cx8800
i2c_algo_bit            8584  1 cx88xx
video_buf              19844  2 cx8800,cx88xx
ir_common               7428  1 cx88xx
tveeprom               12568  1 cx88xx
v4l1_compat            12420  1 cx8800
v4l2_common             5888  1 cx8800
btcx_risc               4872  2 cx8800,cx88xx
videodev                9344  2 cx8800,cx88xx
shpchp                 80612  0
pci_hotplug            24628  1 shpchp
snd_intel8x0           30144  3
snd_ac97_codec         72188  1 snd_intel8x0
snd_pcm_oss            46368  0
snd_mixer_oss          16128  1 snd_pcm_oss
snd_pcm                78344  4 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              21764  2 snd_pcm
snd                    48644  10 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore               9184  1 snd
snd_page_alloc         10120  2 snd_intel8x0,snd_pcm
i2c_nforce2             6528  0
i2c_core               19728  7 i2c_acpi_ec,tda9887,tuner,cx88xx,i2c_algo_bit,tveeprom,i2c_nforce2
nvidia_agp              7964  1
nls_cp437               5888  3
vfat                   12288  3
fat                    46492  1 vfat
nls_utf8                2176  6
ntfs                   92016  3
dm_mod                 50364  1
tsdev                   7616  0
evdev                   9088  0
nvidia               3923004  12
agpgart                32328  2 nvidia_agp,nvidia
psmouse                26116  0
mousedev               10912  1
parport_pc             31812  1
lp                     11460  0
parport                32072  2 parport_pc,lp
md                     40656  0
ext3                  115976  3
jbd                    48536  1 ext3
thermal                13192  0
processor              23100  1 thermal
fan                     4740  0
8139too                23552  0
8139cp                 18432  0
mii                     5248  2 8139too,8139cp
forcedeth              19072  0
ehci_hcd               29448  0
ohci_hcd               18564  0
usbcore               104316  3 ehci_hcd,ohci_hcd
ide_cd                 36996  0
cdrom                  33952  1 ide_cd
ide_disk               16128  12
ide_generic             1664  0
sata_nv                 9092  0
libata                 47876  1 sata_nv
scsi_mod              124872  1 libata
amd74xx                12828  1
ide_core              125268  4 ide_cd,ide_disk,ide_generic,amd74xx
unix                   24624  644
vesafb                  8088  0
capability              5000  0
commoncap               6784  1 capability
vga16fb                12232  1
vgastate                8320  1 vga16fb
softcursor              2432  2 vesafb,vga16fb
cfbimgblt               2944  2 vesafb,vga16fb
cfbfillrect             3840  2 vesafb,vga16fb
cfbcopyarea             4480  2 vesafb,vga16fb
fbcon                  34176  72
tileblit                2560  1 fbcon
font                    8448  1 fbcon
bitblit                 5248  1 fbcon
```

---

### Post by TechSonic on 2006-01-23
I have the same problem. When I use an application the uses sound, other applications then don't.  I could have Teamspeak working fine on OSS dev/dsp and then when I go to startup America's Army (Game) I have no sound.  But then it also works viseversa.  I get sound in AA, but only if teamspeak is not running.  Please help us with our most inconvinent problem [-o< .

---

### Post by happyponcho42 on 2006-01-24
Try [this](http://ubuntuforums.org/showthread.php?t=32063).  Worked for me.

---

