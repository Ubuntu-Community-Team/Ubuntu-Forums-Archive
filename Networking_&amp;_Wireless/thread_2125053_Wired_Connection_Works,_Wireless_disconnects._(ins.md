---
title: "Wired Connection Works, Wireless disconnects. (insight needed)"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by Physics Eskimo on 2013-03-12
Hello there forum folk (ya'll seem to know about this more then I so i figured I'd ask for help)

I have a dual boot between windows and Ubuntu (12.04 LTS) and on windows, my wired and wireless connection works fantastic. on ubuntu my wired connection works great.
however on wireless, when booted in ubuntu my wireless will connect (after about 2-3 minutes of waiting while the internet thing pulses and asks me for the password 5 times) then after 5 minutes it will disconnect and my process 
starts again in a fantastic cycle of anger. 

From reading other posts, searching for a solution seems to be unique to each person, (maybe i just dont recognise the answer and its infront of me) 

Usually when other people ask they are quickly asked for certain outputs, so I'll do my best to show them right away,

I have gone to my connections and ensured that the password to the wireless and the ID are correct. it works right away if i switch from wirelss to wired. So im convinced its someting with this computer infront of me, Yelling at it, caressing it, crying, violently screaming, emotional breakdowns and massive caffine intakes have not yet solved the problem. I will try to convince my computer to connect by telling it I would hate it if it actually wirelessly connected... (that might work....right?)


1) 
```

**lspci -nnk | grep -iA2 net**

00:19.0 Ethernet controller [0200]: Intel Corporation 82579LM Gigabit Network Connection [8086:1502] (rev 04)
    Subsystem: Lenovo Device [17aa:21ce]
    Kernel driver in use: e1000e
--
03:00.0 Network controller [0280]: Intel Corporation Centrino Advanced-N 6205 [8086:0085] (rev 34)
    Subsystem: Intel Corporation Centrino Advanced-N 6205 AGN [8086:1311]
    Kernel driver in use: iwlwifi


```

```

**lsmod**
Module                  Size  Used by
snd_hda_codec_conexant    62358  1 
joydev                 17693  0 
bnep                   18281  2 
parport_pc             32866  0 
rfcomm                 47604  0 
ppdev                  17113  0 
bluetooth             180153  10 bnep,rfcomm
lp                     17799  0 
parport                46562  3 parport_pc,ppdev,lp
arc4                   12529  2 
snd_hda_intel          33773  3 
snd_hda_codec         127706  2 snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              17764  1 snd_hda_codec
snd_pcm                97275  2 snd_hda_intel,snd_hda_codec
thinkpad_acpi          81819  0 
uvcvideo               72627  0 
videodev               98259  1 uvcvideo
nvram                  14413  1 thinkpad_acpi
v4l2_compat_ioctl32    17128  1 videodev
tpm_tis                18804  0 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
iwlwifi               401140  0 
mac80211              506862  1 iwlwifi
snd_seq                61929  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
psmouse                97485  0 
mac_hid                13253  0 
snd                    79041  16 snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,thinkpad_acpi,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
nouveau               775039  0 
i915                  477611  3 
cfg80211              205774  2 iwlwifi,mac80211
serio_raw              13211  0 
ttm                    76949  1 nouveau
drm_kms_helper         46978  2 nouveau,i915
drm                   241971  6 nouveau,i915,ttm,drm_kms_helper
i2c_algo_bit           13423  2 nouveau,i915
mxm_wmi                13021  1 nouveau
wmi                    19256  1 mxm_wmi
soundcore              15091  1 snd
video                  19651  2 nouveau,i915
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
mei                    41616  0 
firewire_ohci          41000  0 
sdhci_pci              18826  0 
sdhci                  33205  1 sdhci_pci
firewire_core          63600  1 firewire_ohci
crc_itu_t              12707  1 firewire_core
e1000e                156873  0 

```

```

**rfkill list**

0: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


```

*** Note I am on wired right now ***

---

### Post by Hadaka on 2013-03-12
Hi, give this a try
```
sudo modprobe -rfv iwlwifi
sudo modprobe iwlwifi 11n_disable=1
rfkill list all
```
thanks

---

### Post by Physics Eskimo on 2013-03-12
Would you like to See the outputs?

```

rmmod /lib/modules/3.2.0-38-generic/kernel/drivers/net/wireless/iwlwifi/iwlwifi.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/net/mac80211/mac80211.ko
rmmod /lib/modules/3.2.0-38-generic/kernel/net/wireless/cfg80211.ko

```

Second produces no terminal output

```

1: phy0: Wireless LAN
    Soft blocked: yes
    Hard blocked: yes


``` 

^^ Hey hey the 0 changed to a 1, i'll try wireless now:

-> Switching to wireless it connected in ~ 5 seconds, Much faster. I'll post up again if the Issue persists. Thank you good sir.
I'll tag this as Solved untill anything happens.

May I ask how you knew what to do? And why you said to disable =1?

---

### Post by Hadaka on 2013-03-12
Hi, glad its working,
when you said "(after about 2-3 minutes of waiting while the internet thing pulses and asks me for the password 5 times)"
thats usually an indication the N part of the wireless b/g/n is flakey.
so..disabeled it with the  "1"
have fun !

---

