---
title: "Failure to make rt2570 driver"
date: 2011-01-18
forum: Networking &amp; Wireless
---

### Post by slashwannabe94 on 2011-01-18
Good morning all, 

I am inquiring about an error i have run into when i tried to make the driver "Ralink 2750 usb enhanced drvier". I downloaded it from this site [http://homepages.tu-darmstadt.de/~p_larbig/wlan/](http://homepages.tu-darmstadt.de/~p_larbig/wlan/). 

My wifi card according to lsusb is a 2570 Ralink Technology, Corp. 802.11g WiFi. 

I extract the package inside my /home/user/Downloads directory, using 

tar -xvf /home/user/Downloads/rt2570-k2wrlz-1.6.4.tar.bz2

That works fine and extracts the file, but once i change the working directory to 
/home/user/Downloads/rt2570-k2wrlz-1.6.4/Module

and run the 'make' command, i receive the following error. 

make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

I have already posted a similar post to this with no replies. Please people help me with this. 

Thanks, 

SlashWannabe94

---

### Post by MooPi on 2011-01-18
Can you give us the results from terminal ```
 lsmod
```& ```
iwconfig
```

---

### Post by slashwannabe94 on 2011-01-18
lsmod
----------------
Module                  Size  Used by
ppp_deflate             3682  0 
zlib_deflate           19568  1 ppp_deflate
bsd_comp                4811  0 
ppp_async               6734  1 
crc_ccitt               1339  1 ppp_async
nls_utf8                1069  1 
isofs                  29250  1 
tda1004x               15070  2 
saa7134_dvb            22167  0 
videobuf_dvb            5175  1 saa7134_dvb
dvb_core               86142  1 videobuf_dvb
saa7134_alsa           10380  2 
binfmt_misc             6587  1 
tda827x                 9240  4 
snd_hda_codec_realtek   203310  1 
tda8290                12092  2 
snd_hda_intel          21941  2 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
tuner                  20412  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
vga16fb                11385  0 
vgastate                8961  1 vga16fb
option                 15654  1 
snd_seq_dummy           1338  0 
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_pcm                70662  4 saa7134_alsa,snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
saa7134               143391  2 saa7134_dvb,saa7134_alsa
rt2500usb              18141  0 
rt2x00usb               9703  1 rt2500usb
ppdev                   5259  0 
snd_timer              19098  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
rt2x00lib              27509  2 rt2500usb,rt2x00usb
radeon                674824  3 
led_class               2864  1 rt2x00lib
ir_common              38875  1 saa7134
v4l2_common            15431  2 tuner,saa7134
lirc_atiusb            13388  0 
parport_pc             25962  1 
ttm                    49943  1 radeon
usbhid                 36110  0 
videodev               34361  3 tuner,saa7134,v4l2_common
lirc_dev                8884  1 lirc_atiusb
v4l1_compat            13251  1 videodev
videobuf_dma_sg        10782  3 saa7134_dvb,saa7134_alsa,saa7134
mac80211              205146  2 rt2x00usb,rt2x00lib
drm_kms_helper         29297  1 radeon
snd                    54148  21 saa7134_alsa,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_seq_oss,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
sbp2                   19448  1 
videobuf_core          16356  3 videobuf_dvb,saa7134,videobuf_dma_sg
tveeprom               11102  1 saa7134
ati_remote              8087  0 
lp                      7028  0 
hid                    67032  1 usbhid
usbserial              33019  4 option
cfg80211              126517  2 rt2x00lib,mac80211
usb_storage            39425  2 
psmouse                63245  0 
serio_raw               3978  0 
drm                   162409  5 radeon,ttm,drm_kms_helper
i2c_algo_bit            5028  1 radeon
parport                32635  3 ppdev,parport_pc,lp
intel_agp              24119  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
agpgart                31724  3 ttm,drm,intel_agp
ohci1394               26950  1 
8139too                18545  0 
floppy                 53016  0 
ieee1394               81181  2 sbp2,ohci1394
8139cp                 16186  0 
mii                     4381  2 8139too,8139cp
--------------------------------------------------------------
iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on
          
ppp0      no wireless extensions.

---

