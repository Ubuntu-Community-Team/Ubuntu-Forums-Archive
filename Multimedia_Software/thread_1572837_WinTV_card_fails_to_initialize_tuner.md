---
title: "WinTV card fails to initialize tuner"
date: 2010-09-11
forum: Multimedia Software
---

### Post by dwilde1 on 2010-09-11
I'm running 10.04 64-bit with all stable and pre-release upgrades enabled in a Dell 4-core Inspiron with 8 GB of memory.

I just bought a Hauppage WinTV-HVR 1600 and it's detected in the boot process and all firmware is loaded, but then it goes bonkers and spews 

[   24.421795] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-dig.fw
[   24.612289] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   24.632510] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   24.633989] tuner 2-0061: tuner type not set
[   24.634935] tuner 2-0061: tuner type not set
 . . .
[13127.813551] tuner 2-0061: tuner type not set

over and over again. All the info on the Hauppage site and LinuxTV is very obsolete.

MythTV initializes, but can't find any channels on either the analog or digital streams.

Thanks in advance! :D

---

### Post by slighted on 2010-09-12
dwilde1, you can try replacing the firmware:

```
sudo apt-get install linux-firmware-nonfree
```

I believe I had success running this route, although I did end up replacing it with a PVR-150 due to audio issues... If I remember correctly.

Ted

---

### Post by dwilde1 on 2010-09-12
The dmesg results are somewhat different, but it still fails to identify the tuner and ends up with the same message repeated many times. I don't remember seeing the segfault (@ 443) before.

[   24.456030] Linux video capture interface: v2.00
[   24.476862] cx18:  Start initialization, version 1.2.0
[   24.476904] cx18-0: Initializing card 0
[   24.476906] cx18-0: Autodetected Hauppauge card
[   24.477035] cx18 0000:02:01.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   24.477044] cx18-0: Unreasonably low latency timer, setting to 64 (was 2)
[   24.478687] cx18-0: cx23418 revision 01010000 (B)
...
[   24.683158] tveeprom 1-0050: Hauppauge model 74041, rev C6G8, serial# 7241133
[   24.683161] tveeprom 1-0050: MAC address is 00-0D-FE-6E-7D-AD
[   24.683164] tveeprom 1-0050: tuner model is unknown (idx 168, type 4)
[   24.683166] tveeprom 1-0050: TV standards NTSC(M) (eeprom 0x08)
[   24.683168] tveeprom 1-0050: audio processor is CX23418 (idx 38)
[   24.683170] tveeprom 1-0050: decoder processor is CX23418 (idx 31)
[   24.683173] tveeprom 1-0050: has no radio, has IR receiver, has IR transmitter
[   24.683175] cx18-0: Autodetected Hauppauge HVR-1600
[   24.683176] cx18-0: tveeprom cannot autodetect tuner!
[   24.683179] cx18-0: Simultaneous Digital and Analog TV capture supported
[   24.775612] IRQ 16/cx18-0: IRQF_DISABLED is not guaranteed on shared IRQs
[   24.786481] tuner 2-0043: chip found @ 0x86 (cx18 i2c driver #0-1)
...
[   24.791976] tda9887 2-0043: creating new instance
[   24.791979] tda9887 2-0043: tda988[5/6/7] found
[   24.794131] tuner 2-0061: chip found @ 0xc2 (cx18 i2c driver #0-1)
[   24.795807] cs5345 1-004c: chip found @ 0x98 (cx18 i2c driver #0-0)
[   24.802455] cx18-0: Registered device video0 for encoder MPEG (64 x 32 kB)
[   24.802456] DVB: registering new adapter (cx18)
[   24.859601] MXL5005S: Attached at address 0x63
[   24.859602] DVB: registering adapter 0 frontend 0 (Samsung S5H1409 QAM/8VSB Frontend)...
[   24.859690] cx18-0: DVB Frontend registered
[   24.859690] cx18-0: Registered DVB adapter0 for TS (32 x 32 kB)
[   24.859717] cx18-0: Registered device video32 for encoder YUV (16 x 128 kB)
[   24.859742] cx18-0: Registered device vbi0 for encoder VBI (20 x 51984 bytes)
[   24.859765] cx18-0: Registered device video24 for encoder PCM audio (256 x 4 kB)
[   24.859768] cx18-0: Initialized card: Hauppauge HVR-1600
[   24.859790] cx18:  End initialization
[   24.862550] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-cpu.fw
[   24.986550] cx18-0: loaded v4l-cx23418-cpu.fw firmware (158332 bytes)
[   25.011985] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-apu.fw
[   25.110100] cx18-0: loaded v4l-cx23418-apu.fw firmware V00120000 (141200 bytes)
[   25.116278] cx18-0: FW version: 0.0.74.0 (Release 2007/03/12)
[   25.333837] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-cpu.fw
[   25.451526] e1000e 0000:00:19.0: irq 25 for MSI/MSI-X
[   25.472110] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-apu.fw
[   25.511360] e1000e 0000:00:19.0: irq 25 for MSI/MSI-X
...
[   25.792959] cx18 0000:02:01.0: firmware: requesting v4l-cx23418-dig.fw
[   26.061280] cx18-0 843: loaded v4l-cx23418-dig.fw firmware (16382 bytes)
[   26.080542] cx18-0 843: verified load of v4l-cx23418-dig.fw firmware (16382 bytes)
[   26.081970] tuner 2-0061: tuner type not set
[   26.082885] tuner 2-0061: tuner type not set
...
[  443.212093] __ratelimit: 21 callbacks suppressed
[  443.212099] tvtime[2865]: segfault at 840 ip 0000000000407400 sp 00007fffec259268 error 4 in tvtime[400000+7e000]
[  466.083191] tuner 2-0061: tuner type not set
[  779.391444] tuner 2-0061: tuner type not set
[  779.421578] tuner 2-0061: tuner type not set
[  779.448521] tuner 2-0061: tuner type not set
[  779.475385] tuner 2-0061: tuner type not set
...

---

### Post by slighted on 2010-09-12
You can try setting the tuner manually:

```
echo "options cx18 tuner=62" | sudo tee -a /etc/modprobe.d/hvr1600.conf
```

Reboot and cross fingers... :D

---

### Post by dwilde1 on 2010-09-15
Still no joy afa working although the 'not found' messages are gone. This is a good step forward! 

Is there a doc for what I can tweak in that conf file, or a log file, or any way I can see if there's data coming in?

---

### Post by slighted on 2010-09-16
I haven't found a one-stop for hvr-1600 options, I will post back if I run across anything though... By the way, what is the model and make of your graphics adapter? Does it happen to be an Nvidia chipset? :-k

---

### Post by dwilde1 on 2010-09-17
It's a cheapo Dell  Inspiron with, I think, and Intel i915. I spent my money on a 4-core and 8 gigs >8^D

---

### Post by majorw00dy on 2010-09-23
I would recommend you use```
sudo modprobe cx18 tuner=x
``` where x is 1 thru 84. Remember to stop mythtv-backend ```
sudo stop mythtv-backend
``` and before you do the modprobe you need to remove it using ```
sudo rmmod cx18
```

Take a look at lglenn post [http://ubuntuforums.org/showthread.php?t=1498620&page=2]("http://ubuntuforums.org/showthread.php?t=1498620&page=2") he has a nice little script that will check all the tuners, but in my case the signal strength was 0 and i was still able to view the channels using ```
ivtv-tune -c 3
``` then view the output using ```
vlc /dev/video0
```

UPDATE:
Once you find the tuner that works for you, you want to make the change permanent. Add 'options cx18 tuner=xx' to /etc/modprobe.d/options.conf file. If it doesn't exist just create it as root.

---

