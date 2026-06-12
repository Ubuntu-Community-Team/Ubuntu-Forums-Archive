---
title: "Ralink RT3090"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by Simica on 2013-03-12
I have installed MInt Nadia and that solved problem. Thanks.

---

### Post by varunendra on 2013-03-13
Hi!

Please do -
```
lspci -nnk | grep -iA2 net
lsmod
```
Enter these commands in a terminal (Ctrl+Alt+T) and post back their outputs here so we can see what chip and driver you are using.

---

### Post by Simica on 2013-03-13
hello
thanks for your reply.
here is the output:

```
tijana@TijanaUbuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Atheros Communications Inc. AR8132 Fast Ethernet [1969:1062] (rev c0)
    Subsystem: ASUSTeK Computer Inc. Device [1043:838a]
    Kernel driver in use: atl1c
--
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: AzureWave Device [1a3b:1087]
    Kernel driver in use: rt2800pci
```
```
tijana@TijanaUbuntu:~$ lsmod
Module                  Size  Used by
joydev                 17393  0 
eeepc_wmi              12949  0 
asus_wmi               19624  1 eeepc_wmi
sparse_keymap          13658  1 asus_wmi
snd_hda_codec_realtek   174313  1 
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
arc4                   12473  2 
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
rt2800pci              18340  0 
rt2800lib              53298  1 rt2800pci
snd_seq_midi_event     14475  1 snd_seq_midi
crc_ccitt              12627  1 rt2800lib
rt2x00pci              14202  1 rt2800pci
rt2x00lib              48875  3 rt2800pci,rt2800lib,rt2x00pci
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
mac80211              436493  3 rt2800lib,rt2x00pci,rt2x00lib
psmouse                86520  0 
serio_raw              13027  0 
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
cfg80211              178877  2 rt2x00lib,mac80211
eeprom_93cx6           12687  1 rt2800pci
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
bnep                   17830  2 
rfcomm                 38139  0 
parport_pc             32114  0 
bluetooth             158479  10 bnep,rfcomm
ppdev                  12849  0 
i915                  423451  3 
drm_kms_helper         45466  1 i915
drm                   197641  4 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19115  1 i915
wmi                    18744  1 asus_wmi
mac_hid                13077  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1c                  36718  0
```

---

### Post by varunendra on 2013-03-14
> **Simica said:**
> ```
--
02:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
    Subsystem: AzureWave Device [1a3b:1087]
    Kernel driver in use: **[COLOR="#B22222"]rt2800pci[/COLOR]**
```
You may try the proprietary driver from ralink : [http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501](http://www.mediatek.com/_en/07_downloads/01_windows.php?sn=501)

But let's try a parameter with the existing driver first. In terminal, please do-
```
sudo modprobe -rfv rt2800pci
sudo modprobe -v rt2800pci nohwcrypt=Y
```
..wait a few seconds for the wireless to get ready, then try to connect.

Also, make sure you are NOT using WPA/WPA2 mixed mode in the router. Preferably, keep it WPA2 only.

Let me know if it helps. Thanks.

---

### Post by Simica on 2013-03-17
It did not worked.
Also, on that web page I do not see driver for rt2800pci, can I use something else...
thanks!

---

### Post by varunendra on 2013-03-18
> **Simica said:**
> Also, on that web page I do not see driver for rt2800pci...
That is the driver name for native module, you need to look for the name of your chip, which is **RT3090**.
Precisely, this link on the page : [RT3090PCIe]("http://www.mediatek.com/_en/07_downloads/01-1_windowsDetail.php?sn=5015")

But I'd recommend you follow the Wireless Script link in my signature, and follow the instructions there to post here a detailed diagnostics report of the wireless, so we can see if there can be something we can further try with the native driver before trying the proprietary one.

---

