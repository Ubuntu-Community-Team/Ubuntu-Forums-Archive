---
title: "Ubuntu 12.04 no wireless"
date: 2012-04-28
forum: Networking &amp; Wireless
---

### Post by dosh on 2012-04-28
I just updated to 12.04 now I have no wireless. Ran Additional Drivers showed Broadcom STA wireless driver. It failed to load. I know I had a similar problem last time I updated can't remember what I did then to get it working. It is a Broadcom BCM43224 802.11a/b/g/n. I tried a number of things they suggest for Ubuntu 11 no success. Any help much appreciated.

---

### Post by praseodym on 2012-04-28
Please show:

```
iwconfig
lsmod
rfkill list
sudo iwlist scan
```

---

### Post by dosh on 2012-04-28
iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

lsmod
Module                  Size  Used by
btusb                  17912  0 
snd_hda_codec_hdmi     31775  1 
snd_hda_codec_conexant    52365  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  11 btusb,rfcomm,bnep
binfmt_misc            17292  1 
joydev                 17393  0 
snd_hda_intel          32765  3 
snd_hda_codec         109562  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
thinkpad_acpi          73942  0 
nvram                  14029  1 thinkpad_acpi
psmouse                72919  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
mac_hid                13077  0 
snd                    62064  17 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,thinkpad_acpi,snd_timer,snd_seq_device
i915                  414603  3 
drm_kms_helper         45466  1 i915
drm                   197692  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
mei                    36570  0 
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
sdhci_pci              18324  0 
r8169                  56321  0 
sdhci                  28241  1 sdhci_pci

rfkill list
0: tpacpi_bluetooth_sw: Bluetooth
	Soft blocked: yes
	Hard blocked: no

sudo iwlist scan

lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

---

### Post by praseodym on 2012-04-28
There is no driver listed:

> sudo apt-get install bcmwl-kernel-source dkms patch fakeroot
Activate it via "additional drivers". Device is listed?

> lspci -nnk | grep -iA2 net

---

### Post by dosh on 2012-04-28
found the solution see

[http://ubuntuforums.org/showthread.php?t=1966012&highlight=bcm43224&page=2](http://ubuntuforums.org/showthread.php?t=1966012&highlight=bcm43224&page=2)

---

