---
title: "Microphone not working"
date: 2010-09-27
forum: Multimedia Software
---

### Post by .broken. on 2010-09-27
Hello,

I was experiencing issues with my sound after installing Ubuntu on Saturday. As a result of this thread, [http://ubuntuforums.org/showthread.php?p=9893015&posted=1](http://ubuntuforums.org/showthread.php?p=9893015&posted=1), I replaced ALSA with OSS 4 and this seems to have solved any problems I had on that front. Only thing is that now my microphone doesn't work.

Any suggestions?

Cheers,
James

---

### Post by .broken. on 2010-09-27
Btw, I should mention that it's an in-built microphone on a Sony Vaio FW11E...

I've googled around but short of going into the Volume Controls and putting a tick in Microphone I haven't found anything useful :/

Thought this might help:

```
$ ossmix
Selected mixer 0/High Definition Audio ALC262
Known controls are:
jack.int-speaker.mode <mix|mix|input> (currently mix)
jack.int-speaker [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.int-speaker.mute ON|OFF (currently OFF)
jack.black.mode <mix|mix|input> (currently mix)
jack.black [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.black.mute ON|OFF (currently OFF)
jack.red.mode <mix|mix|input> (currently mix)
jack.red [<leftvol>:<rightvol>] (currently 29.9:29.9 dB)
jack.red.mute ON|OFF (currently OFF)
record.mix.mute.mic1 ON|OFF (currently OFF)
record.mix.mute.line-out1 ON|OFF (currently OFF)
record.mix.mute.headphone1 ON|OFF (currently OFF)
record.mix.mute.mix1 ON|OFF (currently OFF)
record.mix1 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
record.mix.mute.mic2 ON|OFF (currently OFF)
record.mix.mute.line-out2 ON|OFF (currently OFF)
record.mix.mute.headphone2 ON|OFF (currently OFF)
record.mix.mute.mix2 ON|OFF (currently OFF)
record.mix2 [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
record.select.select <mic|mix|dmic> (currently mic)
record.select [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.mic [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.line-out [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.headphone [<leftvol>:<rightvol>] (currently 38.9:38.9 dB)
misc.speaker-mute ON|OFF (currently OFF)
misc.mix-mute1 ON|OFF (currently OFF)
misc.mix1 [<leftvol>:<rightvol>] (currently 37.4:37.4 dB)
misc.mix2 <speaker|mix> (currently speaker)
misc.headphone-mute ON|OFF (currently OFF)
misc.mix-mute2 ON|OFF (currently OFF)
misc.mix3 [<leftvol>:<rightvol>] (currently 37.4:37.4 dB)
misc.mix4 <headphone|mix> (currently headphone)
vmix0-enable ON|OFF (currently ON)
vmix0-rate <decimal value> (currently 48000) (Read-only)
vmix0-channels <Stereo|Multich> (currently Stereo)
vmix0-src <Fast|High|OFF> (currently Fast)
vmix0-outvol <monovol> (currently 23.5 dB)
vmix0-invol <monovol> (currently 25.0 dB)
vmix0.pcm7 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm8 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm9 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
vmix0.pcm10 [<leftvol>:<rightvol>] (currently 25.0:25.0 dB)
```

---

