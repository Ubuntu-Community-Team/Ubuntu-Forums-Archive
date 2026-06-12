---
title: "Wireless Fails after Upgrade to 12.04"
date: 2012-05-28
forum: Networking &amp; Wireless
---

### Post by Leed on 2012-05-28
Hi, 

I'm a little stuck in the typical "I don't want to backup all my data, reinstall and repurchase all my Software and reconfigure my whole System" dilema...

After the Upgrade to 12.04 all seemed fine, I even figured out you can bypass the update Stall by simply opening the details window and following the dialoge inside. 

But upon using the new System, I noticed that my Wi-Fi connection stops working after a short time of usage. You don't see an error, it just doesn't load any data/webpage etc. 
Reconnecting to the Network temporarly solves the problem, but it occurs again after less than 1-2 minutes. 

Is there maybe a way to reset the network drivers/settings?

---

### Post by praseodym on 2012-05-29
Please show the outputs of:

```
lspci -nnk | grep -iA2 net
uname -a
iwconfig
rfkill list
lsmod
```
I recommend using WPA2-AES encryption, if possible.

---

### Post by Leed on 2012-05-30
I now also tried an clean installation from CD, same problem, it seems that Pangolin doesn't want to work for me. 

You're my last hope ;) 
I've got my Oncelot Disc ready, if you can't find anything I'll go back to that version. Not exactly what I want, but I can't work on this machine if the connection keeps dropping out. 

```
lspci -nnk | grep -iA2 net
04:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
	Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
	Kernel driver in use: r8169
--
05:02.0 Network controller [0280]: Ralink corp. RT2800 802.11n PCI [1814:0601]
	Subsystem: Edimax Computer Co. Device [1432:7728]
	Kernel driver in use: rt2800pci

```
```
uname -a
Linux leed-home 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux

```
```
iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"mongido2"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:1F:1F:8F:D1:CC   
          Bit Rate=130 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=58/70  Signal level=-52 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:7   Missed beacon:0

eth0      no wireless extensions.

```
```
rfkill list
0: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no

```
```
lsmod
Module                  Size  Used by
rfcomm                 47604  0 
bnep                   18281  2 
bluetooth             180104  10 rfcomm,bnep
snd_hda_codec_hdmi     32474  1 
joydev                 17693  0 
snd_hda_codec_realtek   223867  1 
snd_hda_intel          33773  5 
snd_hda_codec         127706  3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel
snd_hwdep              13668  1 snd_hda_codec
snd_pcm                97188  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
arc4                   12529  2 
snd_seq_midi           13324  0 
snd_rawmidi            30748  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
rt2800pci              18715  0 
rt2800lib              58925  1 rt2800pci
snd_seq                61896  2 snd_seq_midi,snd_seq_midi_event
crc_ccitt              12667  1 rt2800lib
rt2x00pci              14577  1 rt2800pci
rt2x00lib              55301  3 rt2800pci,rt2800lib,rt2x00pci
mac80211              506816  3 rt2800lib,rt2x00pci,rt2x00lib
snd_timer              29990  2 snd_pcm,snd_seq
snd_seq_device         14540  3 snd_seq_midi,snd_rawmidi,snd_seq
ppdev                  17113  0 
parport_pc             32866  1 
radeon                804372  3 
cfg80211              205544  2 rt2x00lib,mac80211
eeprom_93cx6           12725  1 rt2800pci
i7core_edac            28102  0 
ttm                    76949  1 radeon
serio_raw              13211  0 
snd                    78855  20 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
edac_core              53746  3 i7core_edac
drm_kms_helper         46978  1 radeon
mac_hid                13253  0 
drm                   242038  5 radeon,ttm,drm_kms_helper
i2c_algo_bit           13423  1 radeon
soundcore              15091  1 snd
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
lp                     17799  0 
parport                46562  3 ppdev,parport_pc,lp
hid_logitech           26520  0 
ff_memless             13097  1 hid_logitech
usbhid                 47199  1 hid_logitech
hid                    99559  2 hid_logitech,usbhid
r8169                  62099  0 
pata_jmicron           12747  0 
usb_storage            49198  0 

```

---

### Post by carl4926 on 2012-05-30
Looks fine to me, same device as mine.
Try deleting any connections you have setup in networkmanager and then try making a new connection to your access point

---

### Post by praseodym on 2012-05-30
Try to update the system via cable connection, kernel -24 is the latest.

---

### Post by Leed on 2012-05-31
Managed to get the update, by wireless, simply reconnecting every time the connection stopped working...

The -24 Kernel actually seems better, I managed to transfer files over my network that failed every time before. Still I did have an interrupt this morning, hoping it won't be more. 

I already hate myself for trashing all my settings by doing the clean install from cd :(   Maybe next time I should wait 1-2 Month before doing the upgrade.

---

### Post by carl4926 on 2012-05-31
There is no need trash settings with new installs. I only do new installs and it takes me a couple of hours tops to put all my files and settings/configs back in place.

It's worth remembering though, that some things do change and it may be necessary to redo certain settings.

Always keep a backup of what is really important to you, particularly things you might find difficult to setup again from scratch or are time consuming.

---

### Post by Leed on 2012-05-31
Luckily my Data is always on a seperate partition, except for the stuff in /home which I do backup. Even a lot of settings, like E-Mails in Thunderbird, and Bookmarks in Filezilla aren't a problem

The difficult/annoying thigs are
[LIST]
[*]Browser Plugins
[*]Crossover with MSOffice (needed for work)
[*]Installing all programs again
[*]Compizconfig settings & Key/mouse shortcuts
[*]SVN Settings
[*]Figuring out how to set drives to automount again
[*]Restoring Virtualbox and VMs
[/LIST]


Back to the connection problems, it seems better, but I still get connection drops... as stated Ubuntu still thinks it's connected, but I just don't can't send/receive any data anymore.

---

### Post by Leed on 2012-05-31
Hm, had 5 Connection interupts since the last post, that it..


I'm giving up and going back to Oncelot... I always wanted to be on the newest Ubuntu, but this upgrade makes working impossible and as like all LTS Upgrades it doesn't really bring much new things to the Ubuntu experience. 

Pitty, but I'm not ready to waste more hours fidling about on this matter :(

---

