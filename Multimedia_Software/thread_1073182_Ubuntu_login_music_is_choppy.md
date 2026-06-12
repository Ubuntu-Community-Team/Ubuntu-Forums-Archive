---
title: "Ubuntu login music is choppy"
date: 2009-02-18
forum: Multimedia Software
---

### Post by Pitboss on 2009-02-18
Hi all, I'm new to ubuntu and I'm having problems with it's login music. 

In three or four days I ran the alsa-update script I found in [this post]("http://ubuntuforums.org/showthread.php?t=1046137"). Everything worked fine, but after I configured my sound settings from 

System > Preferences > Sound to be:

**Sounds Events** 
Sound Playback:         ALSA - Advanced Linux Sound Architecture
**Music and Movies** 
Sound Playback:         ALSA - Advanced Linux Sound Architecture
**Audio Conferencing**
Sound Playback:         ALSA - Advanced Linux Sound Architecture
Sound Capture:          ALSA - Advanced Linux Sound Architecture
**Default Mixer Tracks**
Device:                 HDA ATI SB (Alsa Mixer)

And set my default sound card to be SB.

I'm having trouble with the ubuntu login music, and every other audio output is fine.

So I wonder is this gstreamer problem, and do you have any ideas how to fix it? It works fine if in the settings above instead of 

"ALSA - Advanced Linux Sound Architecture" there is 
"PulseAudio Sound Server"

and the default card is PulseAudio, but then I have some strange problems with mplayer audio output.

---

### Post by Divider on 2009-02-18
I have no real answer.

If the login music is choppy and  you cant find an alternative,

I would suggest disabling it altogether, its one less thing it load.

---

