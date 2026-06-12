---
title: "PVR USB2: IR receiver doesn't work since Lucid"
date: 2010-05-06
forum: Multimedia Software
---

### Post by deadland on 2010-05-06
Hi ubuntu friend,

I really don't know what happened, but since Lucid the IR receiver of my Hauppauge PVR USB2 doesn't work anymore.

When I have lirc installed I get an endless error in dmesg:

```
pvrusb2: Attempted to execute control transfer when device not ok
```


When I boot my pc without lirc, it looks like this:
```
[   97.709026] usbcore: registered new interface driver pvrusb2
[   97.709041] pvrusb2: V4L in-tree version:Hauppauge WinTV-PVR-USB2 MPEG2 Encoder/Tuner
[   97.709051] pvrusb2: Debug mask is 31 (0x1f)
[   97.720273] pvrusb2_a: i2c scan beginning
[   97.771949] pvrusb2_a: i2c scan: found device @ 0x18
[   97.808667] pvrusb2_a: i2c scan: found device @ 0x21
[   97.855419] pvrusb2_a: i2c scan: found device @ 0x40
[   97.895400] pvrusb2_a: i2c scan: found device @ 0x50
[   97.936072] pvrusb2_a: i2c scan: found device @ 0x61
[   97.950009] pvrusb2_a: i2c scan done.
[   97.950022] pvrusb2: Binding ir_video to i2c address 0x18.
[   97.996522] saa7115 2-0021: saa7115 found (1f7115d0e100000) @ 0x42 (pvrusb2_a)
[   98.149285] pvrusb2: Attached sub-driver saa7115
[   98.172208] msp3400 2-0040: MSP3415G-B8 found @ 0x80 (pvrusb2_a)
[   98.172222] msp3400 2-0040: msp3400 supports nicam and radio, mode is autodetect and autoselect
[   98.172387] pvrusb2: Attached sub-driver msp3400
[   98.211793] tuner 2-0061: chip found @ 0xc2 (pvrusb2_a)
[   98.211810] pvrusb2: Attached sub-driver tuner
[   98.227737] tuner 2-0043: chip found @ 0x86 (pvrusb2_a)
[   98.228562] tda9887 2-0043: creating new instance
[   98.228572] tda9887 2-0043: tda988[5/6/7] found
[   98.229155] tda9887 2-0043: i2c i/o error: rc == -5 (should be 4)
[   98.229190] pvrusb2: Attached sub-driver tuner
[   98.252837] tveeprom 2-0050: Hauppauge model 29034, rev C547, serial# 7141327
[   98.252853] tveeprom 2-0050: tuner model is LG TP18PSB01D (idx 47, type 28)
[   98.252864] tveeprom 2-0050: TV standards PAL(B/G) (eeprom 0x04)
[   98.252874] tveeprom 2-0050: audio processor is MSP3415 (idx 6)
[   98.252883] tveeprom 2-0050: decoder processor is SAA7115 (idx 19)
[   98.252892] tveeprom 2-0050: has radio, has IR receiver, has no IR transmitter
[   98.252912] pvrusb2: Supported video standard(s) reported available in hardware: PAL-B/B1/G/H;SECAM-B/G/H
[   98.252928] pvrusb2: Mapping standards mask=0xd000f (PAL-B/B1/G/H;SECAM-B/G/H)
[   98.252937] pvrusb2: Setting up 9 unique standard(s)
[   98.252947] pvrusb2: Set up standard idx=0 name=PAL-B/G
[   98.252956] pvrusb2: Set up standard idx=1 name=SECAM-B/G
[   98.252964] pvrusb2: Set up standard idx=2 name=PAL-B
[   98.252972] pvrusb2: Set up standard idx=3 name=PAL-B1
[   98.252980] pvrusb2: Set up standard idx=4 name=PAL-G
[   98.252988] pvrusb2: Set up standard idx=5 name=PAL-H
[   98.252996] pvrusb2: Set up standard idx=6 name=SECAM-B
[   98.253004] pvrusb2: Set up standard idx=7 name=SECAM-G
[   98.253012] pvrusb2: Set up standard idx=8 name=SECAM-H
[   98.253024] pvrusb2: Initial video standard guessed as PAL-B/B1/G
[   98.253064] pvrusb2: Device initialization completed successfully.
[   98.253377] usb 1-3: firmware: requesting v4l-cx2341x-enc.fw
[   98.255100] pvrusb2: registered device video1 [mpeg]
[   98.259073] pvrusb2: registered device radio0 [mpeg]
[   98.568414] tuner-simple 2-0061: creating new instance
[   98.568432] tuner-simple 2-0061: type set to 28 (LG PAL_BG+FM (TPI8PSB01D))
[   98.676883] tda9887 2-0043: i2c i/o error: rc == -5 (should be 4)
[   98.751194] tda9887 2-0043: i2c i/o error: rc == -5 (should be 4)
[   98.754627] tda9887 2-0043: i2c i/o error: rc == -5 (should be 4)

```

I also tried to build the latest v4l-dvb, but this also doesn't work:
```
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-22-generic'
  CC [M]  /home/tama/src/v4l-dvb/v4l/ir-raw-event.o
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c: In function 'ir_raw_event_register':
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:80: warning: passing argument 1 of 'kfifo_alloc' makes integer from pointer without a cast
include/linux/kfifo.h:37: note: expected 'unsigned int' but argument is of type 'struct kfifo *'
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:80: warning: passing argument 3 of 'kfifo_alloc' makes pointer from integer without a cast
include/linux/kfifo.h:37: note: expected 'struct spinlock_t *' but argument is of type 'unsigned int'
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:80: warning: assignment makes integer from pointer without a cast
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c: In function 'ir_raw_event_store':
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:145: error: implicit declaration of function 'kfifo_in'
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c: In function 'ir_raw_event_handle':
/home/tama/src/v4l-dvb/v4l/ir-raw-event.c:168: error: implicit declaration of function 'kfifo_out'
make[3]: *** [/home/tama/src/v4l-dvb/v4l/ir-raw-event.o] Error 1
make[2]: *** [_module_/home/tama/src/v4l-dvb/v4l] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-22-generic'
make[1]: *** [default] Fehler 2
make[1]: Verlasse Verzeichnis '/home/tama/src/v4l-dvb/v4l'
make: *** [all] Fehler 2

```

Any ideas?

---

### Post by deadland on 2010-05-06
test

---

### Post by Chunk of Earth on 2010-05-08
I don't have any experience with your particular IR receiver but the one on my Hauppauge card died with Karmic. I think it had something to do with a rewrite of the i2c layer.
I downloaded and tried to build the latest v4l-dvb, too, because there were some updates to the IR code. It looks like that code won't compile, though (at least on my karmic box.) I got the same errors that you show in your v4l-dvb build. If you want v4l-dvb to build you can revert to an earlier changeset just before the new IR code was committed.
```
:~$ cd v4l-dvb         [COLOR=DarkRed]*(or wherever you downloaded v4l-dvb)*[/COLOR]
:~$ hg update -ree9826bc7106
:~$ make distclean
:~$ make menuconfig    [COLOR=DarkRed]*(disable the FireDTV driver if it still causes compile errors)*[/COLOR]
:~$ make               [COLOR=DarkRed]*(make -j3  if you have a dual-core CPU)*[/COLOR]
:~$ sudo make install
```

---

### Post by deadland on 2010-05-10
Sounds good. I will try it! :)

---

### Post by deadland on 2010-05-10
Hi I also found a solution to build the latest v4l-dvb:

[http://ubuntuforums.org/showthread.php?t=1479679](http://ubuntuforums.org/showthread.php?t=1479679)

---

### Post by deadland on 2010-05-11
Nothing works, its frustrating...

I tried it with the latest v4l-dvb and with (hg update -ree9826bc7106). Both no go. I still get the same error:

```
tda9887 2-0043: i2c i/o error: rc == -5 (should be 4)

```

---

