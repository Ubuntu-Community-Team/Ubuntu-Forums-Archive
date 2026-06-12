---
title: "Video capture device sound issue"
date: 2011-03-08
forum: Multimedia Software
---

### Post by APowers on 2011-03-08
Hello all:

I am running a freshly installed Ubuntu 10.04 LTS "Lucid" system, and am having issues with capturing audio with my Roxio Easy VHS-to-DVD USB capture device.

The device is properly recognized, (although it is seen as a Pinnacle/Kworld/"something else" device), and video capture works great, but I am not able to hear any audio. I have checked all the possible Pulse Audio settings, and haven't found any issues.  When I open "Sound Preferences"  I can see and select the USB audio device, as well as "see" the sound level in real time appear visually on the "input level" indicator on the "input" tab of sound preferences, but there is no audio coming out of the speakers.  I have checked all other possibilities - other Pulse Audio apps, as well as Alsamixer, and I could not find any problems or other reasons that the sound is not working.

I looked in the logfile viewer to see if there were any messages that might indicate what the problem was, and I saw this:

```
pulseaudio[1386]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
```

I Googled the above extensively, and found a lot of posts with similar problems, but no solutions...  I tried searching here, but didn't have any luck either...


In case it helps, here is the rest of what I copied from the messages:
```
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.089566] em28xx #0: AC97 vendor ID = 0x83847650
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.100586] em28xx #0: AC97 features = 0x6a90
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.100591] em28xx #0: Sigmatel audio processor detected(stac 9750)
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.164021] ivtv 0000:05:07.0: firmware: requesting v4l-cx2341x-enc.fw
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.300358] ivtv0: Loaded v4l-cx2341x-enc.fw firmware (376836 bytes)
Mar  7 20:20:10 Ubuntu-10.04-System pulseaudio[1170]: lock-autospawn.c: Cannot access autospawn lock.
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.504124] ivtv0: Encoder revision: 0x02060039
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.532042] cx25840 2-0044: firmware: requesting v4l-cx25840.fw
Mar  7 20:20:10 Ubuntu-10.04-System kernel: [   23.589467] em28xx #0: v4l2 driver version 0.1.2
Mar  7 20:20:12 Ubuntu-10.04-System kernel: [   25.456371] em28xx #0: V4L2 video device registered as /dev/video1
Mar  7 20:20:12 Ubuntu-10.04-System kernel: [   25.456375] em28xx #0: V4L2 VBI device registered as /dev/vbi1
Mar  7 20:20:12 Ubuntu-10.04-System kernel: [   25.456893] usbcore: registered new interface driver em28xx
Mar  7 20:20:12 Ubuntu-10.04-System kernel: [   25.456895] em28xx driver loaded
Mar  7 20:20:12 Ubuntu-10.04-System kernel: [   25.614694] usbcore: registered new interface driver snd-usb-audio
Mar  7 20:20:14 Ubuntu-10.04-System kernel: [   27.186404] cx25840 2-0044: loaded v4l-cx25840.fw firmware (16382 bytes)
Mar  7 20:20:17 Ubuntu-10.04-System pulseaudio[1386]: alsa-mixer.c: Your kernel driver is broken: it reports a volume range from 0.00 dB to 0.00 dB which makes no sense.
Mar  7 20:20:22 Ubuntu-10.04-System pulseaudio[1386]: last message repeated 5 times
```



I've been searching for an answer to this for days, to no avail...

If I can provide any further info, just say the word.

Thanks in advance!!

---

