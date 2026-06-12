---
title: "Sound broken in Ubuntu Studio"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by troelsjc on 2007-05-27
Ahoy mateys! :p

When i run Firefox, then the ALSA driver acts wierd. Amarok won't even open, and when i go to *System > Preferences > Sound* and click *Test* when the sound playback is set to *Autodetect*, the window just closes, and if i change the *Audio Playback* setting to *ALSA* and clicks *Test*, a box opens with an error message like this:

```
audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.
```

Sometimes when Firefox is closed, Amarok can start again, and the sound in all other applications works, but sometimes not! When Firefox is open, only the sound in Firefox works, nothing else. Also, JACK can't start cause it fails to load the ALSA kernel module.

Overall the sound support is very unstable. Is there a way to 'reset' the sound, I didn't have problems before in Dapper and Edgy.

My soundcard is the **Zoltrix Nightingale Pro 6** and am using the 2.6.20-15-lowlatency kernel.

Anyone knows how to fix this, help would be greatly apprecieated :)


Best regards,
Troels

---

### Post by troelsjc on 2007-06-05
I found that [garbage792]("http://ubuntuforums.org/member.php?u=105838") has [the same problem.]("http://ubuntuforums.org/showthread.php?t=423117")

---

### Post by euchrid on 2007-06-07
I'm fairly well convinced there's something wrong with the Alsa driver in Feisty (or the way Feisty uses it).

I upgraded my driver, and I got everything working in Ubuntu Studio (as far as recording goes).

Information and instructions here: [http://ubuntuforums.org/showthread.php?p=2798055#post2798055]("http://ubuntuforums.org/showthread.php?p=2798055#post2798055")

---

