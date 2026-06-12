---
title: "HP Elitebook 2730p Wireless Card Disabled"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by Speedy on 2011-08-06
Hi 

The wireless card on my HP Elitebook 2730p disabled. 

I am running Ubuntu 11.04 64Bit

The Enable wireless is grayed out in the network manager.

If I do lshw -C network
 
  *-network DISABLED
       description: Wireless interface
       product: PRO/Wireless 5100 AGN [Shiloh] Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 00:21:6b:43:ea:64
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=iwlagn driverversion=2.6.38-10-generic firmware=8.83.5.1 build 33692 latency=0 link=no multicast=yes wireless=IEEE 802.11abgn

The wireless card is enabled in the bios, there is a wireless on off switch but that stays orange (off) even if switched.

Laptop did have windows on it before & I can remember if the wireless was on or off when I put Ubuntu on it. I had a TC1100 before & I had to modify a file to enable the wireless, something to do with if wireless is off when Ubuntu is built it remains off. 

Any help would be greatly appreciated.
Thank you
Steve

---

### Post by nm_geo on 2011-08-06
Give us the results of the following

```
rfkill list all
``````

lsmod
```Maybe we can spot something.

---

### Post by Speedy on 2011-08-07
Hi

Here is the output

rfkill list all
```
0: hp-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: hp-bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

```

lsmod
```
Module                  Size  Used by
binfmt_misc            17565  1 
sha256_generic         21031  2 
cryptd                 20510  0 
aes_x86_64             17208  342 
aes_generic            38279  1 aes_x86_64
parport_pc             36959  0 
dm_crypt               22993  1 
ppdev                  17113  0 
snd_hda_codec_analog    98042  1 
snd_hda_intel          33211  2 
snd_hda_codec         103804  2 snd_hda_codec_analog,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
arc4                   12529  2 
snd_pcm                96391  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
joydev                 17606  0 
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
iwlagn                333717  0 
iwlcore               167503  1 iwlagn
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
tpm_infineon           17572  0 
mac80211              294370  2 iwlagn,iwlcore
snd                    67382  13 snd_hda_codec_analog,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              12680  1 snd
hp_accel               21880  0 
psmouse                73535  0 
cfg80211              178528  3 iwlagn,iwlcore,mac80211
uvcvideo               72195  0 
videodev               82052  1 uvcvideo
lis3lv02d              19893  1 hp_accel
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
input_polldev          14007  1 lis3lv02d
serio_raw              13166  0 
tpm_tis                18537  0 
tpm                    22267  2 tpm_infineon,tpm_tis
tpm_bios               13684  1 tpm
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
hp_wmi                 13706  0 
v4l2_compat_ioctl32    17078  1 videodev
sparse_keymap          13898  1 hp_wmi
usbhid                 46956  0 
hid                    91020  1 usbhid
i915                  514975  3 
firewire_ohci          40370  0 
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
ahci                   25951  2 
firewire_core          62646  1 firewire_ohci
libahci                26642  1 ahci
e1000e                159096  0 
sdhci_pci              13989  0 
sdhci                  27387  1 sdhci_pci
crc_itu_t              12707  1 firewire_core
i2c_algo_bit           13400  1 i915
video                  19438  1 i915

```

Thanks
Steve

---

