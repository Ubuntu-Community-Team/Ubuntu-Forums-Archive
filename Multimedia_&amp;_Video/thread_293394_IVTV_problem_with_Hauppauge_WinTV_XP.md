---
title: "IVTV problem with Hauppauge WinTV XP"
date: 2006-11-05
forum: Multimedia &amp; Video
---

### Post by winter_rob on 2006-11-05
Ivtv problem with Hauppauge Win TV XP

Ivtv doesn't load anything so MythTV doesn't work.

Can anyone help me?

I have a Hauppauge WinTV XP card and MythTV, but I don't get any TV reception. MythTV does work otherwise. With tvtime I get a very bad picture and no sound, mostly black and white. The remote works, but maybe not all buttons work.

I have a Hauppauge Win TV XP card on a Shuttle SN58G4V3 with a AMD Sempron. I use Ubuntu 6. The Shuttle is connected to a TV set.

It seems that IVTV is loaded, but doesn't load any firmware (or anything else). I did get the firmware from the CD, and also downloaded several sets. Nothing works.

Relevant output (Dutch system):

> ls -l /usr/lib/hotplug/firmware/
total 1068
lrwxrwxrwx 1 root root     26 2006-07-20 10:20 hcw88enc.inf -> /lib/firmware/hcw88enc.inf
-rw-r--r-- 1 root root 262144 2006-03-11 17:32 ivtv-fw-dec.bin
-rw-r--r-- 1 root root 262144 2006-03-11 17:32 ivtv-fw-enc.bin
lrwxrwxrwx 1 root root     41 2006-03-11 17:33 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
-r--r--r-- 1 root root 376836 2006-03-11 17:32 v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 155648 2006-05-01 16:33 v4l-cx2341x-init.mpg
-r--r--r-- 1 root root  14264 2006-03-11 17:32 v4l-cx25840.fw

> md5sum /usr/lib/hotplug/firmware/*
md5sum: /usr/lib/hotplug/firmware/hcw88enc.inf: Onbekend bestand of map
305dba74bbe5905447add8883f3ecb68  /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
d85cb08382395390dc95ac6ebc2205f9  /usr/lib/hotplug/firmware/ivtv-fw-enc.bin
305dba74bbe5905447add8883f3ecb68  /usr/lib/hotplug/firmware/v4l-cx2341x-dec.fw
5f5fa240ada73c3565f5f7de4c7b5138  /usr/lib/hotplug/firmware/v4l-cx2341x-enc.fw
0661f8b2693fe3123e6234557353eacc  /usr/lib/hotplug/firmware/v4l-cx2341x-init.mpg
3a4803384f749d644ee1f1ca9dcb12fa  /usr/lib/hotplug/firmware/v4l-cx25840.fw

uname -a:
Linux shuttle 2.6.15-25-k7 #1 SMP PREEMPT Wed Jun 14 11:43:20 UTC 2006 i686 GNU/Linux

lspci:
0000:02:06.0 Multimedia video controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder (rev 05)
0000:02:06.1 Multimedia controller: Conexant CX23880/1/2/3 PCI Video and Audio Decoder [Audio Port] (rev 05)

lsmod (most messages left out):
Module                  Size  Used by
bttv                  173456  0
video                  16644  0
ivtv                  227220  0
via82cxxx               9988  0 [permanent]
tuner                  25184  0
cx8800                 34828  1
cx88xx                 64288  1 cx8800
i2c_algo_bit           10120  3 bttv,ivtv,cx88xx
video_buf              23108  3 bttv,cx8800,cx88xx
ir_common              10308  1 cx88xx
tveeprom               15504  2 bttv,cx88xx
v4l1_compat            15620  1 cx8800
v4l2_common             6336  2 bttv,cx8800
btcx_risc               5512  3 bttv,cx8800,cx88xx
videodev               10368  5 bttv,ivtv,cx8800,cx88xx
i2c_core               23168  10 bttv,i2c_acpi_ec,ivtv,nvidia,tda9887,tuner,cx88xx,i2c_algo_bit,tveeprom,i2c_nforce2

dmesg:

[17179593.228000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[17179593.228000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40

[17179594.104000] cx2388x v4l2 driver version 0.0.5 loaded
[17179594.104000] **** SET: Misaligned resource pointer: d6fd4f42 Type 07 Len 0

[17179594.104000] CORE cx88[0]: subsystem: 0070:3401, board: Hauppauge WinTV 34xxx models [card=1,autodetected]
[17179594.104000] TV tuner -1 at 0x1fe, Radio tuner -1 at 0x1fe
[17179594.136000] NET: Registered protocol family 17
[17179594.316000] tveeprom 2-0050: Hauppauge model 34519, rev J160, serial# 8346636
[17179594.316000] tveeprom 2-0050: tuner model is LG S001D MK3 (idx 60, type 38)
[17179594.316000] tveeprom 2-0050: TV standards PAL(B/G) PAL(I) SECAM(L/L') PAL(D/K) (eeprom 0x74)
[17179594.316000] tveeprom 2-0050: audio processor is CX881 (idx 31)
[17179594.316000] tveeprom 2-0050: has radio
[17179594.316000] cx88[0]: warning: unknown hauppauge model #34519
[17179594.316000] cx88[0]: hauppauge eeprom: model=34519
[17179594.316000] input: cx88 IR (Hauppauge WinTV 34xxx  as /class/input/input3
[17179594.316000] cx88[0]/0: found at 0000:02:06.0, rev: 5, irq: 209, latency: 32, mmio: 0xe7000000
[17179594.332000] tuner (ivtv): chip found at addr 0xc2 i2c-bus cx88[0]
[17179594.332000] tuner: type set to 38 (Philips PAL/SECAM multi (FM1216ME MK3)) by cx88[0]
[17179594.368000] tda9887 2-0043: (ivtv) chip found @ 0x86 (cx88[0])
[17179594.372000] cx88[0]/0: registered device video0 [v4l2]
[17179594.372000] cx88[0]/0: registered device vbi0
[17179594.372000] cx88[0]/0: registered device radio0

[17179597.244000] ivtv:  ==================== START INIT IVTV ====================
[17179597.244000] ivtv:  version 0.4.6 (tagged release) loading
[17179597.244000] ivtv:  Linux version: 2.6.15-25-k7 SMP preempt K7 gcc-4.0
[17179597.244000] ivtv:  In case of problems please include the debug info between
[17179597.244000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179597.244000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179597.248000] ivtv:  ====================  END INIT IVTV  ====================

[17181795.552000] bttv: driver version 0.9.16 loaded
[17181795.552000] bttv: using 8 buffers with 2080k (520 pages) each for capture

---

### Post by ermannobonifazi on 2006-11-05
See this [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html) and this [http://www.ubuntuforums.org/showthread.php?t=186747](http://www.ubuntuforums.org/showthread.php?t=186747)
Hope this help. It work for me.

---

### Post by winter_rob on 2006-11-06
Thanks for the info.

However, I already tried these guides. The firmwares are for a different Hauppauge cards and didn't work for me. Not my Hauppauge WinTV XP. Thats how I got where I am now. However, I have tried so many different combinations of files and directories, that I am completely confused.

If I do
cat /dev/video > /tmp/test.mpg

I get raw dv, not mpg. However, I know that the card has an MPEG encoder on board. So this again points to problems with the firmware. Somehow, it doesn't load the correct firmware.

Rob

---

