---
title: "AR9285 stopped working altogether after 12.04 Upgrade"
date: 2012-12-05
forum: Networking &amp; Wireless
---

### Post by Armence on 2012-12-05
Hello,

I upgraded to 12.04 yesterday at which point my wireless stopped working entirely. When I left-click on the networking widget, the menu does not even offer the "Enable Wireless Networking" option anymore.

I have made sure that the hardware is turned on.

I have appended: "blacklist acer_wmi" to /etc/modprobe.d/blacklist.conf

Nothing worked. I need help.

```
$ uname -a
Linux armence 3.2.0-34-generic #53-Ubuntu SMP Thu Nov 15 10:49:02 UTC 2012 i686 i686 i386 GNU/Linux
```

```
$ lspci -nn | grep Network
02:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
```

```
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.
```

```
$ rfkill list all
```
Not a typo. Nothing was displayed.

```
$ lsmod
Module                  Size  Used by
dm_crypt               22528  0 
joydev                 17393  0 
snd_hda_codec_via      46138  1 
parport_pc             32114  0 
ppdev                  12849  0 
rfcomm                 38139  0 
bnep                   17830  2 
bluetooth             158438  10 rfcomm,bnep
snd_hda_intel          32765  4 
snd_hda_codec         109562  2 snd_hda_codec_via,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80845  3 snd_hda_intel,snd_hda_codec
psmouse                96684  0 
binfmt_misc            17292  1 
serio_raw              13027  0 
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51567  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
uvcvideo               67203  0 
videodev               86588  1 uvcvideo
snd                    62064  16 snd_hda_codec_via,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore              14635  1 snd
snd_page_alloc         14115  2 snd_hda_intel,snd_pcm
mac_hid                13077  0 
asus_laptop            23693  0 
sparse_keymap          13658  1 asus_laptop
input_polldev          13648  1 asus_laptop
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
atl1e                  32872  0 
i915                  419126  4 
drm_kms_helper         45466  1 i915
drm                   197599  5 i915,drm_kms_helper
i2c_algo_bit           13199  1 i915
video                  19068  1 i915
```

---

