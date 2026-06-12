---
title: "No Digital Audio w/ ATI IXP SB 400 (IEC958)"
date: 2008-03-12
forum: Multimedia &amp; Video
---

### Post by Skitals on 2008-03-12
Sound info:

```
$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: IXP [ATI IXP], device 0: ATI IXP AC97 [ATI IXP AC97]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: IXP [ATI IXP], device 1: ATI IXP IEC958 [ATI IXP IEC958 (AC97)]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
```

 hw=0,0 works beautifully (analog audio). I can't get squat out of the digital coax (0,1). There are threads on this issue dating back 4 years, with varying degrees of resolution. My case appears to be different, given that no prior solution seems to work. I am also experiencing behaviour I haven't heard of before.

The obvious:
IEC958 is unmuted in alsamixer, playback souce = pcm.
Tried turning the External Amplifier switch off/on.
tried forcing all audio through 0,1... nothing
upgraded to alsa-driver -lib and -utils 1.0.16 after trying everything in 1.0.14 (included w/ ubuntu 7.10). I built alsa-driver with --with-cards=atiixp.
Ran alsaconf. Happily recognized my audio and configred snd-atiixp.
Yet no matter what I do, nothing will come out the digital port.

The weird:
Here's what I haven't heard before...
In Sound Preferences (ubuntu/gnome), when I set playback to ATI IXP IEC958 (AC97) and hit test, Sound Preferences crashes when I hit OK to finish. I get "Testing Pipeline" is not responding after a bit, and the option to wait or force quit. I get the same behaviour when playback is set to default and I have set all playback to go through 0,1 (obvious, but at least it shows I was configuring that correctly).

I get similar behavior in mplayer. When I set audio output to 0,1 and play a file, mplayer locks up.

And with speaker-test:

```
$ speaker-test -c2 -Dhw:0,1

speaker-test 1.0.16

Playback device is hw:0,1
Stream parameters are 48000Hz, S16_LE, 2 channels
Using 16 octaves of pink noise
Rate set to 48000Hz (requested 48000Hz)
Buffer size range from 16 to 16384
Period size range from 8 to 8192
Using max buffer size 16384
Periods = 4
was set period_size = 4096
was set buffer_size = 16384
 0 - Front Left
Write error: -5,Input/output error
xrun_recovery failed: -5,Input/output error
Transfer failed: Operation not permitted
```

I got the same exact results in 1.0.14 as i am with 10.16.

Does anyone know any way I can better debug what is cause these failures? Or what could be interfering with the digital audio device?

Thanks!

---

### Post by Skitals on 2008-03-12
In one last desperate attempt, I rechecked all my settings. I can't believe I just spent 6 hours on this. Here's how to make it work:

Turn IEC987 Playback AC97-SPCA in the mixer to 0! Not muted, just all the way down.

And magically, I get digital audio output in mythtv.

MythTV is set to alsa:default, and I have Movies and Music playback set to IEC987 in Sound Preferences. Using the Test button STILL CRASHES Sound Preferences.

None of this makes sense to me, but as long as its working in mythtv, thats all I care about. I hope this helps some hopeless soul down the road who falls into the same traps.

---

