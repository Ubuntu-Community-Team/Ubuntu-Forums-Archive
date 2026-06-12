---
title: "NetworkManager issue on startup"
date: 2013-07-05
forum: Networking &amp; Wireless
---

### Post by Apolyonn on 2013-07-05
Hey all,

I'm running the minimal install of Lubuntu.  Given that it came with the bare-minimum, I had to do some research on which network manager to use (specifically, which one Lubuntu Desktop uses by default).  I installed network-manager and it's more-or-less working well.  However, at startup, my wireless driver doesn't boot; when I left-click on nm-applet, it says "NetworkManager is not enabled" in gray text.  I can get it up manually by using the following:
```

ifconfig wlan0 up
iwlist wlan0 scan
iwconfig wlan0 essid "SSID" key "PASSPHRASE"

```

It takes a bit to initialize, but so far that's the only way I know how.  

Is there an easier way around this?  
My wireless card is Broadcom 4313.  I had this issue with both brcmsmac and wl drivers

Thanks.

---

### Post by wildmanne39 on 2013-07-05
Hi, please post the output of:
```
lspci -nnk | grep -iA2 net
lsmod
```
Thanks

---

### Post by Apolyonn on 2013-07-05
```

nergal@Aeon:~$ lspci -nnk | grep -iA2 net
06:00.0 Ethernet controller [0200]: Qualcomm Atheros AR8152 v2.0 Fast Ethernet [1969:2062] (rev c1)
    Subsystem: Acer Incorporated [ALI] Device [1025:0598]
    Kernel driver in use: atl1c
07:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Broadcom Corporation Device [14e4:0510]
    Kernel driver in use: bcma-pci-bridge

```

```

nergal@Aeon:~$ lsmod
Module                  Size  Used by
ums_realtek            17669  0 
usb_storage            47684  1 ums_realtek
vesafb                 13500  1 
arc4                   12543  2 
brcmsmac              521468  0 
cordic                 12518  1 brcmsmac
brcmutil               14355  1 brcmsmac
joydev                 17097  0 
mac80211              526519  1 brcmsmac
acer_wmi               27592  0 
cfg80211              436177  2 brcmsmac,mac80211
sparse_keymap          13658  1 acer_wmi
uvcvideo               71279  0 
snd_hda_codec_conexant    52256  1 
videobuf2_vmalloc      12920  1 uvcvideo
kvm_amd                50336  0 
videobuf2_memops       13042  1 videobuf2_vmalloc
bnep                   17669  2 
snd_hda_codec_hdmi     36185  1 
parport_pc             27504  0 
ppdev                  12817  0 
videobuf2_core         39161  1 uvcvideo
kvm                   376505  1 kvm_amd
rfcomm                 37420  0 
bluetooth             202069  10 bnep,rfcomm
snd_hda_intel          38307  0 
videodev               95806  2 uvcvideo,videobuf2_core
microcode              18286  0 
snd_hda_codec         117580  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_hwdep              13272  1 snd_hda_codec
snd_pcm                80890  3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
snd_page_alloc         14230  2 snd_pcm,snd_hda_intel
snd_seq_midi           13132  0 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_rawmidi            25114  1 snd_seq_midi
fglrx                4807481  89 
sp5100_tco             13447  0 
snd_seq                51280  2 snd_seq_midi_event,snd_seq_midi
psmouse                81038  0 
serio_raw              13031  0 
k10temp                12958  0 
i2c_piix4              13066  0 
bcma                   39645  1 brcmsmac
snd_seq_device         14137  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              24411  2 snd_pcm,snd_seq
snd                    56485  10 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              12600  1 snd
wmi                    18590  1 acer_wmi
video                  18894  1 acer_wmi
mac_hid                13037  0 
lp                     13299  0 
parport                40753  3 lp,ppdev,parport_pc
atl1c                  36175  0 
ahci                   25507  3 
libahci                26108  1 ahci

```

---

### Post by wildmanne39 on 2013-07-05
This should do it.
```
sudo su 
echo brcmsmac >> /etc/modules 
exit
```
Thanks

---

