---
title: "music plays too fast via spdif"
date: 2008-06-24
forum: Multimedia Software
---

### Post by ldormon on 2008-06-24
Hello all

Well I've tried to get all my audio going via spdif. I thought I'd try the pulseaudio way first and follow these two howto's :-

This all looked good, but just didn't work :(
SPDIF in Hardy
[http://ubuntuforums.org/showthread.php?t=776958](http://ubuntuforums.org/showthread.php?t=776958)

This worked for about 5 mins then alsa just borked with buffer under runs, (no amount of fragment frigging would keep it stable)
HOWTO: A52 Encoded 5.1 Surround Sound Awesomeness with PulseAudio and ALSA on Hardy
[http://ubuntuforums.org/showthread.php?t=714712](http://ubuntuforums.org/showthread.php?t=714712)

So I thought I'd just start again, mplayer all works with 
mplayer -ao alsa:device=spdif 

But if I try and play cd's with aplay --device=spdif they come out too fast. Something funning is going on somewhere and up-sampling the 44.1 content to 48Khz but I've no idea where?

Here's what I've got 

$ aplay -l
**** List of PLAYBACK Hardware Devices ****
card 0: ICH5 [Intel ICH5], device 0: Intel ICH [Intel ICH5]
  Subdevices: 1/1
  Subdevice #0: subdevice #0
card 0: ICH5 [Intel ICH5], device 4: Intel ICH - IEC958 [Intel ICH5 - IEC958]
  Subdevices: 1/1
  Subdevice #0: subdevice #0


I'm not really sure what road to go down down, pulseaudio doesn't seem to do AC3 passthru and alsa playing silly buggers with the sampling.

Has anyone a solid hardy box with all their audio going via spdif, if so how?

Cheers for any help

Lee

---

### Post by ldormon on 2008-06-24
arh how embarrassing

I just switched all the sound prefs to alsa added this to my .asoundrc 

pcm.!default {
   type plug
   slave {
        pcm "spdif"
        rate 48000
        format S16_LE
    }
}

and rhythmbox, youtube, ac3 all work, its just my test with aplay that plays too fast. Mmm think I'll back away slowly.

Sorry

---

