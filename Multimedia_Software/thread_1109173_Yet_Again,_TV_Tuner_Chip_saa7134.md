---
title: "Yet Again, TV Tuner Chip saa7134"
date: 2009-03-28
forum: Multimedia Software
---

### Post by wbee on 2009-03-28
******************SOLVED****************************


Last night,I reinstalled 8.10. Everything worked fine,printers,screen resolutions and speeds,and even the saa7134 chip was recognized. When I downloaded tvtime,I did not even have to scan the channels. It was ready to go,absent the sound,which is another story.

I downloaded all the updates,about an hour's worth,close to three hundred files,and when that was all done,there was no signal from the Philips saa7134 chip.

I did the things I had done previously,with previous installs,to get the video to work,and nothing.

Here is  sudo lshw -C multimedia :

```
 *-multimedia:0          
       description: Multimedia controller
       product: SAA7131/SAA7133/SAA7135 Video Broadcast Decoder
       vendor: Philips Semiconductors
       physical id: 6
       bus info: pci@0000:04:06.0
       version: d1
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: driver=saa7134 latency=64 maxlatency=255 mingnt=255 module=saa7134

```

Here is dmesg:

```
15.920123] saa7133[0]: i2c eeprom f0: ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff ff
[   16.224198] tuner' 1-004b: chip found @ 0x96 (saa7133[0])
[   16.504065] tuner-simple 1-004b: creating new instance
[   16.504070] tuner-simple 1-004b: type set to 2 (Philips NTSC (FI1236,FM1236 and compatibles))
[   16.513049] saa7133[0]: registered device video0 [v4l2]
[   16.513092] saa7133[0]: registered device vbi0
[   16.547711] saa7134 ALSA driver for DMA sound loaded
[   16.548426] saa7133[0]/alsa: saa7133[0] at 0xfebff800 irq 18 registered as card -2]
```

Here is the line from the modprobe:

```
-rw-r--r-- 1 root root   84 2009-03-28 13:56 saa7134

```



Here is lspci:

```
04:06.0 Multimedia controller: Philips Semiconductors SAA7131/SAA7133/SAA7135 Video Broadcast Decoder (rev d1)

```

Ideas? Suggestions?

--------------

Thank you
W

---

### Post by paulita on 2009-05-07
I have exactly the same problem. I can watch tv but have no sound at all (using tvtime)

---

### Post by HappyFeet on 2009-05-07
This will not help you now, but in the future *always* do updates ***first*** after a reinstall, *then* configure your computer. It will save you some headaches.

---

### Post by wbee on 2009-05-07
Yeah,that is exactly what happened:-)

---

