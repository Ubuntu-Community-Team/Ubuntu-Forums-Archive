---
title: "Problems with wireless"
date: 2013-03-07
forum: Networking &amp; Wireless
---

### Post by OSUTIN on 2013-03-07
Hey everyone, I just installed Ubuntu on my laptop (again after quite a while), and am experiencing difficulties with my wireless.  My laptop is an HP G62 Notebook PC, and has a physical hardware button on the keyboard to turn wireless on and off.  When off, it is orange, when on, it is white.  When I first installed Ubuntu, it was orange, but I could turn it on.  But it didn't pick up any wireless networks.  Now, I am unable to turn it on, and the wireless option in the network menu has completely dissapeared.  Before deciding to make an account, I tried a variety of things I found, but nothing seemed to work.  At this point in time, any help would be appreciated.  Thanks in advance!  And just tell me whatever terminal commands you want me to use, in whatever order, but do note, as it has been a long time since I've used Ubuntu, I'm not entirely familiar with the terminal anymore (not that I was ever really familiar with it, in comparison to people who use Ubuntu regularly).

---

### Post by OSUTIN on 2013-03-08
Bump.  I know I'm ever so slightly vague, but please help.  I'm noot a total noob/knob, like my original post may have made me out to be...

---

### Post by praseodym on 2013-03-08
Please show the outputs of:
```

lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
```

---

### Post by OSUTIN on 2013-03-08
the first one gave the following:
```
02:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:145c]
    Kernel driver in use: bcma-pci-bridge
--
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
    Subsystem: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136]
    Kernel driver in use: r8169
    Kernel modules: r8169


```

then

```
Module                  Size  Used by
ums_realtek            17950  0 
rndis_host             13856  0 
cdc_ether              13495  1 rndis_host
usbnet                 26160  2 rndis_host,cdc_ether
snd_hda_codec_hdmi     32049  1 
joydev                 17458  0 
kvm_amd                55605  0 
kvm                   414071  1 kvm_amd
parport_pc             32689  0 
ppdev                  17074  0 
bnep                   18141  2 
rfcomm                 46620  0 
bluetooth             209249  10 bnep,rfcomm
binfmt_misc            17501  1 
microcode              22804  0 
snd_hda_codec_realtek    78147  1 
snd_seq_midi           13325  0 
k10temp                13127  0 
snd_rawmidi            30513  1 snd_seq_midi
psmouse                95595  0 
serio_raw              13216  0 
snd_seq_midi_event     14900  1 snd_seq_midi
snd_seq                61555  2 snd_seq_midi,snd_seq_midi_event
snd_hda_intel          33492  4 
snd_hda_codec         134213  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              17699  1 snd_hda_codec
edac_core              52452  0 
edac_mce_amd           23304  0 
snd_pcm                96668  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
snd_seq_device         14498  3 snd_seq_midi,snd_rawmidi,snd_seq
sp5100_tco             13698  0 
i2c_piix4              13168  0 
snd_timer              29426  2 snd_seq,snd_pcm
radeon                895730  3 
snd                    78921  18 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_rawmidi,snd_seq,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_seq_device,snd_timer
ttm                    83596  1 radeon
drm_kms_helper         49113  1 radeon
uvcvideo               76750  0 
videobuf2_core         32852  1 uvcvideo
video                  19391  0 
videodev              120310  2 uvcvideo,videobuf2_core
drm                   288721  5 radeon,ttm,drm_kms_helper
videobuf2_vmalloc      12861  1 uvcvideo
videobuf2_memops       13405  1 videobuf2_vmalloc
i2c_algo_bit           13414  1 radeon
soundcore              15048  1 snd
snd_page_alloc         18485  2 snd_hda_intel,snd_pcm
wmi                    19071  0 
cdc_acm                26899  0 
b43                   369857  0 
mac80211              540032  1 b43
mac_hid                13206  0 
cfg80211              206797  2 b43,mac80211
bcma                   35657  1 b43
ssb                    52037  1 b43
shpchp                 37109  0 
lp                     17760  0 
parport                46346  3 parport_pc,ppdev,lp
hid_logitech_dj        18605  0 
usbhid                 46987  1 hid_logitech_dj
hid                   100411  2 hid_logitech_dj,usbhid
usb_storage            48834  1 ums_realtek
r8169                  61651  0 
ahci                   25721  2 
libahci                31192  1 ahci
```

then

```
usb0      no wireless extensions.

eth0      no wireless extensions.

lo        no wireless extensions.


```

the last one returned absolutely nothing.

---

### Post by ing.tani on 2013-03-08
Try** ```
sudo rfkill list**
```

Press Enter and insert your password.

Submit the output.

BTW have you installed any network manager (nm-appled, wicd....)?

---

### Post by praseodym on 2013-03-08
Install the package "b43-fwcutter"

---

### Post by OSUTIN on 2013-03-09
Even with Sudo it returns nothing.  And I don't have any network managers that I know of.

---

### Post by OSUTIN on 2013-03-09
installing

---

### Post by OSUTIN on 2013-03-09
installed

---

### Post by OSUTIN on 2013-03-09
hello?  I still need help.  Nothing has been resolved yet.

---

### Post by praseodym on 2013-03-10
Please show
```

uname -a
egrep 'bcma|brcm' /etc/modprobe.d/*
```

---

### Post by OSUTIN on 2013-03-11
here is the first one
```
Linux austin-HP-G62-Notebook-PC 3.5.0-26-generic #40-Ubuntu SMP Tue Feb 26 19:57:24 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux


```

and the second

```
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcm80211
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmfmac
/etc/modprobe.d/blacklist-bcm43.conf:blacklist brcmsmac
/etc/modprobe.d/blacklist-bcm43.conf:blacklist bcma
/etc/modprobe.d/broadcom-sta-common.conf:blacklist brcm80211
/etc/modprobe.d/broadcom-sta-common.conf:blacklist brcmsmac
/etc/modprobe.d/broadcom-sta-dkms.conf:blacklist brcm80211
/etc/modprobe.d/broadcom-sta-dkms.conf:blacklist brcmsmac
```

And also, I'd like to appologize if I sounded ungratefull in my last post.  It's just that this is annoying, and the last time I had Ubuntu installed on my laptop (which was before my hard drive commited suicide/was murdered), it worked completely fine.  So I am just having trouble understanding what could be so different.

---

### Post by OSUTIN on 2013-03-12
hello?

---

### Post by OSUTIN on 2013-03-12
. . . Wow am I impatient.

---

### Post by OSUTIN on 2013-03-13
Gaaa!!!  Maddening!

---

### Post by praseodym on 2013-03-13
Remove these files:
```

sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo rm /etc/modprobe.d/broadcom-sta-common.conf
sudo rm /etc/modprobe.d/broadcom-sta-dkms.conf
```
Reboot.

---

### Post by OSUTIN on 2013-03-13
okies, so now I have the wireless thing in the menu again, and it says disabled by a hardware switch again.  That is progress. Thank yous.  Now hopefully we can get it working completely.

---

### Post by OSUTIN on 2013-03-13
WOOT!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  IT WORKS!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!  My light does not turn white anymore, but it WORKS!!!!!!!!!!!!!!!  YAAAAYYYYYYY!!!!!!!!!!!!!!!!!!!!!!!!!  Thank you so much!

---

