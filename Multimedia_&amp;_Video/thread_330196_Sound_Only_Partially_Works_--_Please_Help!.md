---
title: "Sound Only Partially Works -- Please Help!"
date: 2007-01-02
forum: Multimedia &amp; Video
---

### Post by theWrkncacnter on 2007-01-02
Hi. I installed ubuntu edgy AMD64, but I couldn't hear any sound. My motherboard has integrated audio, a Realtek ALC883. WIth some help, I was able to get some sound to work by manually installing "alsa-utils-1.0.9rc4a" and then installing drivers provided by realtek , "realtek-linux-audiopack-4.05d"

At this point, I can hear sound in totem, vlc, sound juicer
I can't hear sound in audacious, games (planet penguin racer, quake 4)
I can't get alsamixer to work.

What's going on?? How can it be fixed? Any help is greatly appreciated, thanks.

Here are some commands I tried:

$ ls /dev/sound/
ls: /dev/sound/: No such file or directory

$ sudo alsamixer
alsamixer: function snd_ctl_open failed for default: No such device

---

### Post by sgx on 2007-01-04
try the lsmod command to list modules, or visibly check /dev with nautilus/konqueror/rox/xfce or
other filemanager...

---

### Post by theWrkncacnter on 2007-01-04
Here is what lsmod says:
I see some "snd" modules, but I don't know how to fix the problem.

Module                  Size  Used by
nls_cp437               8704  1 
isofs                  43236  1 
udf                    97288  0 
binfmt_misc            16012  1 
rfcomm                 51360  0 
l2cap                  31744  5 rfcomm
bluetooth              64644  4 rfcomm,l2cap
powernow_k8            16576  1 
cpufreq_powersave       3456  0 
cpufreq_stats           9312  0 
cpufreq_userspace       6560  0 
cpufreq_ondemand       10928  1 
cpufreq_conservative    11272  0 
freq_table              7104  2 powernow_k8,cpufreq_stats
tc1100_wmi             10632  0 
video                  22920  0 
battery                14088  0 
container               6656  0 
sbs                    20928  0 
button                  9888  0 
pcc_acpi               19968  0 
sony_acpi               7704  0 
i2c_ec                  7808  1 sbs
ac                      8328  0 
dev_acpi               17540  0 
asus_acpi              21924  0 
hotkey                 14536  0 
nls_utf8                3840  2 
ntfs                  109128  1 
ipv6                  334432  10 
lp                     16584  0 
tsdev                  11136  0 
snd_hda_intel          23964  1 
snd_hda_codec         249600  1 snd_hda_intel
af_packet              29452  6 
sg                     44584  0 
nvidia               5444468  12 
snd_pcm_oss            57856  0 
r1000                  20608  0 
snd_mixer_oss          22784  1 snd_pcm_oss
i2c_core               29312  2 i2c_ec,nvidia
snd_pcm               108040  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_timer              30600  1 snd_pcm
wlan_scan_sta          18432  1 
floppy                 76648  0 
snd                    81192  8 snd_hda_intel,snd_hda_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              14112  1 snd
ath_pci               111656  0 
ath_rate_sample        19200  1 ath_pci
shpchp                 49068  0 
pci_hotplug            38912  1 shpchp
parport_pc             43560  1 
parport                49932  2 lp,parport_pc
snd_page_alloc         14224  2 snd_hda_intel,snd_pcm
psmouse                51088  0 
wlan                  238560  4 wlan_scan_sta,ath_pci,ath_rate_sample
evdev                  14592  1 
pcspkr                  5248  0 
ath_hal               220912  3 ath_pci,ath_rate_sample
serio_raw              10244  0 
reiserfs              283648  1 
ide_cd                 39584  1 
cdrom                  43816  1 ide_cd
ohci_hcd               25988  0 
ehci_hcd               40456  0 
usbcore               167840  3 ohci_hcd,ehci_hcd
ide_generic             2944  0 
sd_mod                 25728  4 
sata_nv                13572  3 
libata                 88984  1 sata_nv
scsi_mod              181424  3 sg,sd_mod,libata
generic                 7940  0 
thermal                19472  0 
processor              38280  2 powernow_k8,thermal
fan                     7432  0 
vesafb                 11048  0 
capability              7304  0 
commoncap              10752  1 capability
vga16fb                16656  1 
cfbcopyarea             5376  2 vesafb,vga16fb
vgastate               10368  1 vga16fb
cfbimgblt               4352  2 vesafb,vga16fb
cfbfillrect             6272  2 vesafb,vga16fb
fbcon                  45824  72 
tileblit                4736  1 fbcon
font                   10240  1 fbcon
bitblit                 8064  1 fbcon
softcursor              3968  1 bitblit

---

### Post by theWrkncacnter on 2007-01-05
Ok I didn't change anything, but sound works perfectly now. Must have been the force or something.

---

