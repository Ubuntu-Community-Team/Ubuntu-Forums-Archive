---
title: "Unsure if D-Link DWA-547 is running at 802.11n speeds"
date: 2010-02-07
forum: Networking &amp; Wireless
---

### Post by sirjasonr on 2010-02-07
Hello!
I have just replaced my old 802.11g wireless adapter with a new 802.11n compatible adapter in order to achieve faster speeds with my 802.11n capable wireless router. I have plugged the card in an have network connectivity (yay!), but I'm not sure if it's running at its fastest.

The output of iwconfig is strange; the bit rate shows 0 kb/s as follows:
```
wlan1     IEEE 802.11bgn  ESSID:"currawa"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:21:29:80:B8:C0   
          Bit Rate=0 kb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=43/70  Signal level=-67 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```
...however the card is clearly performing better than 0 kb/s.

EDIT: I have since learnt that the link speed cannot be reported correctly this way; iw dev wlan# station dump must be used instead. Output of this command is:
```
Station 00:21:29:80:b8:c0 (on wlan1)
	inactive time:	0 ms
	rx bytes:	269632400
	rx packets:	3168309
	tx bytes:	125271782
	tx packets:	1257795
	signal:  	-62 dBm
	tx bitrate:	 MCS 41 40Mhz

```

I am currently experiencing transfer rates over the local network of around 20mbit/s.

The kernel module ath9k seems to have loaded as it should and was compiled from the latest git (lspci reports the adapter as "03:07.0 Network controller: Atheros Communications Inc. AR922X Wireless Network Adapter (rev 01)"), as the output of lsmod shows:
```
Module                  Size  Used by
cbc                     4224  429 
parport_pc             37352  0 
binfmt_misc            10220  1 
ppdev                   8232  0 
vboxnetadp              6528  0 
vboxnetflt             14288  0 
vboxdrv              1777740  2 vboxnetadp,vboxnetflt
cryptd                  8008  0 
aes_x86_64              8992  431 
aes_generic            28480  1 aes_x86_64
dm_crypt               14888  0 
snd_hda_codec_realtek   277860  1 
arc4                    2144  2 
ecb                     3296  3 
snd_usb_audio         102976  1 
snd_usb_lib            19648  1 snd_usb_audio
usblp                  15136  0 
snd_hda_intel          31880  2 
snd_seq_dummy           3460  0 
ath9k                 326912  0 
snd_hda_codec          87584  2 snd_hda_codec_realtek,snd_hda_intel
snd_seq_oss            33440  0 
mac80211              243496  1 ath9k
ath                    10784  1 ath9k
snd_hwdep               9352  2 snd_usb_audio,snd_hda_codec
snd_seq_midi            8192  0 
snd_pcm_oss            44704  0 
uvcvideo               65260  0 
amd64_edac_mod         26688  0 
nls_cp437               6976  1 
snd_rawmidi            27360  2 snd_usb_lib,snd_seq_midi
cfg80211              152616  3 ath9k,mac80211,ath
snd_mixer_oss          18976  1 snd_pcm_oss
snd_seq_midi_event      8448  2 snd_seq_oss,snd_seq_midi
edac_core              48876  1 amd64_edac_mod
videodev               43360  1 uvcvideo
led_class               5256  1 ath9k
cifs                  285528  2 
snd_seq                60608  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_pcm                93160  4 snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_pcm_oss
nvidia              10316904  38 
snd_timer              26992  2 snd_seq,snd_pcm
i2c_piix4              11728  0 
snd_page_alloc         10928  2 snd_hda_intel,snd_pcm
snd_seq_device          8308  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
k8temp                  5504  0 
snd                    77096  19 snd_hda_codec_realtek,snd_usb_audio,snd_hda_intel,snd_hda_codec,snd_seq_oss,snd_hwdep,snd_pcm_oss,snd_rawmidi,snd_mixer_oss,snd_seq,snd_pcm,snd_timer,snd_seq_device
v4l1_compat            16804  2 uvcvideo,videodev
psmouse                57124  0 
v4l2_compat_ioctl32    13344  1 videodev
soundcore               9088  1 snd
lp                     11908  0 
wacom                  25992  0 
serio_raw               6596  0 
parport                40528  3 parport_pc,ppdev,lp
iptable_filter          3872  0 
asus_atk0110            9472  0 
ip_tables              21200  1 iptable_filter
joydev                 13088  0 
x_tables               25832  1 ip_tables
hid_logitech           10112  0 
ff_memless              6504  1 hid_logitech
usbhid                 43968  1 hid_logitech
atl1                   36904  0 
mii                     6368  1 atl1

```

But the output of iwlist wlan1 scan shows only bit rates of 1Mb/s to 54Mb/s:
```
wlan1     Scan completed :
          Cell 01 - Address: 00:21:29:80:B8:C0
                    Channel:1
                    Frequency:2.412 GHz (Channel 1)
                    Quality=43/70  Signal level=-67 dBm  
                    Encryption key:on
                    ESSID:"currawa"
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s
                    Bit Rates:24 Mb/s; 36 Mb/s; 48 Mb/s; 54 Mb/s
                    Mode:Master

```

I am running Ubuntu 9.10 kernel 2.6.31-19-generic.

Any suggestions or comments would be great! Also is there any way to make the adapter have the same name as the old one which is no longer installed? In other words, to change wlan1 back to wlan0 (I use vmware sometimes, and possible some other software which I'd rather not reconfigure so it'd just be nice to have the devices named as they were).

Thanks for taking the time to read of my woes and uncertainties :)

Cheers,
Jason

---

