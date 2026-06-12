---
title: "sound settings for WinTV"
date: 2006-12-02
forum: Multimedia &amp; Video
---

### Post by pickarooney on 2006-12-02
I installed a WinTV Express card yesterday, and am running tvtime (no other applicaiton I installed would work with the card for some reason). I'm having trouble getting sound from it though. I've tried all teh possible sound card settings I can think of, but I can only get silence or else a horrible feedback noise. The line-out of the card is connected to teh line-in of the sound card and my speakers to the main output jack. Up to now I've been using the blue line-out jack of my sound card as a rear audio output, but can't figure out how to disable this and revert it to an audio-inport.

---

### Post by pickarooney on 2006-12-02
Not sure the sound bit is working, actually, dmesg|grep bt gives this:

[17179593.164000] bttv: driver version 0.9.16 loaded
[17179593.164000] bttv: using 8 buffers with 2080k (520 pages) each for capture
[17179593.164000] bttv: Bt8xx card found (0).
[17179593.164000] bttv0: Bt878 (rev 17) at 0000:02:00.0, irq: 233, latency: 64, mmio: 0xdfeff000
[17179593.164000] bttv0: detected: Hauppauge WinTV [card=10], PCI subsystem ID is 0070:13eb
[17179593.164000] bttv0: using: Hauppauge (bt878) [card=10,autodetected]
[17179593.164000] bttv0: gpio: en=00000000, out=00000000 in=00ffffdb [init]
[17179593.168000] bttv0: Hauppauge/Voodoo msp34xx: reset line init [5]
[17179593.336000] bttv0: using tuner=38
[17179593.336000] bttv0: i2c: checking for MSP34xx @ 0x80... not found
[17179593.340000] bttv0: i2c: checking for TDA9875 @ 0xb0... not found
[17179593.340000] bttv0: i2c: checking for TDA7432 @ 0x8a... not found
[17179593.368000] bttv0: i2c: checking for TDA9887 @ 0x86... found
[17179593.392000] tda9887 0-0043: chip found @ 0x86 (bt878 #0 [sw])
[17179593.420000] tuner 0-0061: chip found @ 0xc2 (bt878 #0 [sw])
[17179593.448000] bttv0: registered device video0
[17179593.448000] bttv0: registered device vbi0
[17179593.448000] bttv0: registered device radio0
[17179593.448000] bttv0: PLL: 28636363 => 35468950 .. ok
[17179593.640000] bt878: AUDIO driver version 0.0.0 loaded
[17182993.388000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FDSR OCERR*
[17183550.904000] bttv0: OCERR @ 37e0f01c,bits: HSYNC OFLOW RISCI* FDSR OCERR*
[17183566.776000] bttv0: OCERR @ 37e0f01c,bits: HSYNC OFLOW RISCI* FDSR OCERR*
[17183568.352000] bttv0: OCERR @ 37e0f01c,bits: HSYNC OFLOW RISCI* FDSR OCERR*
[17183568.404000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FBUS FDSR OCERR*
[17183568.472000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW OCERR*
[17183568.512000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FBUS FDSR OCERR*
[17183568.580000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW OCERR*
[17183568.616000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FBUS FDSR OCERR*
[17183568.684000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FBUS FDSR OCERR*
[17183568.756000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW OCERR*
[17183568.788000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW OCERR*
[17183568.824000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW OCERR*
[17183568.852000] bttv0: timeout: drop=3 irq=45972/56365, risc=1286203c, bits: HSYNC OFLOW FDSR
[17183568.864000] bttv0: reset, reinitialize
[17183568.864000] bttv0: PLL: 28636363 => 35468950 . ok
[17183571.156000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FDSR OCERR*
[17183577.404000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FDSR OCERR*
[17183578.384000] bttv0: OCERR @ 37e0f01c,bits: HSYNC OFLOW RISCI* FDSR OCERR*
[17183580.660000] bttv0: OCERR @ 37e0f01c,bits: VSYNC HSYNC OFLOW RISCI* FDSR OCERR*
[17183583.460000] bttv0: OCERR @ 37e0f000,bits: HSYNC OFLOW FDSR OCERR*


Info: when I plug the speakers into the TV tuners audio out, the sound is just a constant buzz. In TVTime the video is set to SECAM and I've tried all available audio modes (PAL-BG, PAL-I, PAL-DK)

---

### Post by pickarooney on 2006-12-03
anyone got an idea?

---

### Post by pickarooney on 2006-12-04
> **pickarooney said:**
> anyone got an idea?


updated to ubuntu 6.10 and now there's no picture or sound. D'oh!
Can anyone throw me a bone?

---

### Post by pickarooney on 2006-12-06
I installed ivtv, but that seems to hqve made things worse. I can't even change channels now, let alone see a picture or hear sound. Also, it's become impossible to remove the bttv module to try and reinstall it with different parameters, as **modprobe -r bttv** yields the message *FATAL: Module bttv is in use.*, even after a reboot.

---

### Post by SyL on 2007-01-06
Hi,

i've got the same issue: no sound using TvTime with SECAM video setting.
Does someone know if this is a known incompatibility?

---

### Post by pickarooney on 2007-01-08
Try these two commands:
```

sudo rmmod tda9887
sudo modprobe tda9887 port1=1 port2=0

```

If they work, you'll just need to add the modules to one of the files in /etc/modprobe.d
If not, you might be using a different card.

---

### Post by SyL on 2007-01-10
Thanks mate,
i'll try it as soon as i'm home!

---

### Post by SyL on 2007-01-10
> **pickarooney said:**
> Try these two commands:
```

sudo rmmod tda9887
sudo modprobe tda9887 port1=1 port2=0

```

If they work, you'll just need to add the modules to one of the files in /etc/modprobe.d
If not, you might be using a different card.
Thank you dude,
that's working fine now!

:)

---

