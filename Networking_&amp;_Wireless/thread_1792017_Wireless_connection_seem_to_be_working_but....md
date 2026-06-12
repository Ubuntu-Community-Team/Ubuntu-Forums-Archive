---
title: "Wireless connection seem to be working but..."
date: 2011-06-27
forum: Networking &amp; Wireless
---

### Post by RochJer on 2011-06-27
The issue I am experiencing is that I am trying to connect to 2Wire modem which is my own modem and it seems like I can connect but can't connect at all because it kept saying WPA2/WPA personal connection and asked me for the pass and I have the info on my 2wire modem sticker and I did try key or password and it kept popping up - meaning my info may be wrong but I know I entered the information correctly. Is it wireless driver issue or something I may have missed?

Thanks.

---

### Post by josephmills on 2011-06-27
dont know if I can help you but could we please sere a ```
lspci -nn
```and a```
lsmod
```thanks

---

### Post by RochJer on 2011-06-27
Okay here is the codes you requested:

jeremy@jeremy-Inspiron-1750:~$ lspci -nn
00:00.0 Host bridge [0600]: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub [8086:2a40] (rev 07)
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a42] (rev 07)
00:02.1 Display controller [0380]: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller [8086:2a43] (rev 07)
00:1a.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 [8086:2937] (rev 03)
00:1a.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 [8086:2938] (rev 03)
00:1a.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 [8086:2939] (rev 03)
00:1a.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 [8086:293c] (rev 03)
00:1b.0 Audio device [0403]: Intel Corporation 82801I (ICH9 Family) HD Audio Controller [8086:293e] (rev 03)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 [8086:2940] (rev 03)
00:1c.1 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 [8086:2942] (rev 03)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 [8086:2944] (rev 03)
00:1c.4 PCI bridge [0604]: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 [8086:2948] (rev 03)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 [8086:2934] (rev 03)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 [8086:2935] (rev 03)
00:1d.2 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 [8086:2936] (rev 03)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 [8086:293a] (rev 03)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev 93)
00:1f.0 ISA bridge [0601]: Intel Corporation ICH9M LPC Interface Controller [8086:2919] (rev 03)
00:1f.2 SATA controller [0106]: Intel Corporation ICH9M/M-E SATA AHCI Controller [8086:2929] (rev 03)
00:1f.3 SMBus [0c05]: Intel Corporation 82801I (ICH9 Family) SMBus Controller [8086:2930] (rev 03)
09:00.0 Ethernet controller [0200]: Marvell Technology Group Ltd. 88E8040 PCI-E Fast Ethernet Controller [11ab:4354] (rev 13)
0c:00.0 Network controller [0280]: Intel Corporation WiFi Link 5100 [8086:4232]
jeremy@jeremy-Inspiron-1750:~$ lsmod
Module                  Size  Used by
binfmt_misc            17565  1 
parport_pc             36959  0 
ppdev                  17113  0 
snd_hda_codec_idt      71137  1 
snd_hda_intel          33211  4 
snd_hda_codec         103804  2 snd_hda_codec_idt,snd_hda_intel
snd_hwdep              13604  1 snd_hda_codec
snd_pcm                96625  3 snd_hda_intel,snd_hda_codec
joydev                 17606  0 
snd_seq_midi           13324  0 
snd_rawmidi            30486  1 snd_seq_midi
snd_seq_midi_event     14899  1 snd_seq_midi
arc4                   12529  2 
snd_seq                61621  2 snd_seq_midi,snd_seq_midi_event
snd_timer              29602  2 snd_pcm,snd_seq
snd_seq_device         14462  3 snd_seq_midi,snd_rawmidi,snd_seq
snd                    67382  16 snd_hda_codec_idt,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
psmouse                73535  0 
uvcvideo               72195  0 
i915                  514985  3 
soundcore              12680  1 snd
videodev               82052  1 uvcvideo
iwlagn                333500  0 
drm_kms_helper         42136  1 i915
drm                   227495  4 i915,drm_kms_helper
snd_page_alloc         18529  2 snd_hda_intel,snd_pcm
iwlcore               167503  1 iwlagn
lp                     17825  0 
parport                46458  3 parport_pc,ppdev,lp
v4l2_compat_ioctl32    17078  1 videodev
dell_laptop            13827  0 
dell_wmi               12681  0 
serio_raw              13166  0 
i2c_algo_bit           13400  1 i915
mac80211              294370  2 iwlagn,iwlcore
video                  19438  1 i915
cfg80211              178528  3 iwlagn,iwlcore,mac80211
dcdbas                 14438  1 dell_laptop
sparse_keymap          13898  1 dell_wmi
usbhid                 46956  0 
usb_storage            53538  0 
hid                    91020  1 usbhid
uas                    17996  0 
sky2                   58509  0 
ahci                   25951  3 
libahci                26642  1 ahci
jeremy@jeremy-Inspiron-1750:~$

---

### Post by josephmills on 2011-06-27
go to synaptic and see if wpa supplicant  is installed if not install it. then reboot anything ?

---

### Post by RochJer on 2011-06-27
I checked the synaptic package manager and wpasupplicant is already installed.

---

### Post by josephmills on 2011-06-27
have you tired to reset you router? could we also see a ```
rfkill list all 
```

---

### Post by RochJer on 2011-06-27
jeremy@jeremy-Inspiron-1750:~$ rfkill list all
0: dell-wifi: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
jeremy@jeremy-Inspiron-1750:~$ 

Resetted the router and still has same result.

---

### Post by josephmills on 2011-06-27
try and set up your network manually. anything?

---

### Post by westie457 on 2011-06-27
> **RochJer said:**
> The issue I am experiencing is that I am trying to connect to 2Wire modem which is my own modem and it seems like I can connect but can't connect at all because it kept saying WPA2/WPA personal connection and asked me for the pass and I have the info on my 2wire modem sticker and I did try key or password and it kept popping up - meaning my info may be wrong but I know I entered the information correctly. Is it wireless driver issue or something I may have missed?

Thanks.

Hi I had a similar problem a while ago with the router not accepting the WPA password. The work around I did was to connect a cable to enable me to access the home page of the router and reset it to factory default.

Then instead of doing an automatic set-up I did a manual one removing all security to get a working connection then I went through the pages of the router and set up 'MAC Address Filtering' only allowing access to my dual-booting pc's. Finally I changed the log in details from the default settings to stop others from piggy-backing off my connection. Have been using it that way for a year now.

PS I have tried a couple of times to use it with a password and one OS still refuses to accept it.

Hope this is helpful to you.

---

### Post by bkratz on 2011-06-27
Also, Ubuntu often seems to have troubles with mixed mode (having the router set to both wpa/wpa2). You might want to try (while in the configuration page of the router) changing to either wpa [COLOR="red"]or[/COLOR] wpa2 (but not both).

---

### Post by RochJer on 2011-06-27
> **bkratz said:**
> Also, Ubuntu often seems to have troubles with mixed mode (having the router set to both wpa/wpa2). You might want to try (while in the configuration page of the router) changing to either wpa [COLOR="red"]or[/COLOR] wpa2 (but not both).

I have tried this step and it didn't work either. I assume ubuntu 11.04 is not wireless-friendly with 2wire modem so I'm just hard-wired for now. Like previous replies, this OS may be the one that rejects any passwords for the wireless. Oh well, at least I tried.

---

