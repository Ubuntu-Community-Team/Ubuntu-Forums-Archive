---
title: "RaLink RT3092 not working"
date: 2012-02-20
forum: Networking &amp; Wireless
---

### Post by SlushpuppieT on 2012-02-20
No wireless networks show up, and no wlan0 is in my list of connections.

I found this old forum post here with someone having the same problem: [http://ubuntuforums.org/showthread.php?t=1573370](http://ubuntuforums.org/showthread.php?t=1573370)

My problem differs from step 1 though. On his output from the lspci -nn command he had:
04:00.0 Network controller [0280]: RaLink RT3092 Wireless 802.11n 2T/2R PCIe [[COLOR=Red]1814:3092[/COLOR]]

When I run the same command my entry says:
02:00.0 Network controller [0280]: RaLink Device [1814:5390]

As if it's just not recognized.

I have the driver from here: [http://www.sparklan.com/download.php?prod_id=158](http://www.sparklan.com/download.php?prod_id=158) (linked from [http://www.sparklan.com/product.php?func=view&prod_id=158](http://www.sparklan.com/product.php?func=view&prod_id=158)), but I honestly have no idea how to install it.

Any help would be greatly appreciated.

---

### Post by praseodym on 2012-02-20
Hi, so its a different chipset. Which Ubuntu version do you use? Please show additionally:

```
uname -a
lsmod
iwconfig
dmesg | grep rt2
rfkill list
```
You may try this one here:

---

### Post by SlushpuppieT on 2012-02-20
Version: 64 bit 10.04

uname -a:
Linux Trent-Ubuntu 2.6.32-38-generic #83-Ubuntu SMP Wed Jan 4 11:12:07 UTC 2012 x86_64 GNU/Linux

lsmod:
```
Module                  Size  Used by
nls_iso8859_1           4633  1 
nls_cp437               6351  1 
vfat                   10866  1 
fat                    55350  1 vfat
binfmt_misc             7960  1 
ppdev                   6375  0 
joydev                 11104  0 
usbhid                 41116  0 
hid                    83888  1 usbhid
snd_hda_codec_realtek   279072  1 
snd_hda_intel          25805  0 
snd_hda_codec          85759  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6924  1 snd_hda_codec
snd_pcm_oss            41394  0 
snd_mixer_oss          16299  1 snd_pcm_oss
snd_pcm                87946  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1782  0 
snd_seq_oss            31191  0 
snd_seq_midi            5829  0 
snd_rawmidi            23420  1 snd_seq_midi
snd_seq_midi_event      7267  2 snd_seq_oss,snd_seq_midi
snd_seq                57481  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              23681  2 snd_pcm,snd_seq
snd_seq_device          6888  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
fbcon                  39270  71 
tileblit                2487  1 fbcon
font                    8053  1 fbcon
bitblit                 5811  1 fbcon
softcursor              1565  1 bitblit
vga16fb                12757  1 
vgastate                9857  1 vga16fb
snd                    71283  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               515227  0 
ttm                    61039  1 nouveau
drm_kms_helper         30742  1 nouveau
psmouse                65040  0 
soundcore               8052  1 snd
serio_raw               4918  0 
snd_page_alloc          8500  2 snd_hda_intel,snd_pcm
edac_core              45423  0 
i2c_piix4               9639  0 
edac_mce_amd            9278  0 
drm                   200384  3 nouveau,ttm,drm_kms_helper
i2c_algo_bit            6024  1 nouveau
lp                      9336  0 
parport                37160  2 ppdev,lp
usb_storage            50633  1 
ahci                   38350  2 
r8169                  39714  0 
mii                     5237  1 r8169
```

iwconfig:
lo        no wireless extensions.

eth0      no wireless extensions.

dmesg | grep rt2:
Gave me no feedback.

rfkill list:
Also no feedback.

---

### Post by SlushpuppieT on 2012-02-21
I've found a couple more topics discussing how to get similar things working but most will involve a wired connection. I won't be able to move my computer till tomorrow to try some of those, so if anyone thinks of something I can do in the meantime please comment.

---

### Post by praseodym on 2012-02-21
You need this driver:

```
sudo apt-get install --reinstall linux-headers-generic build-essential dkms
wget [http://media.cdn.ubuntu-de.org/forum/attachments/34/30/3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz](http://media.cdn.ubuntu-de.org/forum/attachments/34/30/3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz)
sudo tar 3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3
```
Reboot. "dkms" will build the driver automatically in future.

---

### Post by SlushpuppieT on 2012-02-21
Thanks praseodym, I'll try it out tomorrow and get back to you.

---

### Post by SlushpuppieT on 2012-02-22
Worked fine and I'm using the wireless now. One little hitch when I tried to extract the tar file, it gave me the error "Options `-[0-7][lmh]' not supported by *this* tar"

I eventually just extracted it directly to my home folder and moved it to /usr/src/

Other than that, everything went smoothly, thanks again praseodym.

---

