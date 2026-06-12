---
title: "Wifi dongle on already-wifi-enabled netbook"
date: 2011-01-01
forum: Networking &amp; Wireless
---

### Post by Fallingwater on 2011-01-01
I have a EeePC 1005HA that I normally use with its own wifi system. Problem is, I need to pick up distant connections, which means [repurposing a satellite dish](http://www.usbwifi.orconhosting.net.nz/) as a directional wifi antenna - something that requires me to use a USB wifi dongle.

I have a Zydas-based dongle that I'd like to use, but UNR (version 10.04.1) can't seem to see it. I've looked up the drivers, but I've found several pages saying that the current kernels should have the driver built-in... but when I plug it in (after disabling the EeePC's own wifi adapter), nothing happens. The green light on the dongle comes on, but wicd doesn't see any networks (tinkering with the options didn't help), lspci doesn't see anything new connected and ifconfig shows no new adapters.

What to do?

Thanks.

---

### Post by PatchesTheCaveman on 2011-01-01
lspci only list's PCI devices (hence its name).  You want:
```
sudo lsusb
```

If you still have trouble, copy and paste that commands output and the output of this command into a reply here and we'll see what we can do:
```
lsmod
```

---

### Post by Fallingwater on 2011-01-02
Right, sorry. Can't believe I didn't figure that out myself.

Here's lsusb:

```
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
**Bus 001 Device 003: ID 0ace:1215 ZyDAS WLA-54L 802.11bg**
Bus 001 Device 002: ID 058f:6335 Alcor Micro Corp. SD/MMC Card Reader
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```Here's lsmod:

```
Module                  Size  Used by
zd1211rw               42217  0 
nls_iso8859_1           3249  1 
nls_cp437               4919  1 
vfat                    8933  1 
fat                    47767  1 vfat
binfmt_misc             6587  1 
ppdev                   5259  0 
snd_hda_codec_realtek   203344  1 
joydev                  8708  0 
fbcon                  35102  71 
tileblit                2031  1 fbcon
font                    7557  1 fbcon
bitblit                 4707  1 fbcon
softcursor              1189  1 bitblit
vga16fb                11385  0 
vgastate                8961  1 vga16fb
arc4                    1153  4 
snd_hda_intel          22005  2 
snd_hda_codec          74201  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep               5412  1 snd_hda_codec
snd_pcm_oss            35308  0 
snd_mixer_oss          13746  1 snd_pcm_oss
snd_pcm                70694  3 snd_hda_intel,snd_hda_codec,snd_pcm_oss
snd_seq_dummy           1338  0 
snd_seq_oss            26722  0 
snd_seq_midi            4557  0 
snd_rawmidi            19056  1 snd_seq_midi
snd_seq_midi_event      6003  2 snd_seq_oss,snd_seq_midi
snd_seq                47263  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
i915                  287426  4 
ath9k                 306138  0 
snd_timer              19098  2 snd_pcm,snd_seq
drm_kms_helper         29329  1 i915
snd_seq_device          5700  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
mac80211              205402  2 zd1211rw,ath9k
ath                     7611  1 ath9k
drm                   162409  5 i915,drm_kms_helper
i2c_algo_bit            5028  1 i915
snd                    54180  16 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              126528  4 zd1211rw,ath9k,mac80211,ath
intel_agp              24375  2 i915
psmouse                63245  0 
serio_raw               3978  0 
atl1c                  28083  0 
video                  17375  1 i915
led_class               2864  1 ath9k
eeepc_laptop           14331  0 
agpgart                31724  2 drm,intel_agp
soundcore               6620  1 snd
snd_page_alloc          7076  2 snd_hda_intel,snd_pcm
output                  1871  1 video
lp                      7028  0 
parport                32635  2 ppdev,lp
usb_storage            39553  1 
ahci                   32200  2 

```

I see several references to zd1211rw, which is presumably related to the wifi dongle, but I'm not sure how to interpret this.

---

### Post by PatchesTheCaveman on 2011-01-02
Yep, that's your driver.  Run ```
dmesg | grep -i zd1211
``` to see if the driver is reporting any errors.

---

### Post by Fallingwater on 2011-01-03
```
[  117.574087] zd1211rw 1-5:1.0: phy1
[  117.574206] usbcore: registered new interface driver zd1211rw
```

Still doesn't show up in ifconfig...

---

### Post by PatchesTheCaveman on 2011-01-03
Weird.  The kernel's registering it.  What does
```
sudo iwconfig
```
show?

---

### Post by Fallingwater on 2011-01-03
Found the problem - disabling the internal wifi via fn+f2 key disables ALL wifi, including the external dongle. That's why nothing worked. Leaving the internal wifi on also allows the dongle to work.

Thanks for the help!

---

