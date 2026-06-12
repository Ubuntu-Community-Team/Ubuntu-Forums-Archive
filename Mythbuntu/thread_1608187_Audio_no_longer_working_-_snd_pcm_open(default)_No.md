---
title: "Audio no longer working - snd_pcm_open(default): No such file or directory"
date: 2010-10-28
forum: Mythbuntu
---

### Post by Sctmon on 2010-10-28
The audio on one of my Mythtv machines has stopped working. The volume bar appears but is at 0% and doesn't move. The other front ends connected work fine though.

I have deliberately not installed any updates lately to try and avoid problems like this and I only use the computer to run the frontend. Can anyone offer any help? 

This it the terminal output which I think is relevant.
2010-10-28 21:53:20.713 AFD: Opened codec 0x1d921d0, id(MPEG2VIDEO) type(Video)
2010-10-28 21:53:20.713 AFD: codec MP2 has 2 channels
2010-10-28 21:53:20.713 AFD: Opened codec 0x27147d0, id(MP2) type(Audio)
2010-10-28 21:53:20.713 AFD: codec MP3 has 0 channels
2010-10-28 21:53:20.713 AFD: Opened codec 0x1da52f0, id(MP3) type(Audio)
2010-10-28 21:53:20.713 AFD: Opened codec 0x2714010, id(DVB_SUBTITLE) type(Subtitle)
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
2010-10-28 21:53:20.728 AudioOutput Error: snd_pcm_open(default): No such file or directory
2010-10-28 21:53:20.728 Opening audio device 'default'. ch 2(2) sr 48000 (reenc 0)
2010-10-28 21:53:20.728 Opening ALSA audio device 'default'.
ALSA lib pcm_dmix.c:1010:(snd_pcm_dmix_open) unable to open slave
2010-10-28 21:53:20.729 AudioOutput Error: snd_pcm_open(default): No such file or directory
2010-10-28 21:53:20.729 NVP(0): Disabling Audio, reason is: snd_pcm_open(default): No such file or directory

I guess that it has forgotten what the ALSA default refers to but I have no idea where to start or how it happened.

Myth settings are
Audio output device:   ALSA:default
Speaker configuration: Stereo

Mixer device: ALSA:default
Mixer Controls: PCM

These have always been set to this and are the same setting used on my other 2 frontends which are working fine.

Any thoughts?

P.s Audio works fine if I play a file using VLC

---

### Post by klc5555 on 2010-10-29
Not sure what happend to your PCM controls, which seem to be missing, but try switching your frontend mixer controls from "PCM" to "Master" and see if that does it for you. I have a couple of frontends that have never had the sound conrols work properly until I did that.

---

### Post by Sctmon on 2010-10-29
Hi,
Thanks but it was one of the first things I tried along with changing the output device and mixer device setting and it had no effect. I am sure something similar happened a while ago and changing to PCM from Master fixed it then.

I do make system backups and database backups now and then so I made a new database backup, restored my last system backup, dropped the old mysql database and then restored the backup database and the audio was working again. I had to reboot the system and when it restarted , the audio was not working again!


I did find this 
[http://www.mythtv.org/pipermail/mythtv-users/2009-November/269617.html](http://www.mythtv.org/pipermail/mythtv-users/2009-November/269617.html)

but could not get the script it mentions to run. Noe even sure it would help.


Scott

---

### Post by bance on 2010-10-29
Don't know if it'll work for you, but I did :-

```
aplay -l
```this outputs your sound devices

```
**** List of PLAYBACK Hardware Devices ****
card 0: NVidia [HDA NVidia], device 0: ALC889A Analog [ALC889A Analog]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 1: ALC889A Digital [ALC889A Digital]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: NVidia [HDA NVidia], device 3: NVIDIA HDMI [NVIDIA HDMI]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 1: Speaker [SungForn DS-301 USB Speaker], device 0: USB Audio [USB Audio]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```Then in set up I set alsa:default:CARD=1

worked for me:guitar:

---

### Post by Sctmon on 2010-10-29
I did try naming the card directly with the device name but not Card=X. Will give it a go when I get home.

---

### Post by Sctmon on 2010-10-29
Gold star to you! :KSIt worked a treat.

Thanks for help..

Scott

---

### Post by bance on 2010-10-29
glad i could help !

---

### Post by xinix on 2010-12-10
Great advice! It worked for me too.

---

### Post by Sctmon on 2010-12-11
This worked for me for a few days and then the audio stopped working again. Changing back to ALSA:default got it working again.

Both times it happen after installing 'important' updates

---

### Post by xinix on 2010-12-11
We'll see how long this fix lasts.   I've had awful audio experiences since I upgraded to Maverick.  It would work once, then it wouldn't, then only for HD stuff, or not at all.  Never a consistent pattern.

---

