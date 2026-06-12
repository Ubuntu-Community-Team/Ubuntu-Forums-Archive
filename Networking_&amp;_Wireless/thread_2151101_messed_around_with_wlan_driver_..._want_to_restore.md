---
title: "messed around with wlan driver ... want to restore the &quot;original&quot; ones"
date: 2013-06-03
forum: Networking &amp; Wireless
---

### Post by hutzlibu on 2013-06-03
Hi folks,

I messed around with my wlan drivers on my HP 635 Laptop, to maybe enable AP, but that failed ... and now the wlan doesen't work at all anymore.
Unfortunately it's been a while, since i played around with it, so I can't remember, what I did exactly   ... so I'd just like to reset all the settings and restore the original drivers to make it work again.
(they worked without problems out of the box)

Is there a easy way to do this?

Thanks in advance

---

### Post by Hadaka on 2013-06-03
Hi, please post the output of..
```
lspci -nnk | grep -iA3 net
lsmod
rfkill list all
uname -a
lsb_release -a
```
thanks.

---

### Post by hutzlibu on 2013-06-03
Hi Hadaka, 
thx for replay

Output:


lspci -nnk | grep -iA3 

net06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05)
    Subsystem: Hewlett-Packard Company Device [103c:3577]
    Kernel driver in use: r8169
07:00.0 Network controller [0280]: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) [168c:002b] (rev 01)
    Subsystem: Hewlett-Packard Company Device [103c:1461]
    Kernel driver in use: ath9k

#################################
lsmod

Module Size Used by
parport_pc 28152 0 
ppdev 17073 0 
rfcomm 42641 0 
bnep 18036 2 
snd_hda_codec_realtek 78399 1 
snd_hda_codec_hdmi 36913 1 
joydev 17377 0 
hp_wmi 18048 0 
sparse_keymap 13890 1 hp_wmi
kvm 443165 0 
uvcvideo 80847 0 
videobuf2_vmalloc 13056 1 uvcvideo
videobuf2_memops 13202 1 videobuf2_vmalloc
videobuf2_core 40513 1 uvcvideo
videodev 129260 2 uvcvideo,videobuf2_core
microcode 22881 0 
snd_hda_intel 39619 5 
snd_hda_codec 136453 3 snd_hda_codec_realtek,snd_hda_codec_hdmi,snd_hda_intel
snd_hwdep 13602 1 snd_hda_codec
snd_seq_midi 13324 0 
snd_seq_midi_event 14899 1 snd_seq_midi
arc4 12615 2 
snd_rawmidi 30180 1 snd_seq_midi
ath9k 149924 0 
ath9k_common 14055 1 ath9k
snd_pcm 97451 3 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel
radeon 937749 3 
ath9k_hw 413680 2 ath9k_common,ath9k
snd_page_alloc 18710 2 snd_pcm,snd_hda_intel
ath 23827 3 ath9k_common,ath9k,ath9k_hw
ttm 83187 1 radeon
snd_seq 61554 2 snd_seq_midi_event,snd_seq_midi
drm_kms_helper 49394 1 radeon
mac80211 606457 1 ath9k
snd_seq_device 14497 3 snd_seq,snd_rawmidi,snd_seq_midi
ath3k 12918 0 
video 19390 0 
snd_timer 29425 2 snd_pcm,snd_seq
drm 286313 5 ttm,drm_kms_helper,radeon
wmi 19070 1 hp_wmi
btusb 22474 0 
rtsx_pci_ms 13011 0 
bluetooth 228619 13 bnep,ath3k,btusb,rfcomm
k10temp 13126 0 
mac_hid 13205 0 
memstick 16554 1 rtsx_pci_ms
psmouse 95870 0 
serio_raw 13215 0 
sp5100_tco 13735 0 
i2c_piix4 13266 0 
cfg80211 510937 3 ath,ath9k,mac80211
snd 68876 20 snd_hda_codec_realtek,snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec,snd_hda_intel,snd_seq_device
i2c_algo_bit 13413 1 radeon
soundcore 12680 1 snd
lp 17759 0 
parport 46345 3 lp,ppdev,parport_pc
rtsx_pci_sdmmc 17475 0 
r8169 67446 0 
rtsx_pci 33355 2 rtsx_pci_ms,rtsx_pci_sdmmc
ahci 25731 2 
libahci 31364 1 ahci

##############################################################################
rfkill list all0: 
phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
1: hp-wifi: Wireless LAN
    Soft blocked: yes
    Hard blocked: no
2: hp-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
3: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

############################################################################
uname -a
58 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

####################################################
lsb_release -a
Distributor ID:    Ubuntu
Description:    Ubuntu 13.04
Release:    13.04
Codename:    raring



No LSB modules are available.

---

### Post by hutzlibu on 2013-06-03
ah btw ...  pressing the hardware button isn't doing anything either

---

### Post by Hadaka on 2013-06-03
Hi, looks like the hard block on the wifi
is a soft or hardware switch, Is the "Enable Network" in network mgr. checked?
Give this a try also..
```
rfkill unblock all
```
then press  Fn/F12 one time
then post again
```
rfkill list all
```
thanks.

---

### Post by praseodym on 2013-06-03
If Hadakas tip doesnt work, try to reset the BIOS to default settings.

---

### Post by hutzlibu on 2013-06-03
It is not checked, but everytime i check it ... nothing happens except that afterwards it becomes checked for some seconds and then its greyed out.
Enabling wlan in the network menue doesn't work either, and unfortunately your commands didn't achieve resaults.

edit:
trying the bios default now

---

### Post by hutzlibu on 2013-06-03
Somehow ... the Bios reset did the job ...
Thanks.
Even though I don't quite understand why, but nevermind :)

---

### Post by Hadaka on 2013-06-03
Glad you got it going !
@praseodym...thanks !

---

