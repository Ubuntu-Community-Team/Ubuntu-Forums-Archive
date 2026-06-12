---
title: "Wireless connection- no consistant connection"
date: 2013-05-24
forum: Networking &amp; Wireless
---

### Post by PDA1 on 2013-05-24
I'm running Ubuntu 10.04 netbook on a Acer Aspire One ZG5. It's a new clean installation.

The wireless connection isn't consistently "on".

That is- sometimes when I boot up the wireless icon is lit up and sometimes it's just blanked out. When I try to start the wireless connection by selecting (right click on the wireless icon) "enable wireless"....the computer doesn't attempt to connect to the wireless service.

Any ideas how to fix this?

---

### Post by praseodym on 2013-05-24
You know that 10.04 is outdazed and not supported anymore?

Please show the outputs of
```

lspci -nnk | grep -iA2 net
lsusb
lsmod
iwconfig
rfkill list
```

---

### Post by PDA1 on 2013-05-24
Yes, I know 10.04 is out of date but my Acer only runs on it- not 12.04.


Here's the output;

> 
$ lspci -nnk | grep -iA2 net
02:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd.  RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev  02)
    Kernel driver in use: r8169
    Kernel modules: r8169
03:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR5001 Wireless Network Adapter [168c:001c] (rev 01)
    Kernel driver in use: ath5k
    Kernel modules: ath5k
welcome@Welcome:~$ lsusb
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 046d:c52f Logitech, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 003: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
welcome@Welcome:~$ lsmod
Module                  Size  Used by
aes_i586                7268  111 
aes_generic            26863  1 aes_i586
binfmt_misc             6523  1 
ppdev                   5259  0 
dm_crypt               11331  0 
snd_hda_codec_realtek   203472  1 
snd_hda_intel          22069  2 
snd_hda_codec          74297  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
arc4                    1153  2 
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              19130  2 snd_pcm,snd_seq
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
ath5k                 121632  0 
mac80211              205434  1 ath5k
snd                    54244  16  snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
ath                     7611  1 ath5k
uvcvideo               57438  0 
acer_wmi               13861  0 
cfg80211              126496  3 ath5k,mac80211,ath
videodev               34457  1 uvcvideo
v4l1_compat            13251  2 uvcvideo,videodev
joydev                  8740  0 
psmouse                63677  0 
serio_raw               3978  0 
soundcore               6620  1 snd
led_class               2864  2 ath5k,acer_wmi
lp                      7060  0 
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
parport                32635  2 ppdev,lp
fbcon                  35102  71 
tileblit                1999  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
usbhid                 36110  0 
hid                    67288  1 usbhid
i915                  290772  4 
drm_kms_helper         29329  1 i915
drm                   163779  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
intel_agp              24375  2 i915
video                  17375  1 i915
r8169                  34140  0 
output                  1871  1 video
agpgart                31724  2 drm,intel_agp
mii                     4381  1 r8169
welcome@Welcome:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"PA7V5"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:90:BA:C3:9C   
          Bit Rate=48 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr[IMG]http://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff   Fragment thr[IMG]http://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff
          Power Management[IMG]http://ubuntuforums.org/images/smilies/icon_surprised.gif[/IMG]ff
          Link Quality=70/70  Signal level=-39 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

welcome@Welcome:~$ rfkill list
0: acer-wireless: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no

---

### Post by PDA1 on 2013-05-24
Wireless will work if I shut the computer down, remove the power and the battery THEN reattach the power back and battery.....boot up....right click on the wireless icon and select "enable wireless".

---

### Post by praseodym on 2013-05-24
** Soft blocked: yes**
Check:

```
sudo rfkill unblock all
```

---

