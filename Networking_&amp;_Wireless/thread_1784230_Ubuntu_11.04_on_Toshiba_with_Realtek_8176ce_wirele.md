---
title: "Ubuntu 11.04 on Toshiba with Realtek 8176ce wireless freezes my laptop"
date: 2011-06-16
forum: Networking &amp; Wireless
---

### Post by Atirag on 2011-06-16
Hello everyone, I created a new topic since maybe the other I wrote in is not specifically for this issue

I read through this topic ([http://ubuntuforums.org/showthread.php?t=1770202](http://ubuntuforums.org/showthread.php?t=1770202)) but no solution appears to relate with my issue specifically.

I have a Toshiba Satellite C655D. I have no problem with my wired  connection but whenever I try using my wireless connection my computer  freezes. Sometimes if I use my wired connection before using the  wireless one then my wireless connection works fine. Whenever I try  booting without having the network cable plugged then my computer hangs  at boot, but if I plug the cable then it boots without a problem. So I  figure the problem is the wireless driver. I had similar but not  entirely the same issues with Ubuntu 10.10 so I don't want to go back  and I'll rather fix the issues with 11.04. I've been using the driver  that installs with the kernel, in Ubuntu 10.10 I used the driver from  the Realtek website but I had similar problems. So a little info.

This is the output of 

```
modinfo rtl8192ce
``````
filename:        /lib/modules/2.6.38-8-generic-pae/kernel/drivers/net/wireless/rtlwifi/rtl8192ce/rtl8192ce.ko
firmware:       rtlwifi/rtl8192cfw.bin
description:    Realtek 8192C/8188C 802.11n PCI wireless
license:        GPL
author:         Larry Finger    <Larry.Finger@lwfinger.net>
author:         Realtek WlanFAE    <wlanfae@realtek.com>
author:         lizhaoming    <chaoming_li@realsil.com.cn>
srcversion:     7416041392B86CCB7B54065
alias:          pci:v000010ECd00008176sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008177sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008178sv*sd*bc*sc*i*
alias:          pci:v000010ECd00008191sv*sd*bc*sc*i*
depends:        rtlwifi,mac80211
vermagic:       2.6.38-8-generic-pae SMP mod_unload modversions 686 
parm:           swenc:using hardware crypto (default 0 [hardware])
 (bool)
```and this is the output of lsmod

```
Module                  Size  Used by
parport_pc             32111  0 
ppdev                  12849  0 
vesafb                 13449  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24140  2 
arc4                   12473  2 
snd_hda_codec          90901  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13274  1 snd_hda_codec
snd_pcm                80244  2 snd_hda_intel,snd_hda_codec
rtl8192ce             120897  0 
snd_seq_midi           13132  0 
snd_rawmidi            25269  1 snd_seq_midi
rtlwifi                78961  1 rtl8192ce
snd_seq_midi_event     14475  1 snd_seq_midi
mac80211              257001  2 rtl8192ce,rtlwifi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
binfmt_misc            13213  1 
snd_timer              28659  2 snd_pcm,snd_seq
uvcvideo               66851  0 
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
fglrx                2434640  89 
cfg80211              156212  2 rtlwifi,mac80211
snd                    55295  13  snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
videodev               75143  1 uvcvideo
psmouse                59039  0 
shpchp                 32345  0 
serio_raw              12990  0 
sp5100_tco             13456  0 
k10temp                12951  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_piix4              13095  0 
sparse_keymap          13666  0 
video                  18951  0 
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
ahci                   21591  2 
atl1c                  36237  0 
usb_storage            43946  0 
libahci                25548  1 ahci
uas                    17676  0 
```as you can see I have only one wireless driver installed.

Can someone please help me with this? I've been having this issue since probably a week now and I'm getting kind of desperate.

Should I install another kernel? or maybe try with another driver? is it a firmware issue? anybody having similar issues?

 Any help will be appreciated.

Thanks in advance

---

