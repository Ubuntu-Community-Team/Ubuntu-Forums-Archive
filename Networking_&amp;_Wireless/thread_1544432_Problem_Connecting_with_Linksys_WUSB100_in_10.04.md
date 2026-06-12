---
title: "Problem Connecting with Linksys WUSB100 in 10.04"
date: 2010-08-02
forum: Networking &amp; Wireless
---

### Post by si13nt on 2010-08-02
[SIZE=2][B]Hey Guys,
I had Linksys WUSB100 Adapter connected to my desktop, the drivers are installed and it displays me the networks available in my range, but when I try to establish a connection with a network its not going fine and the connection is disconnected automatically. [/B][/SIZE]

[[IMG]http://img638.imageshack.us/img638/5017/screenshothr.png[/IMG]]("http://img839.imageshack.us/img839/5138/screenshotaz.png")
[SIZE=2]
[B]I set the mode to Infrastructure. 
Help me out. [/B][/SIZE]
[SIZE=2][B] 
Thanks.[/B][/SIZE]

---

### Post by marc.verwerft on 2010-08-02
Network manager logs to /var/log/syslog - use any editor to view that file. Maybe it tells you something interesting ;-)

Regards,

Marc

---

### Post by sinewave42 on 2010-08-03
I have the same problem - I have a WUSB100 which is connected and appears to be working, but when I try to connect using NetworkManager, I don't get internet access (I can't ping the router either) and the connection which NetworkManager claims I have drops after a while.

/var/logs/syslog has this just after wireless disconnected:

```

Aug  3 15:44:17 planck wpa_supplicant[1081]: Trying to associate with 00:22:6b:f7:88:2d (SSID='HallWireless' freq=2462 MHz)
Aug  3 15:44:17 planck wpa_supplicant[1081]: Association request to the driver failed
Aug  3 15:44:17 planck NetworkManager: <info>  (wlan0): supplicant connection state:  disconnected -> associating
Aug  3 15:44:17 planck kernel: [ 5826.651078] ===>rt_ioctl_giwscan. 3(3) BSS returned, data->length = 568
Aug  3 15:44:17 planck kernel: [ 5826.651182] ==>rt_ioctl_siwfreq::SIOCSIWFREQ[cmd=0x8b04] (Channel=11)
Aug  3 15:44:17 planck kernel: [ 5826.660034] #
Aug  3 15:44:17 planck wpa_supplicant[1081]: Associated with 00:22:6b:f7:88:2d
Aug  3 15:44:17 planck NetworkManager: <info>  (wlan0): supplicant connection state:  associating -> associated
Aug  3 15:44:17 planck kernel: [ 5826.740019] #
Aug  3 15:44:19 planck NetworkManager: <info>  Activation (wlan0/wireless): association took too long.
Aug  3 15:44:19 planck NetworkManager: <info>  (wlan0): device state change: 5 -> 9 (reason 7)
Aug  3 15:44:19 planck NetworkManager: <info>  Activation (wlan0) failed for access point (HallWireless)
Aug  3 15:44:19 planck NetworkManager: <info>  Marking connection 'Auto HallWireless' invalid.
Aug  3 15:44:19 planck NetworkManager: <info>  Activation (wlan0) failed.
Aug  3 15:44:19 planck NetworkManager: <info>  (wlan0): device state change: 9 -> 3 (reason 0)
Aug  3 15:44:19 planck NetworkManager: <info>  (wlan0): deactivating device (reason: 0).
Aug  3 15:44:19 planck NetworkManager: <info>  Policy set 'Auto eth0' (eth0) as default for routing and DNS.
Aug  3 15:44:19 planck wpa_supplicant[1081]: CTRL-EVENT-DISCONNECTED - Disconnect event - remove keys
Aug  3 15:44:27 planck wpa_supplicant[1081]: last message repeated 2 times
Aug  3 15:44:27 planck wpa_supplicant[1081]: Authentication with 00:00:00:00:00:00 timed out.

```

---

### Post by si13nt on 2010-08-03
I'm came across in some help content that we have two drivers for this wusb100 i.e; rt2800 and sta for which we have to disable one of them. I tried all sort of ways but yet there's no solution to my concern. Below I give the details, please sort out my prob as I'm totally new to Linux environment.

***lsusb***
 ```
Bus 002 Device 002: ID 093a:2500 Pixart Imaging, Inc. USB Optical Mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 005: ID 15a4:1336 Afatech Technologies, Inc. 
Bus 001 Device 004: ID 1058:1100 Western Digital Technologies, Inc. 
Bus 001 Device 003: ID 1737:0070 Linksys 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

***lsmod***
```
Module                  Size  Used by
isofs                  29250  1 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
aes_i586                7268  233 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_nvhdmi     3840  1 
snd_hda_codec_realtek   203312  1 
rt2870sta             461971  0 
arc4                    1153  2 
snd_hda_intel          22037  2 
snd_hda_codec          74201  3 snd_hda_codec_nvhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
saa7134_alsa           10412  0 
snd_seq_dummy           1338  0 
snd_pcm_oss            35308  0 
snd_seq_oss            26726  0 
snd_mixer_oss          13746  1 snd_pcm_oss
rt2800usb              31531  0 
snd_seq_midi            4557  0 
snd_pcm                70886  4 snd_hda_intel,snd_hda_codec,saa7134_alsa,snd_pcm_oss
rt2x00usb               9703  1 rt2800usb
snd_rawmidi            19056  1 snd_seq_midi
rt2x00lib              27541  2 rt2800usb,rt2x00usb
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
led_class               2864  1 rt2x00lib
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
mac80211              205146  2 rt2x00usb,rt2x00lib
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
saa7134               143743  1 saa7134_alsa
cfg80211              126517  2 rt2x00lib,mac80211
snd                    54148  17 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,saa7134_alsa,snd_pcm_oss,snd_seq_oss,snd_mixer_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ir_common              38875  1 saa7134
v4l2_common            15431  1 saa7134
videodev               34361  2 saa7134,v4l2_common
soundcore               6620  1 snd
v4l1_compat            13251  1 videodev
crc_ccitt               1339  1 rt2800usb
i2c_nforce2             5295  0 
nvidia               9962496  38 
videobuf_dma_sg        10814  2 saa7134_alsa,saa7134
videobuf_core          16356  2 saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
snd_page_alloc          7172  2 snd_hda_intel,snd_pcm
agpgart                31788  1 nvidia
lp                      7028  0 
parport                32635  2 ppdev,lp
usbhid                 36174  0 
hid                    67032  1 usbhid
usb_storage            39457  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  1 
vgastate                8961  1 vga16fb
sky2                   41040  0 
pata_amd                8766  0 
ahci                   32232  7
```

***dmesg***
```

[  777.066839] wlan0: associated
[  779.803200] Valid eCryptfs headers not found in file header region or xattr region
[  779.803204] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
[  819.376027] wlan0: deauthenticating from 00:1b:da:33:b3:05 by local choice (reason=3)
[  819.580228] wlan0: deauthenticating from 00:1b:da:33:b3:05 by local choice (reason=3)
[  819.788789] wlan0: direct probe to AP 00:1b:da:33:b3:05 (try 1)
[  819.793045] wlan0: direct probe responded
[  819.793047] wlan0: authenticate with AP 00:1b:da:33:b3:05 (try 1)
[  819.794913] wlan0: authenticated
[  819.794923] wlan0: associate with AP 00:1b:da:33:b3:05 (try 1)
[  819.797417] wlan0: RX AssocResp from 00:1b:da:33:b3:05 (capab=0x411 status=0 aid=2)
[  819.797419] wlan0: associated
[  828.888032] wlan0: deauthenticating from 00:1b:da:33:b3:05 by local choice (reason=3)
[  829.092169] wlan0: deauthenticating from 00:1b:da:33:b3:05 by local choice (reason=3)
[  829.300764] wlan0: direct probe to AP 00:1b:da:33:b3:05 (try 1)
[  829.305145] wlan0: direct probe responded
[  829.305147] wlan0: authenticate with AP 00:1b:da:33:b3:05 (try 1)
[  829.307012] wlan0: authenticated
[  829.307022] wlan0: associate with AP 00:1b:da:33:b3:05 (try 1)
[  829.309516] wlan0: RX AssocResp from 00:1b:da:33:b3:05 (capab=0x411 status=0 aid=2)
[  829.309518] wlan0: associated
[  839.798839] Valid eCryptfs headers not found in file header region or xattr region
[  839.798843] Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO
```

***dmesg | grep firmware***

```
[    8.916639] rt2800usb 1-2:1.0: firmware: requesting rt2870.bin
```

---

