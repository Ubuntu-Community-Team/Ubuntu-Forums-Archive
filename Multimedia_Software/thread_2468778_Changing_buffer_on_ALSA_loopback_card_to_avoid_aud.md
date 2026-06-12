---
title: "Changing buffer on ALSA loopback card to avoid audio latency"
date: 2021-11-10
forum: Multimedia Software
---

### Post by niconl on 2021-11-10
Hi all,

I am working on an application where I have to join an online Jitsi meeting, using a GoPro Hero 9 back as a webcam, and all this headless (without a screen).
The computer used is a laptop running Ubuntu 18.04.6 LTS (GNU/Linux 4.15.0-161-generic x86_64).
I have made a simple node.js scripts that joins the meeting and can change the webcam and microphone, that's no problem.

I have managed to use ffmpeg to "grab" the video+audio feed from the GoPro (available at udp://@0.0.0.0:8554) and convert the video into a v4l2 device /dev/video1 and the audio into an alsa hw: device, with the following command:
```
ffmpeg -i udp://@0.0.0.0:8554 -map 0:v -pix_fmt yuv420p -f v4l2 /dev/video1 -map 0:a:0 -f alsa hw:2,0,3
```
Prior to the execution of this ffmpeg command, I run sudo modprobe v4l2loopback exclusive_caps=1 and sudo modprobe snd-aloop.

This is then the output of my arecord -l:
```
**** List of CAPTURE Hardware Devices ****
card 0: PCH [HDA Intel PCH], device 0: ALC3246 Analog [ALC3246 Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 2: Loopback [Loopback], device 0: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 2: Loopback [Loopback], device 1: Loopback PCM [Loopback PCM]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
```

After running the ffmpeg command (i let it run in the background), I run ```
pacmd load-module module-alsa-source device=hw:2,1,3 source_properties=device.description=gopro-mic
```
I then manage to use the GoPro as a webcam in my Jitsi meeting and use the "gopro-mic" source as a microphone. It works, but I have a good 6 seconds latency on the video and a good 7+ seconds latency on the audio (also meaning that video and audio are out of sync).
I have noticed that when I only try to get the video (with this ffmpeg command: ```
ffmpeg -i udp://@0.0.0.0:8554 -map 0:v -pix_fmt yuv420p -f v4l2 /dev/video1
```, I get a latency of <1 second on the video, which is acceptable).
I tried to get some help from the good folks over on the ffmpeg subreddit, but someone pointed out to me that alsa might introduce buffering (itself generating some latency). 

When my ffmpeg command is running, with audio, the output of ```
cat /proc/asound/card2/pcm0p/sub3/hw_params
``` gives the following:
```
access: RW_INTERLEAVED
format: S16_LE
subformat: STD
channels: 2
rate: 48000 (48000/1)
period_size: 64
buffer_size: 65536
```

so it does look like there's quite some buffering going on indeed.
I don't know for sure if that's the source of my problem but I'd like to drastically reduce this buffer to see what happens. Now the question is: how can I do that?
I have read that I can make a ```
/home/niconl/.asoundrc
``` file and/or a ```
/etc/asound.conf
``` file with some custom settings, but I find that the documentation on those is not very clear for someone like me who doesn't really know/understand much about alsa.

Could someone here help me out with my attempt to change the alsa buffer, to see if this could be indeed the source of my issue?

I have tried making a .asoundrc file with some copy/pasted content that I found online, like:
```
pcm.dmix_44 {
  type dmix
  slave.pcm {
    type dmix
    ipc_key 99
    slave {
      pcm "hw:2"
      rate 48000
      channels 2
      period_size 1024
      buffer_size 1024
    }
  }
}
```

but that has absolutely no effect.

Thanks to anyone who could provide some pointers!

---

