---
title: "Getting an AverMedia Analog M104 to work?"
date: 2006-09-02
forum: Multimedia &amp; Video
---

### Post by rapha on 2006-09-02
Hi all,

my recently purchased Bonobo laptop from [http://www.system76.com]("http://www.system76.com") (works great, except for the camera and TV card) has an [AverMedia Analog M104]("http://www.avermedia.com/cgi-bin/products_odm_M104.asp") for TV and radio. I've been trying to get it to work for some time now and thought maybe someone here might just know something about it.

So far I got the ivtv drivers loaded just fine and *mplayer /dev/video0* displays a perfectly black picture. What does not work is tuning (either through *ivtv-tune* or *scantv*, no matter whether the original antenna or cable is attached). Also, there's no */dev/radio*, which prevents me from even trying out *gnome-radio*.

As far as diagnostics go, I can only provide *dmesg* output from the ivtv driver. No idea what else would be useful/necessary.

```
[17179591.440000] ivtv:  ==================== START INIT IVTV ====================
[17179591.440000] ivtv:  version 0.4.6 (tagged release) loading
[17179591.440000] ivtv:  Linux version: 2.6.15-26-686 SMP preempt 686 gcc-4.0
[17179591.440000] ivtv:  In case of problems please include the debug info between
[17179591.440000] ivtv:  the START INIT IVTV and END INIT IVTV lines, along with
[17179591.440000] ivtv:  any module options, when mailing the ivtv-users mailinglist.
[17179591.628000] ivtv0: Unknown card: vendor/device: 4444/0016
[17179591.628000] ivtv0:               subsystem vendor/device: 1461/c136
[17179591.628000] ivtv0:               cx23416 based
[17179591.628000] ivtv0: Defaulting to WinTV PVR 150 card
[17179591.628000] ivtv0: Please mail the vendor/device and subsystem vendor/device IDs and what kind of
[17179591.628000] ivtv0: card you have to the ivtv-devel mailinglist (www.ivtvdriver.org)
[17179591.628000] ivtv0: Prefix your subject line with [UNKNOWN CARD].
[17179591.740000] ivtv0 warning: i2c client addr: 0x50 not found for command 0x0!
[17179591.740000] ivtv0: Error -19 reading Hauppauge eeprom.
[17179591.740000] ivtv0: Possible causes: the tveeprom module was not loaded, or
[17179591.740000] ivtv0: the eeprom kernel module was loaded before the tveeprom module.
[17179591.780000] tuner (ivtv): chip found at addr 0xc2 i2c-bus ivtv i2c driver #0
[17179591.780000] ivtv0: i2c attach to card #0 ok [client=(tuner unset), addr=61]
[17179592.004000] cx25840 0-0044: ivtv driver
[17179592.004000] cx25840 0-0044: cx25843-23 found @ 0x88 (ivtv i2c driver #0)
[17179596.504000] ivtv0: i2c attach to card #0 ok [client=cx25840, addr=44]
[17179596.612000] ivtv0: Could not detect tuner standard, defaulting to NTSC.
[17179597.268000] ivtv0: loaded v4l-cx2341x-enc.fw firmware (262144 bytes)
[17179597.488000] ivtv0: Encoder revision: 0x02050032
[17179597.488000] ivtv0: Allocate DMA encoder MPEG stream: 128 x 32768 buffers (4096KB total)
[17179597.488000] ivtv0: Allocate DMA encoder YUV stream: 194 x 10800 buffers (2048KB total)
[17179597.488000] ivtv0: Allocate DMA encoder VBI stream: 120 x 17472 buffers (2048KB total)
[17179597.488000] ivtv0: Allocate DMA encoder PCM audio stream: 455 x 4608 buffers (2048KB total)
[17179597.528000] ivtv0 warning: i2c client addr: 0x1b not found for command 0x40046d11!
[17179597.576000] ivtv0 warning: i2c client addr: 0x1b not found for command 0x402c5639!
[17179597.588000] ivtv0: Initialized WinTV PVR 150, card #0
[17179597.740000] ivtv:  ====================  END INIT IVTV  ====================
```

Any pointers, however small or crazy would be greatly appreciatedd :-)

-- Raphael

---

