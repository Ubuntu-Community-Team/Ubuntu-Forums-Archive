---
title: "No wireless networks detected?"
date: 2013-04-14
forum: Networking &amp; Wireless
---

### Post by SemiAwake on 2013-04-14
Hello everyone, I'm very new to Ubuntu and I have encountered a problem upon trying it. (I have been running Ubuntu live from a bootable USB). I cannot detect ANY wireless networks. (I double checked to make sure the wireless was on and my internet was working). I think it may be a wireless card issue. If it's a compatibility issue, could someone post a wireless card (preferably PCI based, but I can settle for USB) that is compatible? Thanks,
-SemiAwake
According to Device Manager in Windows, my wireless card is the Broadcom 802.11g Network Adapter. I can't get an exact model name out of it...

---

### Post by praseodym on 2013-04-14
Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by SemiAwake on 2013-04-14
> **praseodym said:**
> Hi,

please open a terminal with CTRL+ALT+T and show the outputs of these commands:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```
I'm having a problem with this, the document shows a bunch of random symbols when I try to run it in Windows.

---

### Post by praseodym on 2013-04-14
Please run it from the bootable USB with Linux. You can either make screenshots or copy the outputs to a text file and upload it.

---

### Post by SemiAwake on 2013-04-14
Sorry, I poorly worded that. I ran the commands in Ubuntu, copied the outputs into a document and when I open the document in Windows it shows a bunch of random symbols.

---

### Post by praseodym on 2013-04-14
Obviously the windows editor does not use UTF-8 code. Just upload the file using "advanced" mode and "manage attachments"

---

### Post by SemiAwake on 2013-04-14
Could you please tell me how to do that?

---

### Post by praseodym on 2013-04-14
Try it like that:
```

lspci -nnk | grep -iA2 net >> output.txt
lsmod >> output.txt
iwconfig >> output.txt
rfkill list >> output.txt
```
It creates a file named "output.txt" in the "ubuntu" folder of the live system. Copy/paste its content here.

---

### Post by SemiAwake on 2013-04-14
> **praseodym said:**
> Try it like that:
```

lspci -nnk | grep -iA2 net >> output.txt
lsmod >> output.txt
iwconfig >> output.txt
rfkill list >> output.txt
```
It creates a file named "output.txt" in the "ubuntu" folder of the live system. Copy/paste its content here.
Thanks a million it worked.
```
lspci -nnk | grep -iA2 net
Module                  Size  Used by
nls_iso8859_1          12617  1 
snd_hda_codec_hdmi     31423  1 
snd_hda_codec_realtek    63356  1 
dcdbas                 14054  0 
kvm                   357806  0 
rfcomm                 37276  0 
psmouse                84843  0 
serio_raw              13031  0 
k8temp                 12842  0 
parport_pc             31968  0 
snd_hda_intel          32515  5 
bnep                   17707  2 
snd_hda_codec         111547  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
ppdev                  12817  0 
bluetooth             183228  10 rfcomm,bnep
snd_pcm                80163  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
nouveau               823577  2 
snd_seq_midi           13132  0 
b43                   347284  0 
mac80211              461161  1 b43
ttm                    75534  1 nouveau
snd_rawmidi            25382  1 snd_seq_midi
drm_kms_helper         45271  1 nouveau
drm                   230463  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13197  1 nouveau
mxm_wmi                12859  1 nouveau
video                  18847  1 nouveau
wmi                    18590  2 nouveau,mxm_wmi
snd_seq_midi_event     14475  1 snd_seq_midi
cfg80211              175375  2 b43,mac80211
bcma                   34483  1 b43
snd_seq                51255  2 snd_seq_midi,snd_seq_midi_event
snd_timer              24411  2 snd_pcm,snd_seq
snd_seq_device         14137  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13037  0 
snd                    61991  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14599  1 snd
snd_page_alloc         14036  2 snd_hda_intel,snd_pcm
i2c_nforce2            12869  0 
lp                     13299  0 
parport                40753  3 parport_pc,ppdev,lp
hid_generic            12445  0 
usbhid                 41702  0 
hid                    82142  2 hid_generic,usbhid
uas                    17556  0 
usb_storage            39350  1 
ssb                    50087  1 b43
sata_nv                22993  2 
forcedeth              57756  0 
pata_amd               13750  0 



```
```
lsmod
00:07.0 Bridge [0680]: NVIDIA Corporation MCP61 Ethernet [10de:03ef] (rev a2)
	Subsystem: Dell Inspiron 531 [1028:020e]
	Kernel driver in use: forcedeth
--
01:09.0 Network controller [0280]: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller [14e4:4318] (rev 02)
	Subsystem: ASUSTeK Computer Inc. WL-138G v2 / WL-138gE / WL-100gE [1043:100f]
	Kernel driver in use: b43-pci-bridge



```

```
iwconfig
lo            no wireless extensions
eth0        no wireless extensions
```

```
rfkill list
``` did nothing....

---

### Post by praseodym on 2013-04-15
Install this package via double click:

[http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/multiverse/l/linux-firmware-nonfree/linux-firmware-nonfree_1.14_all.deb)

and reload the driver:
```

sudo modprobe -rfv b43
sudo modprobe -v b43
```

---

### Post by SemiAwake on 2013-04-15
So I double click it and it shows up in software center but the install button is greyed out. Is there another way to install it?

---

### Post by praseodym on 2013-04-16
Save it in "Downloads" and install via
```

sudo dpkg -i ~/Downloads/*.deb
```

---

