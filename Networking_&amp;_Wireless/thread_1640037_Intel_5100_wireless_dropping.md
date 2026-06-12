---
title: "Intel 5100 wireless dropping"
date: 2010-12-07
forum: Networking &amp; Wireless
---

### Post by Cheetah05 on 2010-12-07
Hi there,

I have just switch to Ubuntu on my laptop from Windows 7 and I am experiencing alot of wireless dropping.

The signal itself is full and I am very close to the router.

What could be the issue and how do I go about rectifying it.

Laptop: Dell 13z.
Wireless: Intel 5100 agn
Ubuntu 10.10 x64.

Thanks.

---

### Post by MooPi on 2010-12-07
Can you give us the results of these commands from terminal?```
lsmod
```
and ```
iwconfig
```

---

### Post by Cheetah05 on 2010-12-07
Thanks for the response. Here are the results:

(I am downstairs so the signal may not be as good as good as I claimed in the OP, if you need results where I usually am, just say)

```

Module                  Size  Used by
cryptd                  8140  0 
aes_x86_64              7936  1 
aes_generic            27631  1 aes_x86_64
parport_pc             30086  0 
ppdev                   6804  0 
snd_hda_codec_intelhdmi    11032  1 
snd_hda_codec_realtek   299524  1 
binfmt_misc             7984  1 
vboxnetadp              5267  0 
vboxnetflt             14966  0 
rfcomm                 40787  0 
joydev                 11363  0 
sco                     9986  2 
bnep                   11985  2 
vboxdrv              1792408  2 vboxnetadp,vboxnetflt
l2cap                  42304  6 rfcomm,bnep
btusb                  12929  0 
bluetooth              59245  7 rfcomm,sco,bnep,l2cap,btusb
arc4                    1497  2 
snd_hda_intel          26019  2 
snd_hda_codec         100919  3 snd_hda_codec_intelhdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               6660  1 snd_hda_codec
snd_pcm                89104  2 snd_hda_intel,snd_hda_codec
iwlagn                202721  0 
i915                  332088  3 
snd_seq_midi            5932  0 
snd_rawmidi            22207  1 snd_seq_midi
snd_seq_midi_event      7291  1 snd_seq_midi
drm_kms_helper         32836  1 i915
snd_seq                57512  2 snd_seq_midi,snd_seq_midi_event
iwlcore               146875  1 iwlagn
snd_timer              23850  2 snd_pcm,snd_seq
snd_seq_device          6912  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               62379  0 
mac80211              266657  2 iwlagn,iwlcore
drm                   206161  4 i915,drm_kms_helper
usbhid                 42062  0 
hid                    84678  1 usbhid
dell_wmi                3372  0 
snd                    64117  13 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              170293  3 iwlagn,iwlcore,mac80211
videodev               49359  1 uvcvideo
v4l1_compat            15519  2 uvcvideo,videodev
v4l2_compat_ioctl32    12486  1 videodev
dell_laptop             6722  0 
dcdbas                  6910  1 dell_laptop
psmouse                62080  0 
serio_raw               4910  0 
soundcore               1240  1 snd
snd_page_alloc          8588  2 snd_hda_intel,snd_pcm
intel_agp              32144  2 i915
i2c_algo_bit            6208  1 i915
video                  22176  1 i915
lp                     10201  0 
output                  2527  1 video
parport                37032  3 parport_pc,ppdev,lp
usb_storage            50372  0 
ahci                   21857  0 
r8169                  42222  0 
libahci                26199  3 ahci
mii                     5261  1 r8169

```

```

lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:"Router Name"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Router MAC  
          Bit Rate=54 Mb/s   Tx-Power=15 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality=54/70  Signal level=-56 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

vboxnet0  no wireless extensions.

```

---

### Post by Cheetah05 on 2010-12-11
Bump!

---

### Post by uncaspi on 2010-12-11
Try to switch the power management of the card off.

sudo iwcoonfig wlan0 power off

---

### Post by Cheetah05 on 2010-12-11
> **uncaspi said:**
> Try to switch the power management of the card off.

sudo iwcoonfig wlan0 power off

Will try that and post results. In the mean time, what does the power management do exactly? Just turn the wireless power down when it's not being used? Do you think its turning the power down too much and dropping the signal?

---

