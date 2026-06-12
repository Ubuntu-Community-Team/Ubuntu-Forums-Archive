---
title: "Wired Internet breaks in out and out. 12.04"
date: 2013-03-12
forum: Networking &amp; Wireless
---

### Post by avoliva on 2013-03-12
I connect directly through my modem. I dual boot and on Windows 7 the internet works all the time, yet when I jump on Ubuntu the internet can go down randomly for about 5 minutes. It seems nothign does this. I can be coding and try to search on the internet and all the sudden it won't connect. Then I refresh a couple times and it works. Sometimes it can take up to five minutes. It's really annoying. Any help on this issue?

---

### Post by varunendra on 2013-03-12
Hi,

Please open a terminal (Ctrl+Alt+T), enter and post outputs of these commands -
```
uname -mr
lspci -nnk | grep -iA2 net
lsmod
```

While posting the outputs, please wrap them within 'Code' tags (follow the example link in my signature to see how).

---

### Post by avoliva on 2013-03-12
uname -mr : 3.2.0-38-generic-pae i686


lspci -nnk | grep -iA2
```
net00:0f.0 Ethernet controller [0200]: NVIDIA Corporation MCP73 Ethernet [10de:07dc] (rev a2)
    Subsystem: Hewlett-Packard Company Device [103c:2a64]
    Kernel driver in use: forcedeth

lsmod:

Module                  Size  Used by
pci_stub               12550  1 
vboxpci                22911  0 
vboxnetadp             13328  0 
vboxnetflt             27240  0 
vboxdrv               252188  3 vboxpci,vboxnetadp,vboxnetflt
snd_hda_codec_realtek   174313  1 
joydev                 17393  0 
usbhid                 41937  0 
hid                    77428  1 usbhid
snd_hda_intel          32765  3 
snd_hda_codec         109562  2 snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13276  1 snd_hda_codec
snd_pcm                80916  2 snd_hda_intel,snd_hda_codec
snd_seq_midi           13132  0 
snd_rawmidi            25424  1 snd_seq_midi
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51592  2 snd_seq_midi,snd_seq_midi_event
snd_timer              28931  2 snd_pcm,snd_seq
snd_seq_device         14172  3 snd_seq_midi,snd_rawmidi,snd_seq
nouveau               712674  2 
rfcomm                 38139  0 
snd                    62218  15 snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
bnep                   17830  2 
parport_pc             32114  0 
bluetooth             158479  10 rfcomm,bnep
ppdev                  12849  0 
ttm                    65344  1 nouveau
drm_kms_helper         45466  1 nouveau
drm                   197641  4 nouveau,ttm,drm_kms_helper
i2c_algo_bit           13199  1 nouveau
soundcore              14635  1 snd
mxm_wmi                12893  1 nouveau
video                  19115  1 nouveau
serio_raw              13027  0 
snd_page_alloc         14108  2 snd_hda_intel,snd_pcm
wmi                    18744  1 mxm_wmi
binfmt_misc            17292  1 
mac_hid                13077  0 
i2c_nforce2            12906  0 
lp                     17455  0 
parport                40930  3 parport_pc,ppdev,lp
firewire_ohci          40172  0 
firewire_core          56940  1 firewire_ohci
usb_storage            39646  0 
crc_itu_t              12627  1 firewire_core
forcedeth              58096  0 
pata_amd               13750  0 

```


BTW I can acces this website but right now when I'm trying to google or visit ANY other website it won't load . <snip>

---

### Post by varunendra on 2013-03-12
Unfortunately, I don't have any experience with the card you have or the driver it uses. But let us see -
```
ifconfig
nm-tool
ping -c4 google.com
```

---

