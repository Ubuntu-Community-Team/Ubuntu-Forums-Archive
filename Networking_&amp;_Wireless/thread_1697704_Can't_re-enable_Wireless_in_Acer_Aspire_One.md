---
title: "Can't re-enable Wireless in Acer Aspire One"
date: 2011-03-01
forum: Networking &amp; Wireless
---

### Post by DarkAz on 2011-03-01
Greetings, 

Up to yesterday, my netbook was working fine with Ubuntu 10.04 NBE. However, after turning it on today I see that the Networking has been turned off (nothing a right click didn't fix). Sadly the Wireless is proving to be a bit more stubborn.

```

$ lsmod
Module                  Size  Used by
aes_i586                7268  189 
aes_generic            26863  1 aes_i586
binfmt_misc             6587  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203408  1 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
joydev                  8740  0 
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
arc4                    1153  2 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
uvcvideo               57310  0 
snd_timer              19098  2 snd_pcm,snd_seq
videodev               34361  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
ath5k                 121632  0 
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
psmouse                63245  0 
mac80211              205402  1 ath5k
ath                     7611  1 ath5k
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
acerhdf                 6691  0 
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
serio_raw               3978  0 
cfg80211              126528  3 ath5k,mac80211,ath
lp                      7028  0 
led_class               2864  1 ath5k
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
i915                  287458  4 
drm_kms_helper         29329  1 i915
intel_agp              24375  2 i915
drm                   162409  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
r8169                  34108  0 
agpgart                31724  2 intel_agp,drm
mii                     4381  1 r8169
video                  17375  1 i915
output                  1871  1 video

```

> 
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power= off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: off



> 
~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:1e:68:b7:52:6a  
          inet addr:192.168.1.4  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:68ff:feb7:526a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:894 errors:0 dropped:0 overruns:0 frame:0
          TX packets:814 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:779565 (779.5 KB)  TX bytes:172826 (172.8 KB)
          Interrupt:28 Base address:0x6000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:12 errors:0 dropped:0 overruns:0 frame:0
          TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:720 (720.0 B)  TX bytes:720 (720.0 B)


> 
$ rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes


I've tried the following commands:

> 
$ sudo ifconfig wlan0 up
SIOCSIFFLAGS: Unknown error 132

$ sudo iwconfig wlan0 power on
Error for wireless request "Set Power Management" (8B2C) :
    SET failed on device wlan0 ; Operation not supported.

Ethernet is working fine, but it seems I can't turn the wireless back on, which was working fine so far. I've tried searching for the hard blocked issue, but didn't get any worthwhile (as far as I could see) results.

Any and every help would be very appreciated.

SOLVED BY:
Well, that was a bit easy. After inserting a USB WIFI driver, I was able to see my wireless module version (Atheros AR5001) and did [this]("http://ubuntuforums.org/showpost.php?p=9361100&postcount=7"), one restart later everything is back to normal.

---

