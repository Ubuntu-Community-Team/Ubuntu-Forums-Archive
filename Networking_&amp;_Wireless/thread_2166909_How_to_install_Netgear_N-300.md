---
title: "How to install Netgear N-300"
date: 2013-08-11
forum: Networking &amp; Wireless
---

### Post by benjamin4 on 2013-08-11
Hey guys, i am currently struggling trying to instal an Netgear N-300 on my labtop, i do also have an Jensen Scandinavia air:link card, and another built-in card but cant remember the name so im hoping to get the netgear to work

---

### Post by praseodym on 2013-08-11
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands
```

uname -a
lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```
Does LAN work?

---

### Post by benjamin4 on 2013-08-12
```

lspci -nnk | grep -iA2 net:
03:00.0 Ethernet controller [0200]: Atheros Communcations device [1969:e091] (rev 13)
03:00.0 Network controller [0280]: Atheros Communcations inc. device [168c:0037] (rev 01)

lsusb
i got one here with the netgear :
Bus 002 Devuce 004: ID 0846:9020 NetGear, inc. WNA3100(1v)
 Wireless-N 300 [Broadcom BCM43231]

lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
nls_cp437              16991  1 
vfat                   17382  1 
fat                    60034  1 vfat
isofs                  39828  0 
dm_crypt               22668  0 
snd_hda_codec_realtek   222503  1 
snd_hda_codec_hdmi     31994  0 
joydev                 17457  0 
snd_hda_intel          33175  2 
snd_hda_codec         110336  3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep              13554  1 snd_hda_codec
snd_pcm                92879  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            29179  1 snd_seq_midi
snd_seq_midi_event     14436  1 snd_seq_midi
snd_seq                60549  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28838  2 snd_pcm,snd_seq
snd_seq_device         14129  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    64384  14 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12598  1 snd
sdhci_pci              18683  0 
uvcvideo               67221  0 
psmouse                72820  0 
btusb                  18371  0 
videodev               93508  1 uvcvideo
bluetooth             166564  1 btusb
v4l2_compat_ioctl32    20896  1 videodev
serio_raw              13211  0 
lp                     17789  0 
parport                44368  1 lp
snd_page_alloc         18101  2 snd_hda_intel,snd_pcm
sdhci                  31728  1 sdhci_pci
i2c_piix4              13167  0 
usb_storage            55911  1 
uas                    17756  0 
dm_mirror              21906  0 
dm_region_hash         19667  1 dm_mirror
dm_log                 18215  2 dm_mirror,dm_region_hash                                                                                                                           
aufs                  183689  0 
usbhid                 46275  0 
hid                    97618  1 usbhid
wmi                    18697  0 
pata_atiixp            13168  0 
video                  18858  0 

iwconfig
lo        no wireless extensions.



```
Does LAN work?
Not so far


Did forget to write uname -a and rfkill list, as im missing my charger at my parents place i cant get the info atm might get it tomorrow but thats the things i got so far

---

### Post by benjamin4 on 2013-08-12
Reason why i dont have the full data on is that i had to rewrite it on my other pc before it shut down so i tried to write the most important information

---

### Post by praseodym on 2013-08-12
Please show
```

uname -a
```

---

### Post by benjamin4 on 2013-08-12
dont know if you still want it but i somehow got it to work myself ^^ now im connected to the internet! but if you are interrested i could need your help for my touchpad xD

---

