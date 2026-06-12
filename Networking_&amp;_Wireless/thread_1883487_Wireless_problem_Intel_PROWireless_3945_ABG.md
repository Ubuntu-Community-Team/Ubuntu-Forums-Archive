---
title: "Wireless problem: Intel PRO/Wireless 3945 ABG"
date: 2011-11-19
forum: Networking &amp; Wireless
---

### Post by RBHarris on 2011-11-19
Hi I have a Gateway M series laptop that used to work fine on the old Ubuntu i updated a week ago and havent been able to get the wireless to work. I have read all the related threads i could find but still havent got anywhere...
(The wireless hardware switch is in the on position!)
Below is a list of commands and responses they returned:

```
nm-tool
```

```
NetworkManager Tool

State: disconnected

- Device: eth0  [Wired connection 1] -------------------------------------------
  Type:              Wired
  Driver:            r8169
  State:             unavailable
  Default:           no
  HW Address:        00:03:25:4D:47:5B

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

 
- Device: wlan0 ----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwl3945
  State:             unavailable
  Default:           no
  HW Address:        00:1B:77:9A:85:7E

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 
   
```

```
iwconfig
```
```
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
```

```
rfkill list all
```

```
0: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: no
```

```
 sudo iwlist scan 
```

```
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wlan0     Interface doesn't support scanning : Network is down
```

```
lsmod | grep iwl
```


```
iwl3945               130113  0 
iwlcore               148965 1 iwl3945
mac80211              257001 2 iwl3945,iwlcore
cfg80211              156212 3 iwl3945,iwlcore,mac80211
```


The only difference i can see from other posts I have read is that when
```
nm-tool 
```
is returned the wireless state is:
```
State: unavailable
```

Any help would be great thanks in advance.

---

### Post by praseodym on 2011-11-19
Hi,

your card is off:
```
wlan0     IEEE 802.11abg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=[COLOR="Red"]0[/COLOR]
```
Due to the fact, that "rfkill list" doesnt show any block, it looks like a "real" hardware button/switch/key/key combination or you may have a look into your BIOS settings, if wireless can be activated there.
Please show additionally:
```
lsmod
iwlist chan
```
Which channel does you router send? Tried channel 1?

---

### Post by RBHarris on 2011-11-19
Hi results:

```
Module                  Size  Used by 
parport_pc             32111  0 
ppdev                  12849  0 
snd_hda_codec_hdmi     27479  1 
snd_hda_codec_idt      60537  1 
joydev                 17322  0 
arc4                   12473  2 
binfmt_misc            13213  1 
iwl3945               130113  0 
snd_hda_intel          24140  2 
iwlcore               148965  1 iwl3945 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel 
mac80211              257001  2 iwl3945,iwlcore 
snd_hwdep              13274  1 snd_hda_codec 
snd_pcm                80244  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi 
i915                  450944  2 
snd_seq_midi_event     14475  1 snd_seq_midi 
cfg80211              156212  3 iwl3945,iwlcore,mac80211 
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event 
snd_timer              28659  2 snd_pcm,snd_seq 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq 
psmouse                73312  0 
uvcvideo               66851  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device 
videodev               75143  1 uvcvideo 
drm_kms_helper         40745  1 i915 
serio_raw              12990  0 
drm                   180037  3 i915,drm_kms_helper 
soundcore              12600  1 snd 
i2c_algo_bit           13184  1 i915 
video                  18951  1 i915 
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp 
usb_storage            43946  0 
uas                    17676  0 
r8169                  42534  0 
ahci                   21591  2 
libahci                25548  1 ahci 
```

and:


```
lo        no frequency information. 

eth0      no frequency information. 

wlan0     32 channels in total; available frequencies : 
          Channel 01 : 2.412 GHz 
          Channel 02 : 2.417 GHz 
          Channel 03 : 2.422 GHz 
          Channel 04 : 2.427 GHz 
          Channel 05 : 2.432 GHz 
          Channel 06 : 2.437 GHz 
          Channel 07 : 2.442 GHz 
          Channel 08 : 2.447 GHz 
          Channel 09 : 2.452 GHz 
          Channel 10 : 2.457 GHz 
          Channel 11 : 2.462 GHz 
          Channel 12 : 2.467 GHz 
          Channel 13 : 2.472 GHz 
          Channel 34 : 5.17 GHz 
          Channel 36 : 5.18 GHz 
          Channel 38 : 5.19 GHz 
          Channel 40 : 5.2 GHz 
          Channel 42 : 5.21 GHz 
          Channel 44 : 5.22 GHz 
          Channel 46 : 5.23 GHz 
          Channel 48 : 5.24 GHz 
          Channel 52 : 5.26 GHz 
          Channel 56 : 5.28 GHz 
          Channel 60 : 5.3 GHz 
          Channel 64 : 5.32 GHz 
          Channel 100 : 5.5 GHz 
          Channel 104 : 5.52 GHz 
          Channel 108 : 5.54 GHz 
          Channel 112 : 5.56 GHz 
          Channel 116 : 5.58 GHz 
          Channel 120 : 5.6 GHz 
          Channel 124 : 5.62 GHz
```

I'm unsure what channel the routers on? How would i find out? 
Thanks

---

### Post by RBHarris on 2011-11-19
Thanks so much after running those two commands just restarted and went into BIOS WLAN was set to restore not sure why but set it to on and all good now! Thanks again you've no idea how much that's been bugging me!

---

### Post by praseodym on 2011-11-19
Obviously the router is sending in N-mode, too (5 GHz-band visible). Connect via cable to the router and type in the IP address of it into your browser. Check the mode (the card only can handle a+b+g, nothing with n).

Edit: Too late ;-) Glad its working

---

