---
title: "alsamixer: function snd_ctl_open failed for default: No such device (again)"
date: 2007-01-12
forum: Multimedia &amp; Video
---

### Post by blackcoatman on 2007-01-12
I had Alsa 1.11 installed by default in Edgy and I decided to install the OSS drivers from [www.opensound.com](www.opensound.com). They worked fine (especially with Audacity which was the purpose I installed them) but i had no Flash9 sound and system sounds, so I decided to go back to alsa. I removed OSS from synaptic (since i installed it from a .deb package) and downloaded and installed the newest drivers and libs and all from the alsa website (1.14rc2). Now when I run alsamixer I get this well-known alsa error:  alsamixer: function snd_ctl_open failed for default: No such device. I am really stuck. I paste my lsmod outpu here, maybe I need to remove some oss entries (this worked for another guy, but I don't which ones mine must be!). Any help appreciated!

```
Module                  Size  Used by
snd_ice1712            69492  0 
snd_ice17xx_ak4xxx      5504  1 snd_ice1712
snd_ak4xxx_adda         9472  2 snd_ice1712,snd_ice17xx_ak4xxx
snd_cs8427             10752  1 snd_ice1712
snd_ac97_codec        102820  1 snd_ice1712
snd_ac97_bus            3456  1 snd_ac97_codec
snd_i2c                 7168  2 snd_ice1712,snd_cs8427
snd_mpu401_uart        10496  1 snd_ice1712
snd_usb_audio          83296  0 
snd_usb_lib            19072  1 snd_usb_audio
snd_hwdep              10884  1 snd_usb_audio
snd_pcm_oss            47616  0 
snd_pcm                85764  4 snd_ice1712,snd_ac97_codec,snd_usb_audio,snd_pcm_oss
snd_page_alloc         11656  1 snd_pcm
snd_mixer_oss          19584  1 snd_pcm_oss
snd_seq_oss            38144  0 
snd_seq_midi            9984  0 
snd_rawmidi            27136  3 snd_mpu401_uart,snd_usb_lib,snd_seq_midi
snd_seq_midi_event      8960  2 snd_seq_oss,snd_seq_midi
snd_seq                60016  5 snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              25220  2 snd_pcm,snd_seq
snd_seq_device          9996  4 snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    62984  17 snd_ice1712,snd_ak4xxx_adda,snd_cs8427,snd_ac97_codec,snd_i2c,snd_mpu401_uart,snd_usb_audio,snd_usb_lib,snd_hwdep,snd_pcm_oss,snd_pcm,snd_mixer_oss,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              11232  1 snd
nls_utf8                3200  1 
nls_cp437               6912  1 
vfat                   14720  1 
fat                    56348  1 vfat
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
softoss              1176300  0 
ossusb                 95756  0 
ich                    19184  0 
envy24                139772  0 
osscore               565168  4 softoss,ossusb,ich,envy24
ipv6                  272288  8 
powernow_k8            15008  0 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  2 powernow_k8,cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  1 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  2 
fuse                   43912  0 
sbp2                   24584  0 
parport_pc             37796  0 
lp                     12964  0 
parport                39496  2 parport_pc,lp
tsdev                   9152  0 
usb_storage            75072  1 
usblp                  15488  0 
libusual               17040  1 usb_storage
sg                     37404  0 
nvidia               4554836  12 
agpgart                34888  1 nvidia
serio_raw               8452  0 
floppy                 63044  0 
evdev                  11392  1 
pcspkr                  4352  0 
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
psmouse                41352  0 
i2c_nforce2             8192  0 
i2c_core               23424  3 i2c_ec,nvidia,i2c_nforce2
ext3                  142728  1 
jbd                    62228  1 ext3
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  9 snd_usb_audio,snd_usb_lib,ossusb,usb_storage,usblp,libusual,ehci_hcd,ohci_hcd
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
forcedeth              32268  0 
ide_generic             2432  0 
ide_cd                 33696  0 
cdrom                  38944  1 ide_cd
generic                 6276  0 
amd74xx                15260  0 [permanent]
sd_mod                 22656  5 
sata_nv                11268  2 
libata                 74892  1 sata_nv
scsi_mod              144648  5 sbp2,usb_storage,sg,sd_mod,libata
thermal                15624  0 
processor              31560  2 powernow_k8,thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

```

---

### Post by blackcoatman on 2007-01-13
Anyone?? :confused:

---

### Post by JoeLondon on 2007-06-15
I have exactly the same problem, with an almost identical cause ([http://ubuntuforums.org/showthread.php?p=2846162#post2846162](http://ubuntuforums.org/showthread.php?p=2846162#post2846162)). I don't know where to begin

---

### Post by narQuase on 2007-08-30
In my case, the problem could be solved by adding my user to the group "plugdev".

---

### Post by apparle on 2007-08-30
I have installed Ubuntu Fiesty Fawn 7.04 x86-64.
I have a intel dual core machine with foxconn RC4107MA-RS2 mother board
T hve ATI IXP SB450 south bridge and Realtek Sound card.
I have reffered to other posts and found out that there is a problem with alsa and it detects SB400 instead of SB450 . There was somthing about patching, which i didn't understand

Having same problem

I am new to linux though i have used Windows.
Plaese help.


IMPORTANT : I donot have internet connection and use net in my college

---

### Post by gbendotti on 2008-01-05
Hi All, after much mucking about I found this file /usr/share/alsa/user-must-execute-asoundconf-set-default-card.update-notifier

So I opened it...
It contained:
[INDENT]Name: Refresh Advanced Linux Sound Architecture (ALSA) configuration presets
Priority: High
Terminal: True
DontShowAfterReboot: False
DisplayIf: [ -f ~/.asoundrc.asoundconf ] && asoundconf is-active
Description: New Advanced Linux Sound Architecture (ALSA) configuration presets
 have been added.  Please execute the asoundconf(1) set-default-card macro in
 a Terminal now to refresh your user's configuration presets.  You may
 accomplish this task by executing the following command in a Terminal:
 asoundconf set-default-card[/INDENT]

Which I did, it then asked me to choose a card from "asoundconf list"

So I did:

asoundconf set-default-card SI7012

:guitar:

Now all is good, alsa works.

Hope this helps someone else.

---

### Post by jessdog9001 on 2008-01-27
Hey! That did the trick for me. Unfortunately, I still can't have 5.1 sound with my SB Live External. I guess I'll have to use a different sound card for that... :cry:

---

### Post by hl2040 on 2008-04-01
I had an identical issue, and the fix for me (after a few hours of searching) was, *somehow* the /etc/group file was modified to remove my username from most of the groups necessary to use the system, such as plugdev, audio, etc. The "backup" file was dated 1/10/2008 and was named /etc/group- (the trailing slash is part of the filename.)

So my fix just was 'sudo mv /etc/group- /etc/group'

To get sudo privledges back, I had to use a live CD to mount my root partition and re-add myself to /etc/sudoers.

I suspect the cause was a package update with an install script typo.

---

### Post by jetdog440 on 2008-06-03
> **narQuase said:**
> In my case, the problem could be solved by adding my user to the group "plugdev".

YOU, my friend, are a GENIUS!!!  Thank you sooo much!

Now i can make my SeKsiE talking firewall!!! :KS:KS:KS:):KS:KS:KS

---

