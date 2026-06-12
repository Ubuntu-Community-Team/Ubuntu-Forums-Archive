---
title: "Zoom 4411 usb won't connect"
date: 2010-07-29
forum: Networking &amp; Wireless
---

### Post by RealGomer on 2010-07-29
I've loaded Ubuntu 10.04 onto a dual boot machine. I have a Zoom 4411 Wireless-N USB dongle that works fine in Windows. The wireless network icon implies I'm connected but I can't connect to the internet or see the PCs on my network. Here's the output from lsmod and ifconfig.

~$ lsmod
Module Size Used by
nls_utf8 1069 1
isofs 29250 1
binfmt_misc 6587 1
fbcon 35102 71
tileblit 2031 1 fbcon
font 7557 1 fbcon
bitblit 4707 1 fbcon
softcursor 1189 1 bitblit
vga16fb 11385 0
vgastate 8961 1 vga16fb
snd_intel8x0 25588 2
snd_ac97_codec 100646 1 snd_intel8x0
ac97_bus 1002 1 snd_ac97_codec
snd_pcm_oss 35308 0
snd_mixer_oss 13746 1 snd_pcm_oss
snd_pcm 70662 3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy 1338 0
snd_seq_oss 26726 0
snd_seq_midi 4557 0
snd_rawmidi 19056 1 snd_seq_midi
snd_seq_midi_event 6003 2 snd_seq_oss,snd_seq_midi
rt2870sta 461811 0
snd_seq 47263 6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
arc4 1153 2
radeon 674135 3
rt2800usb 31531 0
snd_timer 19098 2 snd_pcm,snd_seq
rt2x00usb 9703 1 rt2800usb
snd_seq_device 5700 5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
joydev 8708 0
ttm 49943 1 radeon
rt2x00lib 27509 2 rt2800usb,rt2x00usb
led_class 2864 1 rt2x00lib
drm_kms_helper 29297 1 radeon
mac80211 204922 2 rt2x00usb,rt2x00lib
ppdev 5259 0
ns558 3056 0
snd 54148 14 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_oss,snd_rawmidi,snd_seq,snd_ti mer,snd_seq_device
usbhid 36110 0
hid 67032 1 usbhid
drm 162471 5 radeon,ttm,drm_kms_helper
i2c_algo_bit 5028 1 radeon
cfg80211 126485 2 rt2x00lib,mac80211
crc_ccitt 1339 1 rt2800usb
amd64_agp 7025 1
gameport 9089 2 ns558
soundcore 6620 1 snd
k8temp 3024 0
parport_pc 25962 1
agpgart 31724 3 ttm,drm,amd64_agp
i2c_nforce2 5199 0
snd_page_alloc 7076 2 snd_intel8x0,snd_pcm
shpchp 28820 0
lp 7028 0
parport 32635 3 ppdev,parport_pc,lp
skge 35683 0
floppy 53016 0
pata_amd 8766 3


~$ ifconfig
eth0 Link encap:Ethernet HWaddr 00:0d:61:68:d7:81
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
Interrupt:19

lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:104 errors:0 dropped:0 overruns:0 frame:0
TX packets:104 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:8192 (8.1 KB) TX bytes:8192 (8.1 KB)

wlan0 Link encap:Ethernet HWaddr 00:40:36:3c:0a:d9
UP BROADCAST MULTICAST MTU:1500 Metric:1
RX packets:0 errors:0 dropped:0 overruns:0 frame:0
TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)

I logged in as root and blacklisted rt2800usb. I am also getting a message about needing to enter the login keyring password, whatever that is. The system is set to log in automatically.
Do I need to install the drivers at System -> Administration-> Hardware Drivers as well? Do I need to enter a BSSID in the wireless configuration screen? What is the BSSID if so?

And most importantly, did I already post this question? Oh boy, is the ol' melon fried.

---

### Post by chili555 on 2010-07-29
You have too many drivers loaded. Please edit, as root, /etc/modprobe.d/blacklist.conf to add these lines:```
blacklist rt2800usb
blacklist rt2x00usb
blacklist rt2x00lib
```Proofread carefully. Reboot and connect.

---

### Post by RealGomer on 2010-07-30
I blacklisted the three rt2*** files. No go. Another person suggested removing the keyring file using 
rm .gnome2/keyrings/login.keyring which I did as root and using Terminal.

I get aq pop up asking for my keyrings password, which I have no idea what it is so I use the Ubuntu admins password. If I click on the wirewess icon, I get a message I've been disconnected. I set up the D-Link DIR-624 router so it plainly sees the wireless dongle. It still works just fine under Windows, but craps out under Ubuntu. Next step?

---

### Post by chili555 on 2010-07-31
Please post:```
dmesg | grep -e rt2 -e wlan
```Thanks.

---

### Post by RealGomer on 2010-08-15
Well, I got rid of the Zoom usb wireless adapter and tried another usb adapter that claimed to have the Linux drivers on disk. Of course, I need to figure out how to load them. Anyway, are there other settings that need to be made in Lucid to get a connection from the PC thru a router to the internet. I've run the commands, set the IP addresses, and tried what's been suggested. I checked with D-Link and they suggested turning off WEP/WPA and wireless security. (YIKES!!) I did notice that even tho both Network Manager & WICD say the adapter is working and connected, neither the router not the other PC's are seen.
So, what do the mavens of Linux suggest? Who knows. Maybe we'll un up with a sticky on how to set up a wireless usb adapter.
Oh, I forgot to get the results from Chili555's request. Sorry.

---

