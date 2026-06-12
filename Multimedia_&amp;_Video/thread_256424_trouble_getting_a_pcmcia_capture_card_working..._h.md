---
title: "trouble getting a pcmcia capture card working... help?"
date: 2006-09-13
forum: Multimedia &amp; Video
---

### Post by 0okami on 2006-09-13
I ordered a PCMCIA capture card off ebay and its prooving a little problematic to set up. Details:
 
EasyTV Card Bus
Model: p34 cardbus
---barcode----
p34cardbus0605e4678

---barcode---
T08HYF 060701035

(website: [http://szforwardvideo.en.ec21.com/offerdetail.html?offerId=OF0001028427](http://szforwardvideo.en.ec21.com/offerdetail.html?offerId=OF0001028427) )

lspci -v -v
```
0000:07:00.0 Multimedia controller: Philips Semiconductors SAA7134 Video Broadcast Decoder (rev 01)
        Subsystem: Unknown device 0919:2003
        Control: I/O- Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 64 (2000ns min, 8000ns max)
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at f6000000 (32-bit, non-prefetchable) [size=1K]
        Capabilities: <available only to root>

```



dmesg | grep saa7
```
ookami@inspiron:~$ dmesg | grep saa7134
[17179596.892000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 0, mmio: 0xf6000000
[17179596.892000] saa7134[0]: subsystem: 0919:2003, board: UNKNOWN/GENERIC [card=0,autodetected]
[17179596.892000] saa7134[0]: board init: gpio is 0
[17179597.028000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17179597.028000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.028000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.028000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.028000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.028000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.028000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.028000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179597.028000] saa7134[0]: registered device video0 [v4l2]
[17179597.028000] saa7134[0]: registered device vbi0
[17179597.052000] saa7134 ALSA driver for DMA sound loaded
[17179597.052000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17179820.704000] saa7134 ALSA driver for DMA sound unloaded
[17179915.128000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 64, mmio: 0xf6000000
[17179915.128000] saa7134[0]: subsystem: 0919:2003, board: AVACS SmartTV [card=32,insmod option]
[17179915.128000] saa7134[0]: board init: gpio is 0
[17179915.132000] input: saa7134 IR (AVACS SmartTV) as /class/input/input4
[17179915.336000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17179915.336000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17179915.336000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179915.336000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179915.336000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179915.336000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179915.336000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179915.336000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17179915.456000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17179915.460000] saa7134[0]: registered device video0 [v4l2]
[17179915.460000] saa7134[0]: registered device vbi0
[17179915.464000] saa7134[0]: registered device radio0
[17179915.624000] saa7134 ALSA driver for DMA sound loaded
[17179915.628000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17179961.928000] saa7134 ALSA driver for DMA sound unloaded
[17180233.848000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 64, mmio: 0xf6000000
[17180233.848000] saa7134[0]: subsystem: 0919:2003, board: AVACS SmartTV [card=32,insmod option]
[17180233.848000] saa7134[0]: board init: gpio is 0
[17180233.908000] input: saa7134 IR (AVACS SmartTV) as /class/input/input5
[17180234.188000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17180234.220000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17180234.220000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17180234.220000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180234.220000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180234.220000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180234.220000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180234.220000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180234.220000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180234.264000] saa7134[0]: registered device video0 [v4l2]
[17180234.264000] saa7134[0]: registered device vbi0
[17180234.264000] saa7134[0]: registered device radio0
[17180234.292000] saa7134 ALSA driver for DMA sound loaded
[17180234.292000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17180253.200000] saa7134 ALSA driver for DMA sound unloaded
[17180262.108000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 64, mmio: 0xf6000000
[17180262.112000] saa7134[0]: subsystem: 0919:2003, board: UNKNOWN/GENERIC [card=0,autodetected]
[17180262.112000] saa7134[0]: board init: gpio is 0
[17180262.288000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17180262.320000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17180262.320000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17180262.320000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180262.320000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180262.320000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180262.320000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180262.320000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180262.320000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180262.324000] saa7134[0]: registered device video0 [v4l2]
[17180262.324000] saa7134[0]: registered device vbi0
[17180262.348000] saa7134 ALSA driver for DMA sound loaded
[17180262.348000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17180281.392000] saa7134 ALSA driver for DMA sound unloaded
[17180295.216000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 64, mmio: 0xf6000000
[17180295.216000] saa7134[0]: subsystem: 0919:2003, board: Proteus Pro [philips reference design] [card=1,insmod option]
[17180295.216000] saa7134[0]: board init: gpio is 0
[17180295.396000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17180295.428000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17180295.428000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17180295.428000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180295.428000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180295.428000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180295.428000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180295.428000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180295.428000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180295.464000] saa7134[0]: registered device video0 [v4l2]
[17180295.464000] saa7134[0]: registered device vbi0
[17180295.468000] saa7134[0]: registered device radio0
[17180295.620000] saa7134 ALSA driver for DMA sound loaded
[17180295.620000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17180505.892000] saa7134 ALSA driver for DMA sound unloaded
[17180515.576000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 64, mmio: 0xf6000000
[17180515.576000] saa7134[0]: subsystem: 0919:2003, board: UNKNOWN/GENERIC [card=0,autodetected]
[17180515.576000] saa7134[0]: board init: gpio is 0
[17180515.756000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17180515.792000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17180515.792000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17180515.792000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180515.792000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180515.792000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180515.792000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180515.792000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180515.792000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180515.796000] saa7134[0]: registered device video0 [v4l2]
[17180515.796000] saa7134[0]: registered device vbi0
[17180515.908000] saa7134 ALSA driver for DMA sound loaded
[17180515.908000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17180631.196000] saa7134 ALSA driver for DMA sound unloaded
[17180638.572000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 0, mmio: 0xf6000000
[17180638.572000] saa7134[0]: subsystem: 0919:2003, board: UNKNOWN/GENERIC [card=0,autodetected]
[17180638.576000] saa7134[0]: board init: gpio is 0
[17180638.752000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17180638.788000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17180638.788000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17180638.788000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180638.788000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180638.788000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180638.788000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180638.788000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180638.788000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180638.792000] saa7134[0]: registered device video0 [v4l2]
[17180638.792000] saa7134[0]: registered device vbi0
[17180638.816000] saa7134 ALSA driver for DMA sound loaded
[17180638.816000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17180669.984000] saa7134 ALSA driver for DMA sound unloaded
[17180676.184000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 64, mmio: 0xf6000000
[17180676.184000] saa7134[0]: subsystem: 0919:2003, board: Sedna/MuchTV PC TV Cardbus TV/Radio (ITO25 Rev:2B) [card=79,insmod option]
[17180676.188000] saa7134[0]: board init: gpio is 0
[17180676.248000] input: saa7134 IR (Sedna/MuchTV PC TV  as /class/input/input6
[17180676.524000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17180676.708000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17180676.708000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17180676.708000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180676.708000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180676.708000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180676.708000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180676.708000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180676.708000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17180679.164000] saa7134[0]: registered device video0 [v4l2]
[17180679.164000] saa7134[0]: registered device vbi0
[17180679.168000] saa7134[0]: registered device radio0
[17180679.328000] saa7134 ALSA driver for DMA sound loaded
[17180679.328000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17180794.472000] saa7134 ALSA driver for DMA sound unloaded
[17181192.404000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 0, mmio: 0xf6000000
[17181192.404000] saa7134[0]: subsystem: 0919:2003, board: UNKNOWN/GENERIC [card=0,autodetected]
[17181192.404000] saa7134[0]: board init: gpio is 0
[17181192.580000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17181192.612000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17181192.612000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17181192.612000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181192.612000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181192.612000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181192.612000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181192.612000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181192.612000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181192.616000] saa7134[0]: registered device video0 [v4l2]
[17181192.616000] saa7134[0]: registered device vbi0
[17181192.640000] saa7134 ALSA driver for DMA sound loaded
[17181192.640000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17181399.480000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 0, mmio: 0xf6000000
[17181399.480000] saa7134[0]: subsystem: 0919:2003, board: UNKNOWN/GENERIC [card=0,autodetected]
[17181399.480000] saa7134[0]: board init: gpio is 0
[17181399.656000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17181399.688000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17181399.688000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17181399.688000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181399.688000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181399.688000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181399.688000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181399.688000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181399.688000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181399.688000] saa7134[0]: registered device video0 [v4l2]
[17181399.688000] saa7134[0]: registered device vbi0
[17181399.688000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
[17181404.956000] saa7134 ALSA driver for DMA sound unloaded
[17181429.856000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 11, latency: 64, mmio: 0xf6000000
[17181429.856000] saa7134[0]: subsystem: 0919:2003, board: UNKNOWN/GENERIC [card=0,autodetected]
[17181429.856000] saa7134[0]: board init: gpio is 0
[17181430.032000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[17181430.064000] saa7134[0]: i2c eeprom 00: 19 09 03 20 08 20 1c 55 43 43 a9 1c 55 43 43 a9
[17181430.064000] saa7134[0]: i2c eeprom 10: ff ff 00 00 ff ff ff ff ff ff ff ff ff ff ff ff
[17181430.064000] saa7134[0]: i2c eeprom 20: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181430.064000] saa7134[0]: i2c eeprom 30: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181430.064000] saa7134[0]: i2c eeprom 40: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181430.064000] saa7134[0]: i2c eeprom 50: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181430.064000] saa7134[0]: i2c eeprom 60: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181430.064000] saa7134[0]: i2c eeprom 70: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[17181430.068000] saa7134[0]: registered device video0 [v4l2]
[17181430.068000] saa7134[0]: registered device vbi0
[17181430.096000] saa7134 ALSA driver for DMA sound loaded
[17181430.096000] saa7134[0]/alsa: saa7134[0] at 0xf6000000 irq 11 registered as card -1
ookami@inspiron:~$

```

I tried following some instructions i found online [http://gentoo-wiki.com/HARDWARE_saa7134]("http://gentoo-wiki.com/HARDWARE_saa7134")  which said to: 
sudo rmmod saa7134
and to 
sudo modprobe saa7134 card=xx tuner=yy

...but im not having much luck.  yet....  


I thought maybe i'd throw this post out in the air and see what others have to say?

---

### Post by 0okami on 2006-09-13
After further investigating, the pcmcia card information is:

Card: SinoVideo PCI2390 Proteus (7134)
Tuner: SinoVideo (tda8275) 
^ as reported by windows device manager. (i love dual booting!)

With that information, I found that the settings should be card=1 tuner=54 BUT... As odd as it seems, in doing so, composite1 refuses to work. 

This setting did the trick... 
```
sudo modprobe saa7134 card=81 tuner=54 oss=1
```


still no audio however...

---

### Post by Crayoneater on 2006-09-13
you need to use sox to get sound...at least that is one option...

so install sox: 
sudo apt-get install sox

then do this: 
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp

you may have to do something like this when you bring up the module:
modprobe saa7134 card=xx tuner=xx oss=1

what i did was make a script that i can run everytime i put in my capture card and it sets everything up nicely....i created a file called tvcard.sh and inserted the following lines of text:

#/bin/sh
rmmod saa7134-oss
rmmod saa7134-dvb
rmmod saa7134
modprobe saa7134 card=78 tuner=54 oss=1
modprobe saa7134-oss
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp



after i run that script, i can simply open whatever i'm using for capturing ...mplayer, tvtime, etc...

i hope this helps you.....

---

### Post by 0okami on 2006-09-13
> **Crayoneater said:**
> you need to use sox to get sound...at least that is one option...

so install sox: 
sudo apt-get install sox

then do this: 
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
.....

It appears I already have sox installed...
```
ookami@inspiron:~$ sudo apt-get install sox
Reading package lists... Done
Building dependency tree... Done
sox is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


when trying the command sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp i get this error:  
```

ookami@inspiron:~$ sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
sox: Can't open input file '/dev/dsp1': No such file or directory
ookami@inspiron:~$
```



err... after further tinkering... now im getting:
```
ookami@inspiron:~$ sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
sox: Can't open output file '/dev/dsp': Device or resource busy

```

*puzzled*

I tried running this: ```
#!/bin/sh
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute

```

and i get this: 
```
Running tvtime 1.0.1.
Reading configuration from /etc/tvtime/tvtime.xml
Reading configuration from /home/ookami/.tvtime/tvtime.xml
sox: Can't open output file '/dev/dsp': Device or resource busy

```

still no audio...

---

### Post by Crayoneater on 2006-09-13
it is saying that the device or resource is busy which could mean that another program is using the sound card...make sure all of your media players are closed or anything else that could be using your sound card...

---

### Post by 0okami on 2006-09-14
> **Crayoneater said:**
> it is saying that the device or resource is busy which could mean that another program is using the sound card...make sure all of your media players are closed or anything else that could be using your sound card...

True, but why would it say that when there is nothing playing?

---

### Post by 0okami on 2006-09-14
EasyTV Card Bus
Model: p34 cardbus
Barcode: p34cardbus0605e4678
Barcode: T08HYF 060701035

It's working! it's working! 
the trick was to killall esd. ^_^ 
So here's a run down of what has been done: 

This removes the module which is not auto configured properly
```
sudo rmmod saa7134_alsa saa7134
```

this loads the modules configured properly for this card
```
sudo modprobe saa7134 card=81 tuner=54 oss=1
```

kill esd... not sure if its required, but it worked for me when dsp was busy: 
```
killall esd
```

Run this sox command: 
```
sox -r 32000 -w -t ossdsp /dev/dsp1 -t ossdsp /dev/dsp
```

and you should see this which remains active in a terminal:
```

Input Filename : /dev/dsp1
Sample Size    : 16-bits
Sample Encoding: signed (2's complement)
Channels       : 1
Sample Rate    : 32000

```

*quickly!!* start a new terminal and type 
```
aoss tvtime
``` 

That should be all it takes to get audio working with *this* pcmcia video capture / tuner card.

Now the problem is, these changes to saa7134 are lost on reboot... so to fix that, do this:
```
sudo gedit /etc/modprobe.conf
```

Paste this line into the modprobe.conf (mine was empty)
```
 options saa7134 card=81 tuner=54 oss=1
```
Now every time your machine reboots, it should load the saa7134 module with the right options. To verify, do this:

```
dmesg | grep saa7 
```
and you should see something like this: 
```
[17179598.828000] saa7134[0]: subsystem: 0919:2003, board: Proteus Pro [philips reference design] [card=1,insmod option]
```
Note it says card=1 instead of 0.  ^_^

So with the module properly set every time on reboot, this script should work for loading tvtime... 

```
#!/bin/sh
killall esd
sox -c 2 -s -w -r 32000 -t ossdsp /dev/dsp1 -t ossdsp -w -r 32000 /dev/dsp &
tvtime --mixer=/dev/mixer:pcm
wait tvtime
t=`pidof sox`;
kill $t;
amixer -c 0 sset PCM 80%,80%  unmute

```

save this to a document and name it "tvtime_launch.sh" and give it executable rights.

Launch "tvtime_launch.sh" and choose "run in a terminal." 
It should kill esd, set the sox options, and launch tvtime with sound.



done...

---

