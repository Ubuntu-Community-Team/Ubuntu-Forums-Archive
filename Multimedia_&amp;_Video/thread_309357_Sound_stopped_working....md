---
title: "Sound stopped working..."
date: 2006-11-29
forum: Multimedia &amp; Video
---

### Post by RavenndudE on 2006-11-29
I was playing with my sound settings trying to get my mic to work, then when I rebooted one of the times I lost all of my sound.

Nothing is muted in the Alsa Mixer (when I double click on the speaker icon that controls volume).

"$ alsamixer" gives me: "No mixer elems found"

And here's my "$ lsmod":
```

$ lsmod
Module                  Size  Used by
nls_utf8                2560  0
nls_cp437               6208  0
sg                     40352  0
sd_mod                 20864  0
usb_storage            80128  0
scsi_mod              145736  3 sg,sd_mod,usb_storage
binfmt_misc            13192  1
rfcomm                 44244  0
l2cap                  29184  5 rfcomm
bluetooth              54372  4 rfcomm,l2cap
ppdev                  10052  0
fglrx                 391980  77
cpufreq_userspace       6816  0
cpufreq_stats           6912  0
freq_table              5152  1 cpufreq_stats
cpufreq_powersave       2240  0
cpufreq_ondemand        8104  0
cpufreq_conservative     9256  0
video                  16644  0
tc1100_wmi              7172  0
sony_acpi               5900  0
pcc_acpi               12736  0
hotkey                 11812  0
dev_acpi               11652  0
container               4928  0
button                  6992  0
acpi_sbs               20556  0
battery                10308  1 acpi_sbs
ac                      5508  1 acpi_sbs
i2c_acpi_ec             5440  1 acpi_sbs
vfat                   14976  0
fat                    56028  1 vfat
fuse                   41616  2
dm_mod                 63640  1
md_mod                 76244  0
lp                     12612  0
joydev                 10688  0
ipv6                  287456  24
tsdev                   8320  0
snd_cs46xx             91464  3
usbhid                 42912  0
snd_ac97_codec         99296  1 snd_cs46xx
snd_ac97_bus            2688  1 snd_ac97_codec
snd_pcm_oss            56352  1
snd_mixer_oss          20800  2 snd_pcm_oss
snd_pcm                96772  3 snd_cs46xx,snd_ac97_codec,snd_pcm_oss
snd_timer              27204  1 snd_pcm
snd_page_alloc         11592  2 snd_cs46xx,snd_pcm
snd_mpu401              7112  0
snd_mpu401_uart         8896  1 snd_mpu401
snd_rawmidi            27552  2 snd_cs46xx,snd_mpu401_uart
snd_seq_device          9548  1 snd_rawmidi
snd                    60068  12 snd_cs46xx,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer,snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device
hw_random               6100  0
analog                 12960  0
gameport               17032  3 snd_cs46xx,analog
e100                   42180  0
parport_pc             38340  1
parport                39560  3 ppdev,lp,parport_pc
mii                     6528  1 e100
soundcore              11040  3 snd
i2c_amd756              7108  0
floppy                 65924  0
psmouse                40132  0
pcspkr                  2564  0
i2c_core               23168  2 i2c_acpi_ec,i2c_amd756
serio_raw               8132  0
amd_k7_agp              9356  1
agpgart                37072  2 fglrx,amd_k7_agp
jedec_probe            16832  0
tulip                  53792  0
cfi_probe               6976  0
gen_probe               4032  2 jedec_probe,cfi_probe
mtdcore                 7684  0
chipreg                 3968  2 jedec_probe,cfi_probe
map_funcs               2496  0
shpchp                 49312  0
pci_hotplug            30916  1 shpchp
evdev                  10432  1
ext3                  148424  1
jbd                    65684  1 ext3
ide_generic             1792  0
ehci_hcd               36104  0
ohci_hcd               22788  0
uhci_hcd               35600  0
usbcore               139012  6 usb_storage,usbhid,ehci_hcd,ohci_hcd,uhci_hcd
ide_disk               19520  5
ide_cd                 36228  0
cdrom                  41504  1 ide_cd
generic                 5444  0
amd74xx                15324  0 [permanent]
thermal                14088  0
processor              27208  1 thermal
fan                     5124  0
capability              5256  0
commoncap               7616  1 capability
vga16fb                14344  1
vgastate               10304  1 vga16fb
fbcon                  44640  72
tileblit                3072  1 fbcon
font                    8640  1 fbcon
bitblit                 6592  1 fbcon
softcursor              2752  1 bitblit

```

Bty the way, I'm running on Dapper and the sound card is a Turtle Beach Santa Cruz (Sound Fusion CS46xx).

Thanks, let me know of you need any more information that may help =)

---

### Post by RavenndudE on 2006-11-30
Ok I figured it out. I guess when I was going through my soud mixer trying to get my mic to work I unchecked "use external amplifier"

I turned this on and it works now.

---

