---
title: "Realtek Wireless USB not starting automatically"
date: 2013-09-04
forum: Networking &amp; Wireless
---

### Post by JonPaul on 2013-09-04
I have a high-spead wireless USB stick which I want to use instead of the slower on-board atheros.

I managed to disable the onboard but the stick does not start automatically - after booting I have to plug it out and in.

After replugging it connects automatically

Any ideas? 

paul@paul:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Hewlett-Packard Company Device [103c:360b]
    Kernel driver in use: r8169
02:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR242x / AR542x Wireless Network Adapter (PCI-Express) [168c:001c] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:137b]
    Kernel driver in use: ath5k
paul@paul:~$ 

paul@paul:~$ lsusb
Bus 001 Device 002: ID 0bda:0158 Realtek Semiconductor Corp. USB 2.0 multicard reader
Bus 001 Device 003: ID 04f2:b091 Chicony Electronics Co., Ltd Webcam
Bus 002 Device 006: ID 0bda:8172 Realtek Semiconductor Corp. RTL8191SU 802.11n WLAN Adapter
Bus 002 Device 003: ID 05e3:0608 Genesys Logic, Inc. USB-2.0 4-Port HUB
Bus 008 Device 002: ID 045e:0734 Microsoft Corp. Wireless Optical Desktop 700
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 008 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 005: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

---

### Post by kc-koellein on 2013-09-04
I don't have your technical answer, but have you tried installing with this USB wifi adapter connected?

It would be a lazy cheater solution, but it should work. I did that for my kids' computers. Different wifi adapters, too. Ubuntu from 10.04 to 12.04. Xubuntu, Lubuntu, Ubuntu. 

I don't have time to solve every problem around here...!  :-)

HTH,
K9SPY

---

### Post by praseodym on 2013-09-04
Please show
```

lsmod
```
For the internal adapter try to deactivate the hardware encryption of the driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

---

### Post by JonPaul on 2013-09-05
Thank you for your reply 
lsmod
```

paul@paul:~$ lsmod
Module                  Size  Used by
nls_iso8859_1          12713  1 
parport_pc             28152  0 
ppdev                  17073  0 
bnep                   18036  2 
rfcomm                 42641  0 
bluetooth             228667  10 bnep,rfcomm
binfmt_misc            17500  1 
joydev                 17377  0 
snd_hda_codec_hdmi     36913  1 
snd_hda_codec_conexant    62000  1 
gpio_ich               13476  0 
arc4                   12615  2 
coretemp               13355  0 
hp_wmi                 18048  0 
sparse_keymap          13890  1 hp_wmi
microcode              22881  0 
psmouse                95905  0 
serio_raw              13215  0 
r8712u                187938  0 
uvcvideo               80847  0 
videobuf2_vmalloc      13056  1 uvcvideo
videobuf2_memops       13202  1 videobuf2_vmalloc
videobuf2_core         40513  1 uvcvideo
videodev              129260  2 uvcvideo,videobuf2_core
snd_hda_intel          39619  3 
snd_hda_codec         136453  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13602  1 snd_hda_codec
snd_pcm                97451  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         18710  2 snd_pcm,snd_hda_intel
snd_seq_midi           13324  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_rawmidi            30180  1 snd_seq_midi
snd_seq                61554  2 snd_seq_midi_event,snd_seq_midi
snd_seq_device         14497  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              29425  2 snd_pcm,snd_seq
lpc_ich                17061  0 
ath5k                 149933  0 
wmi                    19070  1 hp_wmi
ath                    23827  1 ath5k
snd                    68876  16 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
mac80211              606457  1 ath5k
mac_hid                13205  0 
i915                  600396  3 
video                  19390  1 i915
drm_kms_helper         49394  1 i915
drm                   286028  4 i915,drm_kms_helper
cfg80211              510937  3 ath,ath5k,mac80211
lp                     17759  0 
i2c_algo_bit           13413  1 i915
parport                46345  3 lp,ppdev,parport_pc
soundcore              12680  1 snd
hid_generic            12540  0 
usbhid                 47074  0 
hid                   101002  2 hid_generic,usbhid
ums_realtek            17949  0 
usb_storage            57204  2 ums_realtek
ahci                   25731  4 
libahci                31364  1 ahci
r8169                  67466  0
```

---

### Post by JonPaul on 2013-09-05
> **praseodym said:**
> Please show
```

lsmod
```
For the internal adapter try to deactivate the hardware encryption of the driver:
```

echo "options ath5k nohwcrypt=1" | sudo tee -a /etc/modprobe.d/ath5k.conf
sudo modprobe -rfv ath5k
sudo modprobe -v ath5k
```

Did the above . No observable difference

The thing is, the USB device is working, it just does not come on with boot. I have to pull it out and plug it in every time. 
it seems that the module r8169 loads OK. I did the lsmod command after boot but before plugging out and in just to make sure.

Thanks again

JonPaul

---

### Post by JonPaul on 2013-09-05
Hi K9SPY

Thanks for your reply - it simply is not a hassle enough to make me reload the OS!

Best

JonPaul

---

### Post by JonPaul on 2013-09-14
Came right by itself

---

