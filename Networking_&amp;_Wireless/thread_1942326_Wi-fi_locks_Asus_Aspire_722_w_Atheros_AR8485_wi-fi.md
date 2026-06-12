---
title: "Wi-fi locks Asus Aspire 722 w Atheros AR8485 wi-fi"
date: 2012-03-17
forum: Networking &amp; Wireless
---

### Post by hsweet on 2012-03-17
And that is ACER not ASUS,,  names are too close..

System locks solid anytime I've tried to access wi-fi. It's a new machine, works ok in Windows. I'm just running live USB.  So far, it's happened every time with Ubuntu 11.10 64 and 32 bit and Linux Mint.  In the 64 bit U I also get a WMI error.

The card is detected as AR8485 and us using ath9k driver, in Mint at least.

---

### Post by praseodym on 2012-03-17
Please show the terminal (CTRL+ALT+T) outputs of
```

lspci -nnk | grep -iA2 net
lsmod
dmesg | grep ath
rfkill list
```
Try to shut off the hardware encryption of this driver on-the-fly:

```
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1
```
If it works, make it permanent via

```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
```

---

### Post by hsweet on 2012-03-17
I'll send the outputs of the terminal stuff in next post as I have to rig up a way to save the >output

But for now, the 1st modprobe worked ok, on the 2nd it locked the computer, on this line.```
insmod /lib/modules/3.0.0-12-generic/kernal/drivers/net/wireless/ath/ath9k/ath9k.ko nohwcrypt=1
```

---

### Post by hsweet on 2012-03-17
Got it
lscpi:
> 06:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
	Subsystem: Acer Incorporated [ALI] Device [1025:0598]
	Kernel driver in use: atl1c
--
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
	Subsystem: Foxconn International, Inc. Device [105b:e047]
	Kernel driver in use: ath9k
lsmod

> Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40253  1 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
parport_pc             36962  0 
ppdev                  17113  0 
dm_crypt               23199  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
joydev                 17693  0 
snd_hda_codec_conexant    62197  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_intel          33390  2 
snd_hda_codec         104802  3 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
ath9k                 127538  0 
mac80211              310872  1 ath9k
snd_seq_midi           13324  0 
sparse_keymap          13890  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
ath9k_common           13839  1 ath9k
uvcvideo               72711  0 
ath9k_hw              312866  2 ath9k,ath9k_common
videodev               93004  1 uvcvideo
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
v4l2_compat_ioctl32    17083  1 videodev
ath                    24067  2 ath9k,ath9k_hw
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
cfg80211              199587  3 ath9k,mac80211,ath
serio_raw              13166  0 
snd                    68266  14 snd_hda_codec_conexant,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sp5100_tco             13791  0 
k10temp                13166  0 
i2c_piix4              13301  0 
soundcore              12680  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
binfmt_misc            17540  1 
squashfs               36799  1 
overlayfs              28267  1 
nls_iso8859_1          12713  2 
nls_cp437              16991  2 
vfat                   17585  2 
fat                    61475  1 vfat
dm_raid45              78155  0 
xor                    12894  1 dm_raid45
dm_mirror              22203  0 
dm_region_hash         20918  1 dm_mirror
dm_log                 18564  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 648895  0 
zlib_deflate           27139  1 btrfs
libcrc32c              12644  1 btrfs
radeon               1015995  3 
ums_realtek            13272  0 
ttm                    76805  1 radeon
drm_kms_helper         42558  1 radeon
usb_storage            57901  4 ums_realtek
uas                    18027  0 
atl1c                  41643  0 
drm                   236330  5 radeon,ttm,drm_kms_helper
ahci                   26002  0 
libahci                26861  1 ahci
i2c_algo_bit           13423  1 radeon
wmi                    19256  0 
video                  19412  0 

dmseg
> [   64.929113] ath9k 0000:07:00.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[   64.929173] ath9k 0000:07:00.0: setting latency timer to 64
[   64.937219] ath: EEPROM regdomain: 0x6c
[   64.937225] ath: EEPROM indicates we should expect a direct regpair map
[   64.937234] ath: Country alpha2 being used: 00
[   64.937239] ath: Regpair used: 0x6c
[   65.075749] ieee80211 phy0: Selected rate control algorithm 'ath9k_rate_control'
[   65.078730] Registered led device: ath9k-phy0

rfkill
> 0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

---

### Post by praseodym on 2012-03-18
Try the "permanent" way and reboot.

---

### Post by ronewolf on 2012-07-06
First off, does this thread have the wrong title?? Its tagged with 9485, but the title is "AR8485" (that is 8 instead of 9). Is there an AR8485? In any case I have and 9485 simply turning off the hardware encrypt has worked wonders for me. My network performance (as seen from just general use of FF) went from spotty and slow to lightening fast and I think that the system in general is now much faster (subjective). Also, I was also able to move the network boot from first in the boot order which also leads to faster cleaner boots (especialy when ethernet is plugged in). After much searching and reading about this problem, this simple fix does the trick. To be more specific, I am on a fairly fresh 12.04 with all (as far as I can tell) recommended updates applied. As found on

[http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722](http://ubuntuforums.org/showthread.php?mode=hybrid&t=1942326&highlight=atheros+acer+722)

I first tried these commands:

sudo modprobe -rfv ath9k
sudo modprobe -v ath9k nohwcrypt=1

with functionally great results and then

made it permanent by creating the file

/etc/modprobe.d/ath9k.conf

and adding this line (followed by a <cr> which i'm not sure was needed...)

options ath9k nohwcrypt=1

just for the record:

rone@ronsAcerUbu:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
 Subsystem: Acer Incorporated [ALI] Device [1025:0598]
 Kernel driver in use: atl1c
--
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9485 Wireless Network Adapter [168c:0032] (rev 01)
 Subsystem: Foxconn International, Inc. Device [105b:e047]
 Kernel driver in use: ath9k

Let me know if you need any more info.

---

### Post by rogertestevnt on 2013-05-15
Hi I have used the commands below to solve a wi-fi issue on my Sony Vaio with Ubuntu 12.04:

[COLOR=#000000]sudo modprobe -rfv ath9k[/COLOR]
[COLOR=#000000]sudo modprobe -v ath9k nohwcrypt=1[/COLOR]

[COLOR=#000000]Abd then I create the file below 
[/COLOR]
[COLOR=#333333][FONT=Ubuntu]gksudo gedit [/FONT][/COLOR][COLOR=#000000]/etc/modprobe.d/ath9k.conf[/COLOR]

[COLOR=#000000]and add the line below followed by a <cr> [/COLOR]

[COLOR=#000000]options ath9k nohwcrypt=1

However, at every system reboot the wi-fi connection is lost. I have to enter the commands "[/COLOR][COLOR=#000000]sudo modprobe -rfv ath9k and[/COLOR]
[COLOR=#000000]sudo modprobe -v ath9k nohwcrypt=1" again to have the wi-fi ON. I have checked that the file ath9k.conf has been created
in the right location and it has the right contents.
Does anybody know why the configuration I made is not being kept? [/COLOR]

---

### Post by praseodym on 2013-05-15
Please check:
```

grep ath9k /etc/modprobe.d/*
```
If the module is blacklisted remove it from the respective file. Otherwise force the driver being loaded at boot-up:
```

echo ath9k | sudo tee -a /etc/modules
```

---

