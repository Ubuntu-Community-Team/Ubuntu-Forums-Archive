---
title: "ivtv only gives me static"
date: 2006-07-30
forum: Multimedia &amp; Video
---

### Post by jaymode on 2006-07-30
I have been following this guide: [http://hyams.webhop.net/mythtv/myth_ubuntu.html](http://hyams.webhop.net/mythtv/myth_ubuntu.html)

and a post about dapper and myth tv. Everything has gone fine until the IVTV driver. I have an adaptec avc-2410 and I know the card works as I can use it in windows without a problem and gentoo would let me capture video before I got frustrated with it.

I know about this also:
[http://www.ivtvdriver.org/index.php/Adaptec_AVC-2410](http://www.ivtvdriver.org/index.php/Adaptec_AVC-2410)

I am using the latest ivtv for kernel 2.6.15 and have followed the howto guide for Ubuntu. I only differed in the firmware. I used the recommended firmware from ivtvdriver.org.

Here is my dmesg:
```

[17179589.348000] ivtv:  ==================== START INIT IVTV ====================
[17179589.348000] ivtv:  version 0.4.6 (tagged release) loading
[17179589.348000] ivtv:  Linux version: 2.6.15-26-386 preempt 486 gcc-4.0
[17179589.348000] ivtv:  In case of problems please include the debug info between
[17179589.348000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179589.348000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179589.348000] ivtv0: Autodetected Adaptec VIDEOH! AVC-2410 card (cx23416 based)
[17179589.348000] ACPI: PCI Interrupt 0000:00:0b.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179589.356000] tuner (ivtv): chip found at addr 0xc0 i2c-bus ivtv i2c driver #0
[17179589.356000] All bytes are equal. It is not a TEA5767
[17179589.356000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=60]
[17179589.468000] tuner (ivtv): chip found at addr 0xd6 i2c-bus ivtv i2c driver #0
[17179589.468000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=6b]
[17179589.528000] saa7115 1-0021: saa7115 found @ 0x42 (ivtv i2c driver #0)
[17179589.652000] ivtv0: i2c attach to card #0 ok [client=saa7115, addr=21]
[17179589.716000] cs53l32a 1-0011: chip found @ 0x22 (ivtv i2c driver #0)
[17179589.732000] ivtv0: i2c attach to card #0 ok [client=cs53l32a, addr=11]
[17179589.748000] tda9887 1-0043: (ivtv) chip found @ 0x86 (ivtv i2c driver #0)
[17179589.748000] ivtv0: i2c attach to card #0 ok [client=tda9887, addr=43]
[17179589.760000] ivtv0: Could not detect tuner standard, defaulting to NTSC.
[17179589.760000] ivtv0: Detected a TEA5767 radio tuner. Enabling radio support.
[17179589.872000] input: PC Speaker as /class/input/input3
[17179590.152000] Floppy drive(s): fd0 is 1.44M
[17179590.156000] parport: PnPBIOS parport detected.
[17179590.156000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179590.224000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKF] -> GSI 11 (level, low) -> IRQ 11
[17179590.368000] FDC 0 is a post-1991 82077
[17179590.468000] ts: Compaq touchscreen protocol output
[17179590.536000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179590.740000] eth0: Media Link Off
[17179590.752000] ivtv0: Encoder revision: 0x02050032
[17179590.752000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179590.752000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179590.752000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179590.752000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179590.752000] ivtv0: Create encoder radio stream
[17179590.752000] tuner: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F)) by ivtv i2c driver #0
[17179590.792000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40086d11!
[17179590.792000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179590.792000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179590.792000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40085618!
[17179590.832000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179590.832000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179590.836000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x402c5639!
[17179590.836000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x80287610!
[17179590.836000] ivtv0 warning: i2c client addr: 0x40 not found for command 0x40287611!
[17179590.836000] ivtv0: Initialized Adaptec VIDEOH! AVC-2410, card #0
[17179590.836000] ivtv:  ====================  END INIT IVTV  ====================

```

I tried tuning the channel but that did not help and I know the signal is good.

Here are somethings I tried that might be useful:
```

jmodi@mythbox:~$ ivtvctl -R
ioctl VIDIOC_G_FREQUENCY ok
Frequency = 1076
jmodi@mythbox:~$ ivtv-tune -c5 -d/dev/video0
/dev/video0: 77.250 MHz
jmodi@mythbox:~$ ivtvctl -R
ioctl VIDIOC_G_FREQUENCY ok
Frequency = 1236
jmodi@mythbox:~$ ivtv-tune -c5 -d/dev/video0
/dev/video0: 77.250 MHz
jmodi@mythbox:~$ cat /dev/video0 > Desktop/out2.mpg

jmodi@mythbox:~$ ivtvctl -I
check SAA7115 input signal
ioctl: Input detect failed (cannot read SAA regs)
ioctl: Input detect failed (cannot read SAA regs)
jmodi@mythbox:~$ sudo ivtvctl -I
check SAA7115 input signal
ioctl: Input detect failed (cannot read SAA regs)
ioctl: Input detect failed (cannot read SAA regs)

```

Let me know what else I should post in order for you to help me.

This is a P4 2.0 GHZ
768 mb pc133
SIS M650 Mobo
Adaptec AVC 2410
Ubuntu 6.06

---

### Post by jaymode on 2006-08-05
I think I may have found part of the error looking through dmesg:

[17180268.084000] tuner: no version for "struct_module" found: kernel tainted. 

Any ideas?

---

### Post by wjston on 2006-11-25
jaymode

Are you running NTSC of PAL in the setup for your Hauppauge card? The reason I ask is I saw this in your dmesg log:
   ivtv0: Could not detect tuner standard, defaulting to NTSC

If your signal is PAL, change your setting in the MythTV Setup screen and make sure the other settings reflect the change.

It may even be advisable to delete your card in setup and install it new to remove any old settings.Then complete the rest of the setup.

Good Luck

---

