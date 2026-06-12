---
title: "Latitude D531 - restricted drivers not working?"
date: 2011-11-14
forum: Networking &amp; Wireless
---

### Post by epic93 on 2011-11-14
I have a Dell Latitude D531, and it's having an... unusual problem.

After I installed Ubuntu 11.10, I tried to use my Wifi at home. In the network applet at the top of the screen it said "Device not ready: (firmware missing)"

So I used the Restricted Drivers application to install the Broadcom STA Wireless Drivers, and reboot. When I boot up again, it says Device Not Ready:(Disabled by Hardware Switch)

I try to turn on the Wifi with the hardware switch, but it doesn't seem to be turning on. I know the switch is working and the wireless card is working because it worked with Windows a few days ago.

What is going on here? Do I need different drivers? 

Also, if it means anything, it used to work in Ubuntu 10.10.

---

### Post by BillyBoa on 2011-11-14
Go here:

[http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092)

---

### Post by epic93 on 2011-11-14
I tried that, and it's still giving me the (firmware missing) message.

---

### Post by BillyBoa on 2011-11-14
I assume that you have connected your computer through wire?

---

### Post by bkratz on 2011-11-14
> **epic93 said:**
> I tried that, and it's still giving me the (firmware missing) message.

Can you post the output of 


```
rfkill list all

```

and

```
lsmod
```



that is LSMOD in lowercase.

---

### Post by epic93 on 2011-11-14
```
rfkill list all---

0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no


lsmod---

Module                  Size  Used by
nls_utf8               12557  1 
isofs                  40253  1 
parport_pc             36962  0 
ppdev                  17113  0 
bnep                   18436  2 
rfcomm                 47946  0 
bluetooth             166112  10 bnep,rfcomm
joydev                 17693  0 
dell_wmi               12681  0 
sparse_keymap          13890  1 dell_wmi
snd_hda_codec_idt      70553  1 
dell_laptop            13831  0 
snd_hda_intel          33390  2 
dcdbas                 14490  1 dell_laptop
snd_hda_codec         104802  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                96755  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13324  0 
snd_rawmidi            30547  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
pcmcia                 49378  0 
snd_timer              29991  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                73882  0 
serio_raw              13166  0 
yenta_socket           28084  0 
pcmcia_rsrc            18430  1 yenta_socket
snd                    68266  13 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
pcmcia_core            22614  3 pcmcia,yenta_socket,pcmcia_rsrc
edac_core              53746  0 
edac_mce_amd           23709  0 
k8temp                 13057  0 
soundcore              12680  1 snd
sp5100_tco             13791  0 
i2c_piix4              13301  0 
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
radeon               1015995  3 
ttm                    76805  1 radeon
arc4                   12529  2 
drm_kms_helper         42558  1 radeon
drm                   236330  5 radeon,ttm,drm_kms_helper
b43                   341198  0 
mac80211              310872  1 b43
cfg80211              199587  2 b43,mac80211
i2c_algo_bit           13423  1 radeon
wmi                    19256  1 dell_wmi
binfmt_misc            17540  1 
video                  19412  0 
shpchp                 37345  0 
ndiswrapper           254773  0 
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
firewire_ohci          40722  0 
firewire_core          63626  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
pata_atiixp            13164  1 
ahci                   26002  2 
tg3                   147729  0 
libahci                26861  1 ahci
ssb                    52752  1 b43

```

---

### Post by bkratz on 2011-11-14
Can you do a

lspci -nnk | grep -iA2 net

So we can all see what card we are working with? Again that is LSPCI xxx in lowercase. Oh and I see you have b43 and ndiswrapper modules loaded, we may have to clean up some of those.

---

