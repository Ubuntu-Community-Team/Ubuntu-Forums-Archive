---
title: "connect to wireless network"
date: 2013-06-13
forum: Networking &amp; Wireless
---

### Post by judy200951 on 2013-06-13
[COLOR=#000000][FONT=Arial][TABLE="width: 0"]
[TR="bgcolor: transparent"]
[TD="class: postcell, bgcolor: transparent"]I have Toshiba satellite C850-B884 laptop running windows 8 did dual boot with backtrack 5 32 bit. The problem is that backtrack can't recognize the WiFi card :(and I can't connect to the internet I am using another laptop right now
uname -a
Linux bt 3.2.6
lspci -nnk | grep -iA2 net
02:00.0 Network controller [0280]: Realtek Semiconductor Co., Ltd. Device [10ec:8723] 03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 05) Kernel driver in use: r8169 Kernel modules: r8169
Module Size Used by dm_crypt 22236 0 snd_hda_codec_hdmi 31410 1 snd_hda_codec_realtek 172903 1 snd_hda_intel 32238 0 snd_hda_codec 93484 3 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel snd_hwdep 13232 1 snd_hda_codec snd_pcm 72878 3 snd_hda_codec_hdmi,snd_hda_intel,snd_hda_codec snd_seq_midi 13132 0 snd_rawmidi 24215 1 snd_seq_midi snd_seq_midi_event 14076 1 snd_seq_midi snd_seq 50403 2 snd_seq_midi,snd_seq_midi_event snd_timer 23911 2 snd_pcm,snd_seq snd_seq_device 13817 3 snd_seq_midi,snd_rawmidi,snd_seq snd 52787 10 snd_hda_codec_hdmi,snd_hda_codec_realtek,snd_hda_intel,snd_hda_codec,snd_hwdep,snd_pcm,snd_rawmidi,snd_seq,snd_timer,snd_seq_device soundcore 12534 1 snd snd_page_alloc 13709 2 snd_hda_intel,snd_pcm mei 35758 0 joydev 17161 0 btusb 17979 0 bluetooth 149909 1 btusb btusb 17979 0
videodev 82668 1 uvcvideo psmouse 72465 0 mac_hid 13037 0 serio_raw 13027 0 lp 13321 0 parport 34960 1 lp toshiba_bluetooth 12711 0 toshiba_acpi 17759 0 sparse_keymap 13342 1 toshiba_acpi dm_mirror 21585 0 dm_region_hash 15035 1 dm_mirror dm_log 17871 2 dm_mirror,dm_region_hash aufs 162169 0 ums_realtek 17562 0 usb_storage 42478 1 ums_realtek uas 17476 0 r8169 46895 0 wmi 18273 0
ifconfig
eth0 Link encap:Ethernet HWaddr 7c:05:07:00:d0:40
UP BROADCAST MULTICAST MTU:1500 Metric:1 RX packets:0 errors:0 dropped:0 overruns:0 frame:0 TX packets:0 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000 RX bytes:0 (0.0 B) TX bytes:0 (0.0 B) Interrupt:42 Base address:0xa000
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0 inet6 addr: ::1/128 Scope:Host UP LOOPBACK RUNNING MTU:16436 Metric:1 RX packets:22 errors:0 dropped:0 overruns:0 frame:0 TX packets:22 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0 RX bytes:1425 (1.4 KB) TX bytes:1425 (1.4 KB)
lo no wireless extensions.
eth0 no wireless extensions.
[/TD]
[/TR]
[/TABLE]
[/FONT][/COLOR]

---

### Post by kiltedcameraman on 2013-06-14
Read through this thread [http://ubuntuforums.org/showthread.php?t=2039318](http://ubuntuforums.org/showthread.php?t=2039318) and it should help you get the drivers and get them installed.

---

