---
title: "Sound card problems with 8.10"
date: 2008-11-22
forum: Multimedia Software
---

### Post by doyouhas on 2008-11-22
I have a Turtle Beach sound card and works fine with 7.10 but it will not work with 8.04 or 8.10. I&#7743; not sure if it&#347; a problem with drivers or something else entirely. This is the message I get when I attempt to enable the sound card 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Any information could be helpful. Thank you!

---

### Post by psyke83 on 2008-11-23
> **doyouhas said:**
> I have a Turtle Beach sound card and works fine with 7.10 but it will not work with 8.04 or 8.10. I&#7743; not sure if it&#347; a problem with drivers or something else entirely. This is the message I get when I attempt to enable the sound card 

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open audio device for playback.

Any information could be helpful. Thank you!

You need to configure PulseAudio correctly. See: [http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

---

### Post by doyouhas on 2008-11-25
Thank you. Fixed the problem right away.

---

