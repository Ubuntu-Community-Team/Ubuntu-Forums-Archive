---
title: "Sound card driver loaded and no sound"
date: 2006-08-15
forum: Multimedia &amp; Video
---

### Post by calcite on 2006-08-15
Hi, I've worked out my soundcard driver I have a 

```

0000:00:1f.5 Multimedia audio controller: Intel Corporation 82801BA/BAM AC'97 Audio (rev 11)

```

and the corresponding driver would be 

```
 snd-intel8x0 
```

Here I have loaded it

```


calcite@calcite-Dev:~$ sudo modprobe snd-intel8x0
calcite@calcite-Dev:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device
calcite@calcite-Dev:~$ lsmod
Module                  Size  Used by
iptable_filter          3072  1
ip_tables              22400  1 iptable_filter
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
ppdev                   9220  0
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
ipv6                  265728  6
dm_mod                 58936  1
md_mod                 72532  0
af_packet              22920  2
lp                     11844  0
8139too                26880  0
mii                     5888  1 8139too
floppy                 62148  0
rtc                    13492  0
tsdev                   8000  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
pcspkr                  2180  0
snd_intel8x0           33692  0
snd_ac97_codec         93088  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
serio_raw               7300  0
psmouse                36100  0
snd_pcm                89864  2 snd_intel8x0,snd_ac97_codec <---- the driver with a few others there
snd_timer              25220  1 snd_pcm
snd                    55268  4 snd_intel8x0,snd_ac97_codec,snd_pcm,snd_timer
soundcore              10208  1 snd
intel_agp              22940  1
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
agpgart                34888  2 intel_agp
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
i2c_i810                5252  0
i2c_algo_bit            9608  1 i2c_i810
i2c_core               21904  2 i2c_acpi_ec,i2c_algo_bit
evdev                   9856  1
ext3                  135688  1
jbd                    58772  1 ext3
ide_generic             1536  0
uhci_hcd               33680  0
usbcore               130692  2 uhci_hcd
ide_disk               17664  3
ide_cd                 33028  0
cdrom                  38560  1 ide_cd
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
calcite@calcite-Dev:~$


```


Can someone help me out to see whats going wrong ?

---

