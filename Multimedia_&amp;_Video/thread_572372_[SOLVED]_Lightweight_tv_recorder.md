---
title: "[SOLVED] Lightweight tv recorder"
date: 2007-10-10
forum: Multimedia &amp; Video
---

### Post by ogcub on 2007-10-10
Hello,
Everybody knows Mythtv. However i think it's too heavy  for me. Is there any simpler tv recording app out there?

---

### Post by rsambuca on 2007-10-10
Do you need pvr functionality, or are you just recording things and can be around to turn it on and off?

---

### Post by ogcub on 2007-10-10
PVR functionality is useful, but even simple recorder is enough for now

---

### Post by rsambuca on 2007-10-10
VLC will record the video streams, or you can just do it from a command line as well.  What is your tuner card?

---

### Post by ogcub on 2007-10-10
Pixelview playtv mobile with saa7134 chip

---

### Post by rsambuca on 2007-10-10
I think that uses v4l2, so you should be able to use vlc for recording and transcoding if you wish.  If you open VLC, select File, Open Capture Device.  Go to the PVR tab, then make sure it says /dev/video0 (or whatever your card is set at), and then press OK.  You can then see if it works ( There may be sound issues with that card, though).  To record, you would select "Stream/Save" at the bottom of the PVR tab and use the settings to configure it.

As an alternative, you could just record from the command line with ```
cat /dev/video0 > /path/to/file/filename.mpg
```Then press Control-C when you want to stop recording.

---

### Post by ogcub on 2007-10-10
> **rsambuca said:**
> I think that uses v4l2, so you should be able to use vlc for recording and transcoding if you wish.  If you open VLC, select File, Open Capture Device.  Go to the PVR tab, then make sure it says /dev/video0 (or whatever your card is set at), and then press OK.  You can then see if it works ( There may be sound issues with that card, though).  To record, you would select "Stream/Save" at the bottom of the PVR tab and use the settings to configure it.

As an alternative, you could just record from the command line with ```
cat /dev/video0 > /path/to/file/filename.mpg
```Then press Control-C when you want to stop recording.

cat does some sort of recording, but i dont understand how to select chanel, bitrate and other things. And after recording, the file isn't playable.

---

### Post by rsambuca on 2007-10-10
Not playable?  What error does it give you?

---

### Post by ogcub on 2007-10-10
> **rsambuca said:**
> Not playable?  What error does it give you?
totem says Could not determine type of stream
vlc plays it but shows not even empty screen, just moving seek bar

---

### Post by rsambuca on 2007-10-10
Can you post the output of dmesg?

---

### Post by ogcub on 2007-10-10
If I try to open capture device with vlc, i also get nothing. But settings seems strange to me. Is frequency of -1 ok?

---

### Post by rsambuca on 2007-10-10
Is it set to a channel?

```
v4l2-ctl -c#
```is the code for selecting channels (put the correct channel in place of the # sign.

---

### Post by ogcub on 2007-10-10
> **rsambuca said:**
> Can you post the output of dmesg?

Card works, because i can see tv using tv time

```
[  487.332000] saa7130/34: v4l2 driver version 0.2.14 loaded
[  487.336000] saa7134[0]: found at 0000:07:00.0, rev: 1, irq: 17, latency: 64, mmio: 0x34000000
[  487.336000] saa7134[0]: subsystem: 1131:0000, board: Sedna/MuchTV PC TV Cardbus TV/Radio (ITO25 Rev:2B) [card=79,insmod option]
[  487.336000] saa7134[0]: board init: gpio is e240c0
[  487.336000] input: saa7134 IR (Sedna/MuchTV PC TV  as /class/input/input8
[  487.440000] saa7134[0]: Huh, no eeprom present (err=-5)?
[  487.580000] tuner 0-004b: chip found @ 0x96 (saa7134[0])
[  487.628000] tuner 0-004b: setting tuner address to 60
[  487.668000] tuner 0-004b: type set to tda8290+75a
[  487.780000] tuner 0-004b: setting tuner address to 60
[  487.820000] tuner 0-004b: type set to tda8290+75a
[  487.884000] saa7134[0]: registered device video0 [v4l2]
[  487.884000] saa7134[0]: registered device vbi0
[  487.888000] saa7134[0]: registered device radio0
[  487.920000] saa7134 ALSA driver for DMA sound loaded
[  487.920000] saa7134[0]/alsa: saa7134[0] at 0x34000000 irq 17 registered as card -2

```

---

### Post by rsambuca on 2007-10-10
Sorry, I am out of ideas here.  I don't know enough about this particular tuner.

---

### Post by ogcub on 2007-10-10
> **rsambuca said:**
> Is it set to a channel?

```
v4l2-ctl -c#
```is the code for selecting channels (put the correct channel in place of the # sign.

if i write 
```
v4l2-ctl -c2
```
i get
```
control '2' without '='
```

And also how iam supposed to know which chanel number to choose?

---

### Post by rsambuca on 2007-10-10
What channel?  Well what channel do you want to watch?

Check to see if you have 'ivtv-utils' installed first.  Then try```
v4l2-ctl -c# -d /dev/video0
```

---

### Post by ogcub on 2007-10-10
> **rsambuca said:**
> What channel?  Well what channel do you want to watch?

Check to see if you have 'ivtv-utils' installed first.  Then try```
v4l2-ctl -c# -d /dev/video0
```

I get
```
control '#' without '='

```
well, thanks for you help

---

### Post by rsambuca on 2007-10-10
Sorry, I am stuck!  Hopefully someone else can help you out.

---

### Post by ogcub on 2007-10-11
Solved, i can record using mencoder

---

