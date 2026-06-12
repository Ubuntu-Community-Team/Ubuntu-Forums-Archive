---
title: "Pinnacle 800i Analog Tuning Problems"
date: 2008-04-13
forum: Multimedia &amp; Video
---

### Post by pops66 on 2008-04-13
I have a Pinnacle 800i card with the xc5000 tuner chip and cx3288 analog demod.  It also has a samsung chip for digital demod.  I am able to tune ATSC channels in mythtv.  The problem that I'm having is with analog (NTSC) channels.  Both Mythtv and tvtime will tune any given channel, but within a second or two it will fade to static and never come back.  Input from S-Video and Composite work fine.

Relavant dmesg output:
```
[   33.741100] cx88/2: cx2388x MPEG-TS Driver Manager version 0.0.6 loaded
[   33.741177] cx88[0]: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58,autodetected]
[   33.741180] cx88[0]: TV tuner type 76, Radio tuner type -1
[   33.750635] cx88/0: cx2388x v4l2 driver version 0.0.6 loaded
[   33.813839] cx2388x alsa driver version 0.0.6 loaded
[   34.061783] tuner' 0-0064: chip found @ 0xc8 (cx88[0])
[   34.062433] xc5000: Successfully identified at address 0x64
[   34.062435] xc5000: Firmware has not been loaded previously
[   34.062438] xc5000: waiting for firmware upload (dvb-fe-xc5000-1.1.fw)...
[   34.143633] nvidia: module license 'NVIDIA' taints kernel.
[   34.438589] xc5000: firmware read 12332 bytes.
[   34.438592] xc5000: firmware upload
[   34.438595] cx88[0]: Calling XC5000 callback
[   39.010561] input: cx88 IR (Pinnacle PCTV HD 800i) as /class/input/input4
[   39.010600] cx88[0]/2: cx2388x 8802 Driver Manager
[   39.010625] cx88[0]/2: found at 0000:02:05.2, rev: 5, irq: 21, latency: 32, mmio: 0xd3000000
[   39.010747] cx88[0]/0: found at 0000:02:05.0, rev: 5, irq: 21, latency: 32, mmio: 0xd1000000
[   39.010795] cx88[0]/0: registered device video0 [v4l2]
[   39.010828] cx88[0]/0: registered device vbi0
[   39.074251] cx88/2: cx2388x dvb driver version 0.0.6 loaded
[   39.074255] cx88/2: registering cx8802 driver, type: dvb access: shared
[   39.074258] cx88[0]/2: subsystem: 11bd:0051, board: Pinnacle PCTV HD 800i [card=58]
[   39.074261] cx88[0]/2: cx2388x based DVB/ATSC card
[   39.126274] xc5000: Successfully identified at address 0x64
[   39.126277] xc5000: Firmware has been loaded previously
[   39.127303] DVB: registering new adapter (cx88[0])
[   39.127307] DVB: registering frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   41.104374] cx88[0]/1: CX88x/0: ALSA support for cx2388x boards

```

This is using latest v4l-dvb code (4-12-2008)  against kernel 2.6.22-14-generic.  

I can't find mention of this problem anywhere, so even if you don't have a fix, it'd be nice to know if other people have had this same issue.  My best guess would be an issue with the xc5000, but it works fine for DVB so that doesn't really make sense.

---

### Post by jmore9 on 2008-04-16
Hello ! 

You should go to lauchpad.net and try ME TV.  It does a good job with the channels.conf with the Pinnacle 800i

---

### Post by pops66 on 2008-04-18
It's not the channels.conf that I'm having a problem with.  This card will tune to, say, channel 3, display what is playing and then quickly fade to static as though the "dial" kept turning.  Just for spite I did try ME.TV and it works for digital stations!  But it doesn't help at all for the analog ones.  Thanks for the reply!  Anything else?

---

### Post by xc3RnbFO8P on 2008-04-19
Try this:
[http://ubuntuforums.org/showpost.php?p=4194527&postcount=11]("http://ubuntuforums.org/showpost.php?p=4194527&postcount=11")

---

### Post by pops66 on 2008-04-19
I have done that.  The DVB wouldn't work without it.  The only difference is that I made the drivers first and then extracted the firmware.  Do you think that would make any difference?  Thanks for the reply!

---

### Post by xc3RnbFO8P on 2008-04-20
No it wont,
someone has got analog to work
by using Mythtv according to this tread:
[http://ubuntuforums.org/showthread.php?t=676445&page=2]("http://ubuntuforums.org/showthread.php?t=676445&page=2")

---

### Post by pops66 on 2008-04-21
I know, it seems everyone can get analog to work on this card.  I've installed three different ones on three different systems with the same results.  At this point I'm going to start looking for a different card.  Any suggestions for so-called "hybrid" cards?  And this is a question for mythtv forums, I know, but does anybody know a way to make mythtv show digital and analog stations intermixed during playback (ie using ch. up and ch. down, not just in the guide).  Any other help on that pinnacle card also appreciated.

---

### Post by jnthornh on 2008-06-10
I know this is an old thread, but I wanted to mention that I've experienced the exact same issue (QAM/ATSC works, but NTSC seems to tune initially then quickly fades to static) with my Pinnacle 800i.  I'm running gentoo with gentoo sources 2.6.24-r8 and the latest (as of today) v4l-dvb drivers.

I had suspected hardware until I found this post, which mentions trying multiple cards.  So, unless there's a bad batch floating around, that seems unlikely.

Considering we're using different kernels with different distributions, I think our problem must be either in the firmware files we're using or the version of v4l-dvb we're using.  I'm going to try using an older revision and see if I have any luck - perhaps a newer revision introduced this as a bug.

---

