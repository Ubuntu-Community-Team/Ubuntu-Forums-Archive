---
title: "VLC will not record, but other programs do"
date: 2009-04-30
forum: Multimedia Software
---

### Post by xoros on 2009-04-30
I have audacity & other programs recording my voice just fine!

However, I can't get vlc to record voice, no matter what options I choose.  It records video from webcam just fine, but no sound records.

I am thinking I am using the wrong device name... which name do I pick?

```

ls /dev
admmidi          mixer               sequencer   tty35           usbdev1.3_ep00
adsp             mixer1              sequencer2  tty36           usbdev1.3_ep87
amidi            net                 sg0         tty37           usbdev2.1_ep00
audio            network_latency     sg1         tty38           usbdev2.1_ep81
audio1           network_throughput  shm         tty39           usbdev2.3_ep00
block            null                snapshot    tty4            usbdev2.3_ep81
bus              nvidia0             snd         tty40           usbdev2.4_ep00
cdrom            nvidiactl           sndstat     tty41           usbdev2.4_ep81
cdrw             oldmem              sr0         tty42           usbmon0
char             pktcdvd             stderr      tty43           usbmon1
console          port                stdin       tty44           usbmon2
core             ppp                 stdout      tty45           v4l
cpu_dma_latency  psaux               tty         tty46           vcs
disk             ptmx                tty0        tty47           vcs1
dmmidi           pts                 tty1        tty48           vcs2
dsp              ram0                tty10       tty49           vcs3
dsp1             ram1                tty11       tty5            vcs4
dvd              ram10               tty12       tty50           vcs5
dvdrw            ram11               tty13       tty51           vcs6
ecryptfs         ram12               tty14       tty52           vcs7
fd               ram13               tty15       tty53           vcs8
full             ram14               tty16       tty54           vcsa
fuse             ram15               tty17       tty55           vcsa1
hidraw0          ram2                tty18       tty56           vcsa2
hidraw1          ram3                tty19       tty57           vcsa3
hpet             ram4                tty2        tty58           vcsa4
initctl          ram5                tty20       tty59           vcsa5
input            ram6                tty21       tty6            vcsa6
kmem             ram7                tty22       tty60           vcsa7
kmsg             ram8                tty23       tty61           vcsa8
log              ram9                tty24       tty62           video0
loop0            random              tty25       tty63           vmci
loop1            rtc                 tty26       tty7            vmmon
loop2            rtc0                tty27       tty8            vmnet0
loop3            scd0                tty28       tty9            vmnet1
loop4            sda                 tty29       ttyS0           vmnet8
loop5            sda1                tty3        ttyS1           vsock
loop6            sda2                tty30       ttyS2           xconsole
loop7            sda3                tty31       ttyS3           zero
mapper           sda4                tty32       urandom
mem              sda5                tty33       usbdev1.1_ep00
midi             sda6                tty34       usbdev1.1_ep81

```

```
aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: Live [SBLive! Value [CT4830]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
  Subdevices: 32/32
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
  Subdevice #8: subdevice #8
  Subdevice #9: subdevice #9
  Subdevice #10: subdevice #10
  Subdevice #11: subdevice #11
  Subdevice #12: subdevice #12
  Subdevice #13: subdevice #13
  Subdevice #14: subdevice #14
  Subdevice #15: subdevice #15
  Subdevice #16: subdevice #16
  Subdevice #17: subdevice #17
  Subdevice #18: subdevice #18
  Subdevice #19: subdevice #19
  Subdevice #20: subdevice #20
  Subdevice #21: subdevice #21
  Subdevice #22: subdevice #22
  Subdevice #23: subdevice #23
  Subdevice #24: subdevice #24
  Subdevice #25: subdevice #25
  Subdevice #26: subdevice #26
  Subdevice #27: subdevice #27
  Subdevice #28: subdevice #28
  Subdevice #29: subdevice #29
  Subdevice #30: subdevice #30
  Subdevice #31: subdevice #31
card 0: Live [SBLive! Value [CT4830]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SBLive! Value [CT4830]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

```
cat /proc/asound/cards
 0 [Live           ]: EMU10K1 - SBLive! Value [CT4830]
                      SBLive! Value [CT4830] (rev.7, serial:0x80261102) at 0xcce0, irq 17
 1 [U0x46d0x992    ]: USB-Audio - USB Device 0x46d:0x992
                      USB Device 0x46d:0x992 at usb-0000:00:0b.1-2, high speed

```

0,0 is my soundcard which I want to do the recording, the other 0,1 is my webcam mic.. which I could care less about. 

So what should the audio device name be?  (In other programs that work, it just says "default" for the alsa audio option)

---

### Post by xoros on 2009-04-30
Should it be something from /dev/snd??

```
/dev/snd$ ls
controlC0  hwC0D0  midiC0D0  midiC0D2  pcmC0D0p  pcmC0D2c  pcmC0D3p  seq
controlC1  hwC0D2  midiC0D1  pcmC0D0c  pcmC0D1c  pcmC0D2p  pcmC1D0c  timer

```

---

### Post by xoros on 2009-04-30
Is everyone else able to record audio using vlc with alsa?

If so, what device names are you using?  
(/dev/dsp is OSS, if i'm not mistaken.)

---

### Post by xoros on 2009-04-30
Here is vlc's log... still seems it won't find the alsa default!

```
main debug: looking for access_demux module: 1 candidate
v4l2 warning: unknown option v4l2-dev=/dev/video0 
v4l2 warning: unknown option v4l2-adev=/dev/audio 
v4l2 warning: unknown option v4l2-standard=0 
v4l2 warning: unknown option v4l2-dev=/dev/video0 
v4l2 warning: unknown option v4l2-standard=0 
v4l2 warning: unknown option v4l2-chroma= 
v4l2 warning: unknown option v4l2-input=0 
v4l2 warning: unknown option v4l2-audio-input=0 
v4l2 warning: unknown option v4l2-io=1 
v4l2 warning: unknown option v4l2-width=0 
v4l2 warning: unknown option v4l2-height=0 
v4l2 warning: unknown option v4l2-fps=0 
v4l2 warning: unknown option no-v4l2-use-libv4l2 
v4l2 warning: unknown option v4l2-adev=/dev/audio 
v4l2 warning: unknown option v4l2-audio-method=3 
v4l2 warning: unknown option v4l2-stereo 
v4l2 warning: unknown option v4l2-samplerate=48000 
v4l2 warning: unknown option v4l2-caching=300 
v4l2 warning: unknown option v4l2-tuner=0 
v4l2 warning: unknown option v4l2-tuner-frequency=-1 
v4l2 warning: unknown option v4l2-tuner-audio-mode=0 
v4l2 warning: unknown option no-v4l2-controls-reset 
v4l2 warning: unknown option v4l2-brightness=-1 
v4l2 warning: unknown option v4l2-contrast=-1 
v4l2 warning: unknown option v4l2-saturation=-1 
v4l2 warning: unknown option v4l2-hue=-1 
v4l2 warning: unknown option v4l2-black-level=-1 
v4l2 warning: unknown option v4l2-auto-white-balance=-1 
v4l2 warning: unknown option v4l2-do-white-balance=-1 
v4l2 warning: unknown option v4l2-red-balance=-1 
v4l2 warning: unknown option v4l2-blue-balance=-1 
v4l2 warning: unknown option v4l2-gamma=-1 
v4l2 warning: unknown option v4l2-exposure=-1 
v4l2 warning: unknown option v4l2-autogain=-1 
v4l2 warning: unknown option v4l2-gain=-1 
v4l2 warning: unknown option v4l2-hflip=-1 
v4l2 warning: unknown option v4l2-vflip=-1 
v4l2 warning: unknown option v4l2-hcenter=-1 
v4l2 warning: unknown option v4l2-vcenter=-1 
v4l2 warning: unknown option v4l2-audio-volume=-1 
v4l2 warning: unknown option v4l2-audio-balance=-1 
v4l2 warning: unknown option no-v4l2-audio-mute 
v4l2 warning: unknown option v4l2-audio-bass=-1 
v4l2 warning: unknown option v4l2-audio-treble=-1 
v4l2 warning: unknown option v4l2-audio-loudness=-1 
v4l2 warning: unknown option v4l2-set-ctrls=
v4l2 debug: ALSA input support available
v4l2 debug: Trying direct kernel v4l2
v4l2 debug: main device=' '
v4l2 debug: trying device ' ' as video
v4l2 error: cannot open video device (No such file or directory)
v4l2 debug: trying device ' ' as audio
v4l2 error: cannot open device   for ALSA audio (No such file or directory)
v4l2 error: cannot open device   for OSS audio (No such file or directory)
v4l2 debug: opening '/dev/video0' as video
v4l2 debug: V4L2 device: UVC Camera (046d:0992) using driver: uvcvideo (version: 0.1.0) on 0000:00:0b.1
v4l2 debug: the device has the capabilities: (X) Video Capure, ( ) Audio, ( ) Tuner
v4l2 debug: supported I/O methods are: ( ) Read/Write, (X) Streaming, ( ) Asynchronous
```

---

### Post by albinootje on 2009-04-30
> **xoros said:**
> Is everyone else able to record audio using vlc with alsa?

If so, what device names are you using?

I actually didn't know that vlc can record.
> 
(/dev/dsp is OSS, if i'm not mistaken.)

Yes, and the vlc settings also show /dev/dsp for OSS.
You could try that with alsa, since alsa has OSS emulation 
see : 
```

lsmod|grep oss

```
whether the oss emulation is there.

---

### Post by xoros on 2009-04-30
> **albinootje said:**
> I actually didn't know that vlc can record.


Yes, and the vlc settings also show /dev/dsp for OSS.
You could try that with alsa, since alsa has OSS emulation 
see : 
```

lsmod|grep oss

```
whether the oss emulation is there.

You can record sound in vlc under Media > Convert/Save

Here is a picture of where I need to know the device name:

[IMG]http://img528.imageshack.us/img528/3653/screenshotyve.png[/IMG]

---

### Post by albinootje on 2009-05-01
> **xoros said:**
> 
Here is a picture of where I need to know the device name:[/IMG]

This is old, by maybe helpful :
[http://www.linux.org/docs/ldp/howto/Alsa-sound-2.html](http://www.linux.org/docs/ldp/howto/Alsa-sound-2.html)
> 
ALSA has it's own devices in /dev/snd, for example /dev/snd/pcmC0D1 is Card 0, Device 1.


---

### Post by xoros on 2009-05-01
> **albinootje said:**
> This is old, by maybe helpful :
[http://www.linux.org/docs/ldp/howto/Alsa-sound-2.html](http://www.linux.org/docs/ldp/howto/Alsa-sound-2.html)

Thanks for the link!! I will try to test with what they say: 
> A few remarks. ALSA has it's own devices in /dev/snd, for example /dev/snd/pcmC0D1 is Card 0, Device 1. You can use the old /dev/pcmXY devices if you loaded snd-pcm1-oss for backwards compatibility. You'll also want to use /dev/mixer, so load snd-mixer-oss as well. Before you can play any sound, you need to unmute the card with ``amixer''. Type ``amixer groups'', then try something like
amixer set PCM 100 unmute

Generally you can use options ``mute'' or ``unmute'', ``capture'' or ``nocapture'' and numbers.



---

### Post by Francewhoa on 2010-03-26
Same here. VLC records video but not the sound.

@xoros: Have you found a solution?

---

### Post by PokerFacePenguin on 2010-11-11
> **xoros said:**
> You can record sound in vlc under Media > Convert/Save

Here is a picture of where I need to know the device name:

[IMG]http://img528.imageshack.us/img528/3653/screenshotyve.png[/IMG]

Well, to use the USB sound in vlc I found this excellent article

[http://ishmilok.blogspot.com/2010/07/webcam-recording-using-vlc-on-linux.html](http://ishmilok.blogspot.com/2010/07/webcam-recording-using-vlc-on-linux.html)


maybe it helps you or someone else out...

---

