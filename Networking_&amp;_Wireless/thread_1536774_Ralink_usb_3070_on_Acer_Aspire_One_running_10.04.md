---
title: "Ralink usb 3070 on Acer Aspire One running 10.04"
date: 2010-07-22
forum: Networking &amp; Wireless
---

### Post by pink_book7 on 2010-07-22
Hi

I have an Acer Aspire One ZG5, which is running (Desktop Version) 10.04.  I've been happily using the built in wifi adapter, but now I've got a new wireless hub that supports 802.11n and I want to exploit the higher connection speed.  I've bought a wireless usb that has no external markings, however, using 'lsusb' I've managed to establish it contains ralink 3070.  Any ideas how I get this to work?  When I plug in the wireless dongle from another laptop I get two connections available for use in network manager, but when I plug this one in nothing seems to happen.

```
$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 148f:3370 Ralink Technology, Corp. 
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

``````
$ lsmod
Module                  Size  Used by
aes_i586                7268  1 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203310  1 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
joydev                  8708  0 
snd_hda_intel          21941  0 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
arc4                    1153  2 
snd_pcm                70662  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26726  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
ath5k                 121792  0 
i915                  285076  4 
snd_timer              19098  2 snd_pcm,snd_seq
mac80211              205146  1 ath5k
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
drm_kms_helper         29297  1 i915
acerhdf                 6691  0 
ath                     7611  1 ath5k
uvcvideo               56990  0 
drm                   162377  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd                    54148  12 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
intel_agp              24119  2 i915
videodev               34361  1 uvcvideo
cfg80211              126517  3 ath5k,mac80211,ath
soundcore               6620  1 snd
v4l1_compat            13251  2 uvcvideo,videodev
psmouse                63245  0 
serio_raw               3978  0 
led_class               2864  1 ath5k
video                  17375  1 i915
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
lp                      7028  0 
parport                32635  2 ppdev,lp
r8169                  34076  0 
mii                     4381  1 r8169

```I've searched other threads but these all seem to deal with driver conflicts, but I think my problem is more fundamental, it looks to me as if it isn't loading any drivers.

The box says it works on linux, but as usual the instructions and CD only deals with Windows.  Any suggestions?  Thanks.

---

### Post by chili555 on 2010-07-22
> Bus 001 Device 004: ID 148f:[COLOR="Red"]3370[/COLOR] Ralink Technology, Corp.Did you mean to type 3070 here?

If it is indeed a 3070, it is indeed conflicted; being claimed by both rt2870sta and rt2800usb.

It may be that your built-in wireless card is loading the ath5k driver and the system gives up:> snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
[COLOR="Red"]ath5k[/COLOR]                 121792  0 
i915                  285076  4 
snd_timer              19098  2 snd_pcm,snd_seq
mac80211              205146  1 [COLOR="Red"]ath5k[/COLOR]
Please clarify.

---

### Post by pink_book7 on 2010-07-24
You are right, I'm a complete muppet, I have no idea why I typed 3070, I mean 3370.  Sorry!

---

### Post by chili555 on 2010-07-25
No worries, we all make mistakes.

First, do:```
sudo gedit /etc/modprobe.d/blacklist.conf
```Make sure the following lines appear:```
blacklist rt2800usb
blacklist rt2x00lib
blacklist rt2x00usb
```Proofread, save and close gedit. Now, let's remove the wrong modules and load the correct ones:```
sudo su
echo rt2870sta >> /etc/modules
rmmod rt2800usb
rmmod rt2x00usb
rmmod rt2x00lib
modprobe rt2870sta
exit
iwconfig
```Is it working now? If not, please post:```
dmesg | grep 2870
```Thanks.

---

