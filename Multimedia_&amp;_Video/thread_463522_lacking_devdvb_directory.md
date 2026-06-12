---
title: "lacking /dev/dvb directory"
date: 2007-06-03
forum: Multimedia &amp; Video
---

### Post by creznedmick on 2007-06-03
GREETINGS
I have a problem with my Aver DVB-T 773 cpature card. Although it looks to me like the relavant saa7134 modules are loaded there is no /dev/dvb file generated and from here I can not go forward            

$ grep DVB  /var/log/messages
May 30 09:07:45 creznedmassage1 kernel: [   22.016000] saa7133[0]: subsystem: 1461:2c05, board: AverTV DVB-T 777 [card=85,autodetected]
May 30 09:07:45 creznedmassage1 kernel: [   22.016000] input: saa7134 IR (AverTV DVB-T 777) as /class/input/input2
Jun  1 08:41:20 creznedmassage1 kernel: [   22.096000] saa7133[0]: subsystem: 1461:2c05, board: AverTV DVB-T 777 [card=85,autodetected]
Jun  1 08:41:20 creznedmassage1 kernel: [   22.096000] input: saa7134 IR (AverTV DVB-T 777) as /class/input/input3


$ lsmod 
saa7134               122080  1  saa7134_alsa
video_buf              26116   2   saa7134_alsa,saa7134
compat_ioctl32          2304  1 saa7134
ir_kbd_i2c              9872    1  saa7134
i2c_core               22784   4  i2c_ec,i2c_viapro,saa7134,ir_kbd_i2c
ir_common           31236   2  saa7134,ir_kbd_i2c
videodev               28160  1  saa7134
v4l2_common       25216   2  saa7134,videodev
v4l1_compat         15236   2  saa7134,videodev
snd_pcm              79876   5  snd_via82xx,snd_ens1371,snd_ac97_codec,saa7134_alsa,snd_pcm_oss

$ lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8377 [KT400/KT600 AGP] Host Bridge (rev 80)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8237 PCI Bridge
00:09.0 Multimedia controller: Philips Semiconductors SAA7133/SAA7135 Video Broadcast Decoder (rev d1)
00:0b.0 Multimedia audio controller: Ensoniq ES1371 [AudioPCI-97] (rev 08)
00:0f.0 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:10.0 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.1 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 81)
00:10.4 USB Controller: VIA Technologies, Inc. USB 2.0 (rev 86)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8237 ISA bridge [KT600/K8T800/K8T890 South]
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 60)
00:12.0 Ethernet controller: VIA Technologies, Inc. VT6102 [Rhine-II] (rev 78)

 grep |dvb dmesg     comes up blank
Thanks Michael

---

### Post by creznedmick on 2007-06-03
I reloaded the v4l pakage and the directory appeared

---

