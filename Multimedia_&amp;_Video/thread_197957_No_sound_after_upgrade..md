---
title: "No sound after upgrade."
date: 2006-06-16
forum: Multimedia &amp; Video
---

### Post by JayBachatero on 2006-06-16
After I upgraded to the last release candidate of Dapper before Final my sound stop working.  I had a topic about it here but it got locked when the dev board got locked.
[http://ubuntuforums.org/showthread.php?t=182921](http://ubuntuforums.org/showthread.php?t=182921)

This is my most recent lsmod.
```

Module                  Size  Used by
nls_cp437               5888  1
vfat                   13440  1
fat                    53020  1 vfat
rfcomm                 40216  0
l2cap                  26244  5 rfcomm
bluetooth              49892  4 rfcomm,l2cap
vmnet                  37284  13
vmmon                 111852  0
ipt_limit               2432  8
iptable_mangle          2944  0
ipt_LOG                 6912  8
ipt_MASQUERADE          3456  0
ip_nat                 19628  1 ipt_MASQUERADE
ipt_TOS                 2560  0
ipt_REJECT              5632  1
ip_conntrack_irc        6768  0
ip_conntrack_ftp        7792  0
ipt_state               2048  6
ip_conntrack           51500  5 ipt_MASQUERADE,ip_nat,ip_conntrack_irc,ip_conntrack_ftp,ipt_state
nfnetlink               6552  2 ip_nat,ip_conntrack
iptable_filter          3072  1
ip_tables              22400  8 ipt_limit,iptable_mangle,ipt_LOG,ipt_MASQUERADE,ipt_TOS,ipt_REJECT,ipt_state,iptable_filter
apm                    21228  1
ppdev                   9220  0
cpufreq_userspace       4696  0
cpufreq_stats           5636  0
freq_table              4740  1 cpufreq_stats
cpufreq_powersave       1920  0
cpufreq_ondemand        6428  0
cpufreq_conservative     7332  0
nls_utf8                2176  4
ntfs                  103536  3
ipv6                  265600  10
dm_mod                 58936  1
md_mod                 72532  0
snd_intel8x0           33692  0
snd_ac97_codec         92704  1 snd_intel8x0
snd_ac97_bus            2304  1 snd_ac97_codec
snd_pcm_oss            53664  0
snd_mixer_oss          18688  1 snd_pcm_oss
snd_pcm                89864  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25220  1 snd_pcm
snd                    55268  6 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10208  1 snd
snd_page_alloc         10632  2 snd_intel8x0,snd_pcm
lp                     11844  0
af_packet              22920  2
tsdev                   8000  0
pcspkr                  2180  0
usblp                  13056  0
rtc                    13492  0
parport_pc             35780  1
parport                36296  3 ppdev,lp,parport_pc
ns558                   5636  0
gameport               15496  2 ns558
floppy                 62148  0
via_rhine              23940  0
nvidia               4550772  0
psmouse                36228  0
intel_agp              22940  1
agpgart                34888  2 nvidia,intel_agp
serio_raw               7300  0
3c59x                  45608  0
mii                     5888  2 via_rhine,3c59x
i2c_piix4               9104  0
i2c_core               21904  2 nvidia,i2c_piix4
shpchp                 45632  0
pci_hotplug            29236  1 shpchp
sg                     37920  0
sd_mod                 19984  2
evdev                   9856  1
ext3                  135688  2
jbd                    58772  1 ext3
ide_generic             1536  0
usb_storage            74176  2
scsi_mod              139496  3 sg,sd_mod,usb_storage
ohci_hcd               21892  0
uhci_hcd               33680  0
ehci_hcd               32008  0
usbcore               129668  6 usblp,usb_storage,ohci_hcd,uhci_hcd,ehci_hcd
ide_cd                 33028  1
cdrom                  38560  1 ide_cd
ide_disk               17664  8
piix                   11012  1
generic                 5124  0
processor              23360  0
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

---

### Post by wgandhi on 2006-06-16
I had lots of problems getting the sound to work.
Have u used "esd" as ur sound deamon? U could tell by looking at the "Sound" tab under Preferences
Also, check gstreamer-properties. There is a "test" button on there.

---

### Post by JayBachatero on 2006-06-16
Yeah I checked.  It's not picking up mysound card.  I'm recompiling the kernel and see if that works.  Thanks though.

---

### Post by JayBachatero on 2006-06-16
Recompiling the Kernel didn't help either >_<

---

