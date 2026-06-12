---
title: "software mixing problem"
date: 2009-05-03
forum: Multimedia Software
---

### Post by moose3642 on 2009-05-03
I am trying to play sound from two programs at once: mixxx and sweep. 
however, I get this message: 
error opening ALSA plughw (0,0) busy
i tried using all other coordinates, such as (1,1), but they don't play sound.

I already tried changing all sound playback to PulseAudio.

I already went here [https://help.ubuntu.com/community/DebuggingSoundProblemsMisc](https://help.ubuntu.com/community/DebuggingSoundProblemsMisc)
but my problem was that upon entering /var/lib/alsa/asound.state I was returned a bash: permission denied error, even though I was already under sudo from the previous line. I tried sudo prefix, to no avail. I tried su, but apparently I don't know my own password, because I was returned an "authentication failure".

so now I know 99 ways to not make a lightbulb, and I'm wondering if software mixing works right out of the box with the distro that came out after Hardy Heron, which is what I'm using. if it doesn't, I see no point in upgrading anyway.
thanks in advance

---

