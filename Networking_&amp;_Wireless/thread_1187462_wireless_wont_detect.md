---
title: "wireless wont detect"
date: 2009-06-14
forum: Networking &amp; Wireless
---

### Post by iain.mjbanks on 2009-06-14
i just set up my laptop's wireless card using the 43xx fwcutter program. i got the little blue light to go on, but it's not detecting my wireless. i don't have ethernet at the moment, but i can download and transfer files from my other computer. 

any help would be much appreciated. thanks!

Originally Posted by iain.mjbanks  
iain@iain-laptop:~$ lspci|grep net
02:0e.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
iain@iain-laptop:~$ lsmod
Module Size Used by
nls_iso8859_1 12032 1 
nls_cp437 13696 1 
vfat 18816 1 
fat 58272 1 vfat
usb_storage 82880 1 
rfkill_input 12800 0 
i915 65540 2 
drm 96296 3 i915
ppdev 15620 0 
bridge 56340 0 
stp 10500 1 bridge
bnep 20224 2 
lp 17156 0 
parport 42220 2 ppdev,lp
joydev 18368 0 
snd_intel8x0 37532 2 
arc4 9856 2 
snd_ac97_codec 112292 1 snd_intel8x0
ecb 10752 2 
ac97_bus 9856 1 snd_ac97_codec
snd_pcm_oss 46336 0 
snd_mixer_oss 22656 2 snd_pcm_oss
snd_pcm 82948 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 10756 0 
snd_seq_oss 37760 0 
snd_seq_midi 14336 0 
snd_rawmidi 29696 1 snd_seq_midi
snd_seq_midi_event 15104 2 snd_seq_oss,snd_seq_midi
b43 131484 0 
snd_seq 56880 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer 29704 2 snd_pcm,snd_seq
snd_seq_device 14988 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
pcmcia 44748 0 
mac80211 217208 1 b43
pcspkr 10496 0 
psmouse 61972 0 
yenta_socket 32396 1 
rsrc_nonstatic 19328 1 yenta_socket
snd 62628 12 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti mer,snd_seq_device
iTCO_wdt 19108 0 
iTCO_vendor_support 11652 1 iTCO_wdt
cfg80211 38032 1 mac80211
pcmcia_core 43540 3 pcmcia,yenta_socket,rsrc_nonstatic
soundcore 15200 2 snd
snd_page_alloc 16904 2 snd_intel8x0,snd_pcm
serio_raw 13316 0 
led_class 12036 1 b43
input_polldev 11912 1 b43
video 25360 0 
output 11008 1 video
intel_agp 34108 1 
agpgart 42696 3 drm,intel_agp
ohci1394 38576 0 
b44 35984 0 
mii 13312 1 b44
ieee1394 94660 1 ohci1394
ssb 41220 2 b43,b44
fbcon 46112 0 
tileblit 10752 1 fbcon
font 16384 1 fbcon
bitblit 13824 1 fbcon
softcursor 9984 1 bitblit
iain@iain-laptop:~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:15:60:b4:44:86 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:16 

lo Link encap:Local Loopback 
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:12 errors:0 dropped:0 overruns:0 frame:0
TX packets:12 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0 
RX bytes:840 (840.0 B) TX bytes:840 (840.0 B)

wlan0 Link encap:Ethernet HWaddr 00:14:a5:22:18:fe 
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

wmaster0 Link encap:UNSPEC HWaddr 00-14-A5-22-18-FE-00-00-00-00-00-00-00-00-00-00 
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000 
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

iain@iain-laptop:~$

---

### Post by superprash2003 on 2009-06-15
post output of
1)sudo iwlist scanning
2)iwconfig

---

