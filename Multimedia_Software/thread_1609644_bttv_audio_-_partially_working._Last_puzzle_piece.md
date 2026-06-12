---
title: "bttv audio - partially working. Last puzzle piece?"
date: 2010-10-30
forum: Multimedia Software
---

### Post by markdavidoff on 2010-10-30
Ubuntu 10.10 seems to have broken support for my bttv video capture cards audio in mythTV. I think it was to do with OSS support drop.

However, this capture card works by outputting the audio via a cable to the sound card's line-in.

So all I had to do (in theory) is set the recording channel to that line-in in the mythTV-setup.

I entered ALSA:plughw:0,2 as the audio device for my capture card (I checked this input in audacity. so far so good!)

Now, here is the tricky part:
I can get sound to play ONLY if I first start recording from the sound device first in audacity!

(If I don't start the recording in audacity, I won't get any sound, and if I start the recording after the video is displayed, then that won't work either. Recording needs to start BEFORE viewing video from the card in MythTV)

So, how do I get MythTV to open the audio device when it needs to record from it?

Alternatively, is there a way to have the device open at all times (without having audacity recording, obviously)?

EDIT:
Seems I found my own (dirty) solution:
create a script:
> #!/bin/sh
# Opens audio channel for recording at all times
arecord -q -t wav -c 2 -r 48000 -D plughw:0,2 /dev/null &
and add it to startup apps

---

