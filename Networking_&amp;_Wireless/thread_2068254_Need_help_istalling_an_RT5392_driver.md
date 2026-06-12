---
title: "Need help istalling an RT5392 driver"
date: 2012-10-08
forum: Networking &amp; Wireless
---

### Post by s.v.z on 2012-10-08
Hi! I have a D-Link DWA-140 Rev.B3 wi-fi stick which doesn't work out of the box in Ubuntu. So far I've discovered that unlike Rev1, Rev2 it uses an RT5392 chipset, so rt2800 drivers won't do. I have found a number of links to rt5392 drivers like [this]("https://launchpad.net/~marko-martinovic-deactivatedaccount/+archive/ralink-wireless-drivers") one but it seems to be obsolete. The files needed are not found there. 

I'll be grateful for any help on making this beast work. Additional thanks if the driver will support the mac80211 stack.

---

### Post by varunendra on 2012-10-09
Please post the outputs of:
```
lsusb
lsmod
```

---

### Post by s.v.z on 2012-10-09
> **varunendra said:**
> Please post the outputs of:
```
lsusb
lsmod
```

Here you go:
**lsusb**
```

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 004: ID 2001:3c15 D-Link Corp. 
Bus 003 Device 002: ID 09da:000a A4 Tech Co., Ltd Optical Mouse Opto 510D
Bus 003 Device 003: ID 1c4f:0002 SiGma Micro Keyboard TRACER Gamma Ivory
Bus 002 Device 002: ID 1307:0165 Transcend Information, Inc. 2GB/4GB Flash Drive

```

**lsmod**
```

Module                  Size  Used by
dm_crypt               22528  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_realtek   174222  1 
snd_hda_intel          32765  5 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    62064  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
parport_pc             32114  0 
bnep                   17830  2 
rfcomm                 38139  0 
ppdev                  12849  0 
joydev                 17393  0 
psmouse                72919  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
sp5100_tco             13495  0 
bluetooth             158438  10 bnep,rfcomm
i2c_piix4              13093  0 
mac_hid                13077  0 
serio_raw              13027  0 
k10temp                12990  0 
lp                     17455  0 
dm_multipath           22710  0 
parport                40930  3 parport_pc,ppdev,lp
squashfs               36095  1 
overlayfs              27511  1 
nls_iso8859_1          12617  1 
nls_cp437              12751  1 
vfat                   17308  1 
fat                    55605  1 vfat
uas                    17828  0 
usb_storage            39646  1 
dm_raid45              76451  0 
xor                    25987  1 dm_raid45
dm_mirror              21822  0 
dm_region_hash         16065  1 dm_mirror
dm_log                 18193  3 dm_raid45,dm_mirror,dm_region_hash
btrfs                 638208  0 
zlib_deflate           26622  1 btrfs
libcrc32c              12543  1 btrfs
hid_a4tech             12590  0 
usbhid                 41906  0 
hid                    77367  2 hid_a4tech,usbhid
radeon                737789  3 
wmi                    18744  0 
pata_atiixp            12999  0 
ttm                    65344  1 radeon
drm_kms_helper         45466  1 radeon
drm                   197692  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13199  1 radeon
ati_agp                13242  0 
r8169                  56321  0 

```

And one more question now: I tried to make/install a driver that installed successfully, but doesn't work. How do I remove it from the system now? :)

---

### Post by varunendra on 2012-10-10
How did you find out that it is an RT5392 chip? The device/vendor id suggests to me that the rt5372 driver from [ralink]("http://www.ralinktech.com/en/04_support/support.php?sn=501") may be the suitable one for this chip.

Which driver(s) have you tried so far? And from where?

As for removing an existing one, if you compiled it, it should have created an uninstall script to do so. The 'Install' or 'readme' file usually included with such packages contains that information. But it is not necessary unless it is conflicting with a working one.

**EDIT:**
Please refer to Ubuntu wireless device support page here: [https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink)
Look for "DWA-140/B3" under USB section. Your Vendor: ProductId is the same (2001:3c15), which means the rt5370sta driver should also work. But please try the rt5372 driver from ralink first, as it appears to be more promising according to some posts I found.

---

### Post by s.v.z on 2012-10-10
I installed the Ralink RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB driver and it seems to work, but now lsmod shows rt5370sta instead of rt5372. Is that normal?

As for RT5392, I found some clues [here]("http://wikidevi.com/wiki/D-Link_DWA-140_rev_B3"), [here]("http://rt2x00.serialmonkey.com/phpBB/viewtopic.php?f=5&t=6202") and in a number of other places.
Actually the first link refers to a different Vendor: ProductId, but the second one is about the right one.

---

### Post by varunendra on 2012-10-11
> **s.v.z said:**
> I installed the Ralink RT8070 /RT3070 /RT3370 /RT5370 /RT5372 USB driver and it seems to work, but now lsmod shows rt5370sta instead of rt5372. Is that normal?

I can't say, since I have never compiled that module myself, but taking a look at the installation script (in the extracted folder) should tell you which module it probes at the end. But since it is an interesting point, I may download the package myself, when I get enough time to do so, to see what it is supposed to do.

But how is the performance so far anyway?


**EDIT:**
Based on the info in [this post]("http://ubuntuforums.org/showthread.php?p=11831414") (which you have already visited 6 days ago), the rt5370sta seems to be the module that package is supposed to build, so it's normal.

As suggested in the post #20 on the same page, you should take note of the suggested commands to be able to rebuild the module after kernel upgrades.

---

### Post by s.v.z on 2012-10-11
Ok, then. Thanks for your time. :) 

rt5370sta seems to work fine. As for the performance, it goes on 54 Mb/s. Guess that'd be enough for a while.

---

