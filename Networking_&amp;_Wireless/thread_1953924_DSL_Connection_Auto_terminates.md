---
title: "DSL Connection Auto terminates"
date: 2012-04-07
forum: Networking &amp; Wireless
---

### Post by john314 on 2012-04-07
I am using Xubuntu 11.10 with Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06) and using the latest updates.

I have a stable internet connection. 

The output from lsmod:
> Module                  Size  Used by
pppoe                  17875  2 
pppox                  13342  1 pppoe
rfcomm                 47946  4 
bnep                   18436  2 
bluetooth             166112  10 rfcomm,bnep
parport_pc             36962  0 
ppdev                  17113  0 
binfmt_misc            17540  1 
snd_hda_codec_hdmi     32040  1 
snd_hda_codec_idt      70553  1 
snd_hda_intel          33390  3 
snd_hda_codec         104931  3 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96714  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
joydev                 17693  0 
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
arc4                   12529  2 
uvcvideo               72711  0 
videodev               92992  1 uvcvideo
v4l2_compat_ioctl32    17083  1 videodev
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
rt2800pci              18715  0 
rt2800lib              54538  1 rt2800pci
snd                    68266  16 snd_hda_codec_hdmi,snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
fglrx                2928969  0 
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14578  1 rt2800pci
rt2x00lib              50365  3 rt2800pci,rt2800lib,rt2x00pci
i915                  571251  2 
mac80211              462046  3 rt2800lib,rt2x00pci,rt2x00lib
drm_kms_helper         42558  1 i915
cfg80211              199630  2 rt2x00lib,mac80211
drm                   236290  3 i915,drm_kms_helper
rts_pstor             445246  0 
soundcore              12680  1 snd
hp_accel               21880  0 
lis3lv02d              19888  1 hp_accel
input_polldev          13896  1 lis3lv02d
hp_wmi                 18092  0 
psmouse                73882  0 
serio_raw              13166  0 
sparse_keymap          13890  1 hp_wmi
i2c_algo_bit           13423  1 i915
eeprom_93cx6           12725  1 rt2800pci
video                  19412  1 i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41480  0 
wmi                    19256  1 hp_wmi
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
usb_storage            57901  0 
uas                    18027  0 
ahci                   26002  2 
xhci_hcd               82820  0 
libahci                26861  1 ahci
r8169                  52788  0 
The problem is i am synchronizing some sources from git and the sources are quite large. While synchronizing, my dsl connection gets auto terminated and i cant even connect back to my connection because after disconnection i cant even see my connection in the network manager applet. It only appears when i restart my machine and my connection is up again.

Any solution for this?

---

### Post by mörgæs on 2012-04-09
Moved to the network forum.

---

