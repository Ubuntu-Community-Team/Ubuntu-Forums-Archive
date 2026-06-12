---
title: "How to connect to broadband wirelessly???"
date: 2011-09-10
forum: Networking &amp; Wireless
---

### Post by divyansh.sachdeva on 2011-09-10
I'm relatively a newbie and don't have much experience with linux. I'm unable to connect to my broadband connection using a wi-fi modem, though the conection works fine with a LAN cable. Details:

Hardware: Toshiba Satellite L650
OS: Ubuntu 11.04
Broadband: Bsnl
Modem: WA1003A

PS: My modem has been configured for bridge mode.

Please guide with step-by-step instructions.
Help appreciated. 

:confused::confused::confused:

---

### Post by praseodym on 2011-09-10
Hello,

please show the outputs of the following terminal commands:

```
lspci -nnk | grep -iA2 net
lsmod
rfkill list
iwconfig

```

---

### Post by divyansh.sachdeva on 2011-09-10
@praseodym: Thanks for the speedy reply. Here are the outputs you asked for: 

1. lspci -nnk | grep -iA2 net

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:fd50]
	Kernel driver in use: atl1c

2. lsmod

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:fd50]
	Kernel driver in use: atl1c
Module                  Size  Used by
pppoe                  17476  2 
pppox                  13158  1 pppoe
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_seq_midi           13132  0 
snd_hwdep              13274  1 snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                900494  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17203  0 
toshiba_bluetooth      12711  0 
uvcvideo               66851  0 
sparse_keymap          13666  0 
wl                   2642531  0 
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
ttm                    65184  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18951  0 
psmouse                73312  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 radeon
drm                   184164  5 radeon,ttm,drm_kms_helper
lib80211               14570  2 lib80211_crypt_tkip,wl
serio_raw              12990  0 
intel_ips              17769  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
atl1c                  36237  0 
libahci                25548  1 ahci

3. rfkill list

03:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller [14e4:4727] (rev 01)
	Subsystem: Askey Computer Corp. Device [144f:7175]
	Kernel driver in use: wl
--
04:00.0 Ethernet controller [0200]: Atheros Communications AR8152 v1.1 Fast Ethernet [1969:2060] (rev c1)
	Subsystem: Toshiba America Info Systems Device [1179:fd50]
	Kernel driver in use: atl1c
Module                  Size  Used by
pppoe                  17476  2 
pppox                  13158  1 pppoe
parport_pc             32111  0 
ppdev                  12849  0 
binfmt_misc            13213  1 
joydev                 17322  0 
snd_hda_codec_hdmi     27535  1 
snd_hda_codec_conexant    43782  1 
snd_hda_intel          24113  2 
snd_hda_codec          90901  3 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel
snd_seq_midi           13132  0 
snd_hwdep              13274  1 snd_hda_codec
snd_rawmidi            25269  1 snd_seq_midi
snd_pcm                80042  3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec
radeon                900494  3 
snd_seq_midi_event     14475  1 snd_seq_midi
snd_seq                51291  2 snd_seq_midi,snd_seq_midi_event
lib80211_crypt_tkip    17203  0 
toshiba_bluetooth      12711  0 
uvcvideo               66851  0 
sparse_keymap          13666  0 
wl                   2642531  0 
videodev               75143  1 uvcvideo
snd_timer              28659  2 snd_pcm,snd_seq
ttm                    65184  1 radeon
snd_seq_device         14110  3 snd_seq_midi,snd_rawmidi,snd_seq
video                  18951  0 
psmouse                73312  0 
snd                    55295  14 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_rawmidi,snd_pcm,snd_seq,snd_timer,snd_seq_device
drm_kms_helper         40745  1 radeon
drm                   184164  5 radeon,ttm,drm_kms_helper
lib80211               14570  2 lib80211_crypt_tkip,wl
serio_raw              12990  0 
intel_ips              17769  0 
soundcore              12600  1 snd
snd_page_alloc         14073  2 snd_hda_intel,snd_pcm
i2c_algo_bit           13184  1 radeon
lp                     13349  0 
parport                36746  3 parport_pc,ppdev,lp
usb_storage            43946  0 
uas                    17676  0 
ahci                   21591  3 
atl1c                  36237  0 
libahci                25548  1 ahci
0: brcmwl-0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
eth1      IEEE 802.11  Access Point: Not-Associated   
          Link Quality:5  Signal level:0  Noise level:159
          Rx invalid nwid:0  invalid crypt:0  invalid misc:0


4. iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

ppp0      no wireless extensions.

---

### Post by praseodym on 2011-09-10
Blacklist the following module:

```
echo "blacklist brcm80211" | sudo tee /etc/modprobe.d/blacklist-brcm80211.conf
```
and reboot. Does you router accept new clients (MAC-adress filter)?

---

### Post by divyansh.sachdeva on 2011-09-10
I executed that code and re-booted my system. The Wireless connections are now visible and I can establish a connection with my modem.

As for the router accepting new clients, I've no idea.

---

### Post by divyansh.sachdeva on 2011-09-10
Help appreciated so far. Now the second problem is that I use a username and password, provided by my ISP, to connect to internet... Where do I do that???

---

### Post by praseodym on 2011-09-10
Go to your router interface and establish a PPPoE-connection

---

### Post by divyansh.sachdeva on 2011-09-10
I just re-booted and the list of wireless connections has disappeared again.

---

### Post by haqking on 2011-09-10
> **praseodym said:**
> Go to your router interface and establish a PPPoE-connection

+1

If you have trouble see here [http://www.calcutta.bsnl.co.in/dataoneinstall/menu.html](http://www.calcutta.bsnl.co.in/dataoneinstall/menu.html)

it is your ISP, a link to your modem and a zip file download for Linux

---

### Post by divyansh.sachdeva on 2011-09-10
And can't I configure it with a bridge type connection, so that I dont have to store my username and password on the router??

---

### Post by divyansh.sachdeva on 2011-09-10
@haqking: Thanks for help. But still doesnt solve the problem of ubuntu not detecting wireless networks available.

---

### Post by haqking on 2011-09-10
> **divyansh.sachdeva said:**
> @haqking: Thanks for help. But still doesnt solve the problem of ubuntu not detecting wireless networks available.


Make it a permanent connection from network manager.

Plus they dont always show up staright away until your keyring is unlocked, how is your keyring setup ?

---

### Post by divyansh.sachdeva on 2011-09-11
I've no idea about keyrings... I haven't set up any yet, so I'm guessing its unsecure. 

Okay, I'm lost here. Lets take it one step at a time. 

The first and foremost problem is getting my system to detect wireless networks. As of now it does not detect any wireless connections available.

---

### Post by coffeecat on 2011-09-11
This thread closed.

The OP has started a new thread having tried to install the firmware-b43-installer, here:

[http://ubuntuforums.org/showthread.php?t=1842360](http://ubuntuforums.org/showthread.php?t=1842360)

If anyone wishes to help further, please go to the new thread.

---

