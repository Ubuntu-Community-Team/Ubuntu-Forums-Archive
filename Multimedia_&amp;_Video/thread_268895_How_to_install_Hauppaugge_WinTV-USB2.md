---
title: "How to install Hauppaugge WinTV-USB2"
date: 2006-09-30
forum: Multimedia &amp; Video
---

### Post by brottman on 2006-09-30
I searched the forums far and wide, scanned through many sources, but alas, I don't know what to do. Can someone please explain in lay terms how to install drivers for a Hauppaugge WinTV-USB2 tv tuner? I would be forever grateful :) I am trying to use my tuner with the TVtime application.

---

### Post by brottman on 2006-10-02
Bump.

---

### Post by dixonstalbert on 2006-10-02
hi brottman

I updated my post here  [http://www.ubuntuforums.org/showthread.php?p=906718#post906718]("http://www.ubuntuforums.org/showthread.php?p=906718#post906718")

that has install instructions for the wintvusb2

---

### Post by gmc on 2006-10-08
> **brottman said:**
> I searched the forums far and wide, scanned through many sources, but alas, I don't know what to do. Can someone please explain in lay terms how to install drivers for a Hauppaugge WinTV-USB2 tv tuner? I would be forever grateful :) I am trying to use my tuner with the TVtime application.

Check out [this page]("http://pvrusb2.dax.nu/"). So far I've been able to successfully load the drivers to the point that the pvr is recognized by Ubuntu/Linux.

```

[17179587.440000] tuner 0-0061: chip found @ 0xc2 (pvrusb2_a)
[17179587.480000] tda9887 0-0043: chip found @ 0x86 (pvrusb2_a)
[17179587.504000] tveeprom 0-0050: Hauppauge model 29032, rev D2A3, serial# 8206665
[17179587.504000] tveeprom 0-0050: tuner model is TCL MFNM05-4 (idx 103, type 43)
[17179587.504000] tveeprom 0-0050: TV standards NTSC(M) (eeprom 0x08)
[17179587.504000] tveeprom 0-0050: audio processor is MSP3445 (idx 12)
[17179587.504000] tveeprom 0-0050: decoder processor is SAA7115 (idx 19)
[17179587.504000] tveeprom 0-0050: has radio, has IR remote
[17179587.532000] tuner 0-0061: type set to 43 (Philips NTSC MK3 (FM1236MK3 or FM1236/F))
[17179587.644000] msp3400 0-0040: MSP3445G-B8 rev1 = 0x0207 rev2 = 0x2d48
[17179587.644000] msp3400 0-0040: Audio:    volume 65535
[17179587.644000] msp3400 0-0040: Audio:    balance 0 bass 0 treble 0 loudness off
[17179587.644000] msp3400 0-0040: Standard: autodetect start (mono)
[17179587.644000] msp3400 0-0040: Audmode:  0x0001
[17179587.644000] msp3400 0-0040: Routing:  0x00000000 (input) 0x00000044 (output)
[17179587.644000] msp3400 0-0040: ACB:      0x0c00
[17179587.644000] saa7115 0-0021: Audio frequency: 48000 Hz
[17179587.648000] saa7115 0-0021: Input:           Composite 4
[17179587.648000] saa7115 0-0021: Video signal:    bad
[17179587.648000] saa7115 0-0021: Frequency:       60 Hz
[17179587.648000] saa7115 0-0021: Detected format: BW/No color
[17179587.648000] tuner 0-0061: Tuner mode:      analog TV
[17179587.648000] tuner 0-0061: Frequency:       175.25 MHz
[17179587.648000] tuner 0-0061: Standard:        0x00001000
[17179587.648000] tda9887 0-0043: Data bytes: b=0x14 c=0x30 e=0x44
[17179587.648000] pvrusb2: Device initialization completed successfully.
[17179587.648000] pvrusb2: registered device video0 [mpeg]

```

However I'm still trying to get some sort of useful functionality out of it.

G.

---

### Post by anaconda on 2006-10-29
> **brottman said:**
> I searched the forums far and wide, scanned through many sources, but alas, I don't know what to do. Can someone please explain in lay terms how to install drivers for a Hauppaugge WinTV-USB2 tv tuner? I would be forever grateful :) I am trying to use my tuner with the TVtime application.

here is detailed instructions of how to get your wintv nova-t usb2 working in ubuntu.. (really easy.)
[http://www.ubuntuforums.org/showthread.php?t=274014&highlight=wintv](http://www.ubuntuforums.org/showthread.php?t=274014&highlight=wintv)

---

