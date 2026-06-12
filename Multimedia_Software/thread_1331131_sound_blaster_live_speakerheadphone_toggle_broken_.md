---
title: "sound blaster live speaker/headphone toggle broken in karmic"
date: 2009-11-19
forum: Multimedia Software
---

### Post by Ryuhayabusa on 2009-11-19
Dear all,

In hardy i had the sound blaster live card alternating between headphone output (black 3.5mm port) and speaker output when i switched "SB live analog/digital output jack" in alsamixer.

This was a very convenient setup for me but in karmic i am unable to get this going.

aplay gives 
```

card 0: Live [SB Live! 5.1 [SB0060]], device 0: emu10k1 [ADC Capture/Standard PCM Playback]
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
card 0: Live [SB Live! 5.1 [SB0060]], device 2: emu10k1 efx [Multichannel Capture/PT Playback]
  Subdevices: 8/8
  Subdevice #0: subdevice #0
  Subdevice #1: subdevice #1
  Subdevice #2: subdevice #2
  Subdevice #3: subdevice #3
  Subdevice #4: subdevice #4
  Subdevice #5: subdevice #5
  Subdevice #6: subdevice #6
  Subdevice #7: subdevice #7
card 0: Live [SB Live! 5.1 [SB0060]], device 3: emu10k1 [Multichannel Playback]
  Subdevices: 1/1
  Subdevice #0: subdevice #0

```

I remember using the emu10k driver in hardy.

does anyone have a similar card with a similar setup?

thanks

---

### Post by Ryuhayabusa on 2009-11-19
I tried these module settings but they stopped all sound from working. I think that this card is different.
[http://ubuntuforums.org/showthread.php?t=762068]("http://ubuntuforums.org/showthread.php?t=762068")

---

### Post by vogelmann on 2009-11-30
Okay, i ran into the same problem after a new install. So i had to do some research - and here's the solution:

That "trick" with muting the jack-plugin might rather have been a bug and hence was not intended.

What you have to do:

1.) create a file .asoundrc in your home-directory (maybe there's already one)

2.) put the following lines into it
```
pcm.!default {
    type plug
    slave.pcm "surround40"
    slave.channels 4
    route_policy duplicate      
}

```
Save and done. This will duplicate the front output to the rear output. You will be able to control volume etc via alsamixer => surround.

Tested with VLC and Exaile. Did not work with amarok2 (phonon).

---

### Post by vogelmann on 2009-12-01
> **vogelmann said:**
> Did not work with amarok2 (phonon).With help from the phonon guys i've been able to figure out the solution to that problem, too.


<sandsmark> r0bert: as mentioned in the FAQ, you need to set a name hint for it
<sandsmark> and then put it on top in system settings &#8594; multimedia
<sandsmark> r0bert: see last item here: [http://phonon.kde.org/cms/1032](http://phonon.kde.org/cms/1032)

So to use output in a way, that stereo sound, which would only be played on the front plug, will be duplicated and played on the rear plug, too, put this into your .asoundrc file residing in your home-directory:

```

pcm.!default {
    type plug
    slave.pcm "surround40"
    slave.channels 4
    route_policy duplicate
    hint {
        show on
        description "Sound Blaster Live Rear=Front"
    }

}
```
=> Both Front and Rear plugs will play the same sound from now on.

For amarok2 and every other program, that makes use of phonon (at least all kde applications, afaik), go to your system settings > multimedia and move the entry "Sound Blaster Live Rear=Front" up to the top. Maybe you'll have to restart amarok.


Tested and worked for:
Ubuntu 9.10 Karmic Koala (I am using xubuntu btw)

Kernel version:
$ uname -a
Linux atropos 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

ALSA version:
$  cat /proc/asound/version 
Advanced Linux Sound Architecture Driver Version 1.0.20.

Soundcard (Creative Sound Blaster Live! 5.1 Digital):
$ lspci | grep eativ
00:08.0 Multimedia audio controller: Creative Labs SB Live! EMU10k1 (rev 0a)

I included that much information, so that Google might one day direct an unhappy user to this posting and he'll find some help, too.


Helpful resources:
[http://alsa.opensrc.org/index.php/.asoundrc](http://alsa.opensrc.org/index.php/.asoundrc)
[http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_(Howto](http://alsa.opensrc.org/index.php/Playing_stereo_on_surround_sound_setup_(Howto))
[http://alsa.opensrc.org/index.php/SurroundSound](http://alsa.opensrc.org/index.php/SurroundSound)
[https://forum.archlinux.de/?id=20;page=Postings;thread=14252](https://forum.archlinux.de/?id=20;page=Postings;thread=14252) (German)

PS: Yepp, sound and Linux still is a pain in the ***! <.
PPS: This forum censors "as[s]s[/s]". LOL. Poor, easily "offended" americans. :P

---

