---
title: "[SOLVED] Unable to play sound in more than one application"
date: 2008-02-26
forum: Multimedia &amp; Video
---

### Post by oatts on 2008-02-26
When I'm listening to music on XMMS and try to play a video on youtube, mozilla either crashes and gives me an error about too many things trying to access the sound card at once or I just don't hear anything from the video. How do i fix this?

Thanks!!

---

### Post by erginemr on 2008-02-26
What is your sound card? And what is the output of the following command from the terminal:

```
lspci | grep -i audio
```

---

### Post by oatts on 2008-02-27
Soundcard:

   [B]00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 02)
[/B]

---

### Post by Melcar on 2008-02-27
Make sure all your sound settings are set up properly.  On the GNOME menu go to System>Preferences>Sound and make sure you're using ALSA on all the options.

---

### Post by oatts on 2008-02-27
So all of my devices are set to ALSA, but when I try to test it, it says:

[B]
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink profile=music: Resource busy or not available
[/B]

Does Ubuntu even allow two programs to access the audio device simultaneously?

---

