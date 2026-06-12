---
title: "No usb sound being detected?"
date: 2008-04-18
forum: Multimedia &amp; Video
---

### Post by periscope on 2008-04-18
Hi all, first post here. I just got ubuntu something like 4 days ago, but did a fresh reinstallation today. I tried to update my alsa via the guide on the official alsa wiki to fix a different sound problem for my hda-intel card as that is my onboard, and I figured that wouldn't be a horrible idea. After I rebooted, my usb sound card (the only one I use, as my onboard is actually broken) is not detected at all. It is not in mixer, it says not connected in system > sound > preferences, and cat /proc/asound/modules returns just my onboard.

Someone in #ubuntu told me to do sudo apt-get install --reinstall linux-image-$(uname -r) to reinstall that module, and it looks like it reinstalls something, and it asks me to restart, but it is the same as before and if I put that same command in again, it installs it exactly as it did before. So I don't think it is working.

Any help?

---

### Post by Mithrilhall on 2008-04-18
Try both of these via a console and post back the results:


asound list
```

debian:/$ asoundconf list
Names of available sound cards:
NVidia
Headset
debian:/$      

```

```

lsusb

```

---

### Post by periscope on 2008-04-19
asoundconf list-
Names of available sound cards:
Intel

lsusb-
Bus 005 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 04a9:2220 Canon, Inc. 
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 056a:00b1 Wacom Co., Ltd 
Bus 002 Device 003: ID 0763:2010 Midiman 
Bus 002 Device 001: ID 0000:0000  
Bus 004 Device 001: ID 0000:0000  

My usb sound device is a Fast Track USB

---

### Post by Mithrilhall on 2008-04-19
Perhaps someone with more knowledge will jump on this and help. I'm at a loss. If it's not being listed under 'lsusb' then I don't think it's a supported device.

What was your original sound issue?

Also, issue a 'lsmod' via a console and post the results.

---

### Post by periscope on 2008-04-19
I know for sure it is supported, I was using it before I updated alsa. My problem before was that amarok was reporting no drivers were installed. Thanks for trying to help, by the way.

Here is lsmod

lsmod
Module                  Size  Used by
ipv6                  273892  10 
af_packet              24840  2 
binfmt_misc            12936  1 
rfcomm                 42136  2 
l2cap                  26240  11 rfcomm
bluetooth              57060  4 rfcomm,l2cap
ppdev                  10244  0 
acpi_cpufreq           10568  0 
cpufreq_userspace       5280  0 
cpufreq_powersave       2688  0 
cpufreq_ondemand        9612  2 
cpufreq_stats           7232  0 
freq_table              5792  3 acpi_cpufreq,cpufreq_ondemand,cpufreq_stats
cpufreq_conservative     8072  0 
ac                      6148  0 
button                  8976  0 
container               5504  0 
sbs                    19592  0 
dock                   10656  0 
video                  18060  0 
battery                11012  0 
lp                     12580  0 
snd_hda_intel         341784  2 
snd_seq_oss            35328  0 
joydev                 11328  0 
snd_pcm_oss            42784  1 
snd_mixer_oss          18048  1 snd_pcm_oss
snd_seq_midi_event      8704  1 snd_seq_oss
snd_pcm                78596  2 snd_hda_intel,snd_pcm_oss
snd_page_alloc         11656  2 snd_hda_intel,snd_pcm
wacom                  17664  0 
snd_seq                54224  4 snd_seq_oss,snd_seq_midi_event
nvidia               6221648  60 
usbhid                 29536  0 
atl1                   36108  0 
snd_timer              24964  2 snd_pcm,snd_seq
snd_seq_device          9740  2 snd_seq_oss,snd_seq
i2c_core               26112  1 nvidia
hid                    28928  1 usbhid
mii                     6528  1 atl1
snd_hwdep              10628  1 snd_hda_intel
psmouse                39952  0 
serio_raw               8068  0 
parport_pc             37412  1 
parport                37448  3 ppdev,lp,parport_pc
pcspkr                  4224  0 
iTCO_wdt               11940  0 
iTCO_vendor_support     4868  1 iTCO_wdt
shpchp                 34580  0 
pci_hotplug            32704  1 shpchp
snd                    56740  11 snd_hda_intel,snd_seq_oss,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq,snd_timer,snd_seq_device,snd_hwdep
intel_agp              25620  0 
agpgart                35016  2 nvidia,intel_agp
soundcore               8800  2 snd
evdev                  11136  3 
ext3                  133896  1 
jbd                    60456  1 ext3
mbcache                 9732  1 ext3
sg                     36764  0 
sr_mod                 17828  0 
cdrom                  37536  1 sr_mod
sd_mod                 30336  3 
ata_generic             8452  0 
ehci_hcd               36492  0 
uhci_hcd               26640  0 
floppy                 60004  0 
ata_piix               17540  2 
libata                125168  2 ata_generic,ata_piix
scsi_mod              147084  4 sg,sr_mod,sd_mod,libata
usbcore               138632  5 wacom,usbhid,ehci_hcd,uhci_hcd
thermal                14344  0 
processor              32072  2 acpi_cpufreq,thermal
fan                     5764  0 
fuse                   47124  1 
apparmor               40728  0 
commoncap               8320  1 apparmor

---

### Post by xc3RnbFO8P on 2008-04-19
Read this:
[http://ubuntuforums.org/showthread.php?p=2677913#post2677913]("http://ubuntuforums.org/showthread.php?p=2677913#post2677913")

---

### Post by periscope on 2008-04-19
Thank you very much Ringi, I guess I'm not a very good searcher. That worked perfectly.

---

