---
title: "Lenovo Z570 enable bluetooth"
date: 2012-06-16
forum: Networking &amp; Wireless
---

### Post by _sebastian_ on 2012-06-16
Hi there,

I have a Lenovo Z570 running Ubuntu 12.04. I have no problems with WiFi as [others]("http://ubuntuforums.org/showthread.php?t=1754420") have reported. But I can't use my bluetooth.

How can I enable and use the build in bluetooth?

```
$ lsmod
Module                  Size  Used by
dm_crypt               23125  1 
parport_pc             32866  0 
ppdev                  17113  0 
bnep                   18281  2 
rfcomm                 47604  0 
bluetooth             180104  10 bnep,rfcomm
nfsd                  277809  2 
nfs                   356307  1 
binfmt_misc            17540  1 
lockd                  86161  2 nfsd,nfs
fscache                61529  1 nfs
auth_rpcgss            53380  2 nfsd,nfs
nfs_acl                12883  2 nfsd,nfs
sunrpc                245464  16 nfsd,nfs,lockd,auth_rpcgss,nfs_acl
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
acer_wmi               28418  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
rts5139               351143  0 
snd_rawmidi            30748  1 snd_seq_midi
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
arc4                   12529  2 
v4l2_compat_ioctl32    17128  1 videodev
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
ideapad_laptop         18234  0 
sparse_keymap          13890  2 acer_wmi,ideapad_laptop
psmouse                87692  0 
serio_raw              13211  0 
ath9k                 132390  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
mac80211              506816  1 ath9k
ath9k_common           14053  1 ath9k
ath9k_hw              411112  2 ath9k,ath9k_common
ath                    24067  3 ath9k,ath9k_common,ath9k_hw
cfg80211              205544  3 ath9k,mac80211,ath
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
mac_hid                13253  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
wmi                    19256  1 acer_wmi
i915                  468745  3 
r8169                  62099  0 
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
usbhid                 47199  0 
hid                    99559  1 usbhid
i2c_algo_bit           13423  1 i915
video                  19596  1 i915

```

```

$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: yes
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```

---

### Post by davidbilla on 2012-06-23
Hi,

Did you manage to solve this problem? I have a Lenovo Y570 running 12.04 and I have the same problem. Wireless works fine but not bluetooth.

lsmod gives:
```
$ lsmod
Module                  Size  Used by
btusb                  18288  1 
usbhid                 47199  0 
hid                    99559  1 usbhid
bbswitch               13396  0 
rfcomm                 47604  0 
bnep                   18281  2 
parport_pc             32866  0 
[COLOR="Red"]bluetooth             180104  13 btusb,rfcomm,bnep[/COLOR]
ppdev                  17113  0 
joydev                 17693  0 
snd_hda_codec_hdmi     32474  1 
snd_hda_codec_realtek   223867  1 
arc4                   12529  2 
mxm_wmi                12979  0 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  4 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
jmb38x_ms              17646  0 
memstick               16569  1 jmb38x_ms
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
v4l2_compat_ioctl32    17128  1 videodev
snd_timer              29990  2 snd_pcm,snd_seq
psmouse                87692  0 
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
iwlwifi               328352  0 
mac80211              506816  1 iwlwifi
serio_raw              13211  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
snd                    78855  19 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
cfg80211              205544  2 iwlwifi,mac80211
mei                    41616  0 
i915                  468651  3 
tg3                   152032  0 
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
drm_kms_helper         46978  1 i915
drm                   242038  4 i915,drm_kms_helper
ideapad_laptop         18234  0 
sparse_keymap          13890  1 ideapad_laptop
i2c_algo_bit           13423  1 i915
video                  19596  1 i915
wmi                    19256  1 mxm_wmi
mac_hid                13253  0 
acpi_handle_hack       12492  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp

```

and rfkill shows...

```
$ rfkill list all
0: ideapad_wlan: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: ideapad_bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
2: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
3: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
```

But in System Settings -> Bluetooth, it is disabled and I can't turn it on.

---

### Post by _sebastian_ on 2012-06-26
> **davidbilla said:**
> Hi,

Did you manage to solve this problem? I have a Lenovo Y570 running 12.04 and I have the same problem. Wireless works fine but not bluetooth.
...

But in System Settings -> Bluetooth, it is disabled and I can't turn it on.

Sadly not as there was not reply and I did not follow up enywhere else by now.

But I guess we have the same issue.

---

### Post by davidbilla on 2012-07-05
I updated ubuntu today and my bluetooth started working properly! I suggest you make sure you have the latest updates.

---

### Post by davidbilla on 2012-08-29
Well, the bluetooth is giving me problems again. It has gone back to the same old behaviour of staying disabled in Settings->Bluetooth even if the hardware switch is on and the wireless is working!

---

### Post by davidbilla on 2012-08-29
Hi, there's a workaround for this if you have a dual-boot system. Check this out.

[http://ubuntuforums.org/showthread.php?p=12203925#post12203925]("http://ubuntuforums.org/showthread.php?p=12203925#post12203925")

---

