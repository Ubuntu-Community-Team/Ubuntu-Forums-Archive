---
title: "Skystar 2 Rev 3.3 (b2c2-flexcop, cx24120): installation/tuning"
date: 2010-07-27
forum: Multimedia Software
---

### Post by Ocye on 2010-07-27
Hi,

to run this card a proprietary module (cx24120_blob.o_shipped) needs to be included when source are compiled. Therefore, any more recent v4l code fails. On the other hand, I cannot compile the code that should be used for the object file (something from about 2008) with my kernel (2.6.34). 

At a russian forum ([http://www.forum.free-x.de/wbb/index.php?page=Thread&threadID=513](http://www.forum.free-x.de/wbb/index.php?page=Thread&threadID=513)) some patches are recommended, but these are not appropriate to my kernel as well. But with some manual adaptation (own definition of FC_SKY_REV33 in flexcop-fe-tuner.c) I got the module to run finally. But now the module fails at tuning with "diseqc_send_msg: FE_DISEQC_SEND_MASTER_CMD failed".

Does anyone has a suggestion?

[quote=syslog]Jul 27 19:33:51 Sonne kernel: [ 2232.629283] Hardware name: MS-7522
Jul 27 19:33:51 Sonne kernel: [ 2232.629286] name 'Technisat/B2C2 FlexCop II/IIb/III Digital TV PCI Driver'
Jul 27 19:33:51 Sonne kernel: [ 2232.629289] Modules linked in: b2c2_flexcop_pci(+) b2c2_flexcop dvb_core cx24123 mc44s803 cx24120 xc5000 mt20xx tda9887 isl6421 tea5767 tea5761 tda8290 cryptd aes_x86_64 aes_generic binfmt_misc ppdev vboxnetadp vboxnetflt vboxdrv arc4 snd_hda_codec_realtek nfsd exportfs snd_hda_intel nfs snd_hda_codec lockd snd_hwdep nfs_acl auth_rpcgss snd_pcm_oss snd_mixer_oss snd_pcm ath5k mac80211 snd_seq_dummy snd_seq_oss joydev snd_seq_midi snd_rawmidi snd_seq_midi_event f71882fg snd_seq snd_timer snd_seq_device fbcon tileblit ath font usbhid coretemp psmouse snd cfg80211 soundcore bitblit nvidia(P) hid uinput snd_page_alloc led_class softcursor serio_raw lp sunrpc parport ohci1394 ieee1394 [last unloaded: tda8290]
Jul 27 19:33:51 Sonne kernel: [ 2232.629364] Pid: 15725, comm: modprobe Tainted: P    	W  2.6.34-020634-generic #020634
Jul 27 19:33:51 Sonne kernel: [ 2232.670414] DVB: registering new adapter (FlexCop Digital TV device)
Jul 27 19:33:51 Sonne kernel: [ 2232.672069] b2c2-flexcop: MAC address = 00:08:c9:e0:ba:fa
Jul 27 19:33:51 Sonne kernel: [ 2232.672199] CX24120: detected CX24120 (Revision: 0x07)
Jul 27 19:33:51 Sonne kernel: [ 2232.672490] b2c2-flexcop: ISL6421 successfully attached
Jul 27 19:33:51 Sonne kernel: [ 2232.672492] b2c2-flexcop: found 'Conexant CX24120/CX24118' .
Jul 27 19:33:51 Sonne kernel: [ 2232.672540] DVB: registering adapter 0 frontend 0 (Conexant CX24120/CX24118)...
Jul 27 19:33:51 Sonne kernel: [ 2232.672590] b2c2-flexcop: initialization of 'Sky2PC/SkyStar 2 DVB-S2 rev 3.3' at the 'PCI' bus controlled by a 'FlexCopIIb' complete[/quote]

[quote=w_scan -f s -c DE -s S19E2]w_scan version 20091230 (compiled for DVB API 5.1)
using settings for 19.2 east Astra 1F/1G/1H/1KR/1L
frontend_type DVB-S, channellist 6
output format vdr-1.6
Info: using DVB adapter auto detection.
/dev/dvb/adapter0/frontend0 -> DVB-S "Conexant CX24120/CX24118": good :-)
Using DVB-S frontend (adapter /dev/dvb/adapter0/frontend0)
-_-_-_-_ Getting frontend capabilities-_-_-_-_ 
Using DVB API 5.1
frontend Conexant CX24120/CX24118 supports
INVERSION_AUTO
DVB-S
using LNB "UNIVERSAL"
-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_-_ 
(time: 00:00) diseqc_send_msg: FE_DISEQC_SEND_MASTER_CMD failed. [/quote]

---

