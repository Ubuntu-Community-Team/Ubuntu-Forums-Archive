---
title: "How does ubuntu play embedded midis on websites?"
date: 2011-12-24
forum: Multimedia Software
---

### Post by JazzPotato on 2011-12-24
Hi forum,
I am wondering how ubuntu plays midi files that are embedded on websites. I have an ubuntu 11.10 laptop and when going on a website with an embedded midi, the midi plays automatically. (The website in question is my home-made homepage, lewgle.comze.com, accompanied by amusing midi, just so you know what I mean).
 I am trying to replicate the same behaviour in arch. Due to the nature of arch, you only get what you want, and i want this midi to play.
 I have installed vlc, fluidsynth, timidity, banshee, the totem plugin for firefox, and the timidity soundfonts. I can play midis with timidity, but the website's midi still dosn't play. 

Thanks in advance for your help,
Live long, and prosper

---

### Post by Lampi on 2011-12-24
try about:plugins to find out what browser plugin is triggering it

Gecko is a good choice for embedded playback:
```
audio/midi 	MIDI Audio 	mid,midi,kar
```

install gecko-mediaplayer from the ubuntu repos

---

### Post by JazzPotato on 2011-12-24
I have installed gecko-mplayer and have all the plugins activated in firefox, but still the midi dosnt play! :-(

---

### Post by Lampi on 2011-12-24
and what does about: plugins show for audio/midi in firefox?

---

### Post by JazzPotato on 2011-12-24
It says audio/midi is handled by the vlc multimedia plugin, so i think ineed a soundfont .sf2 for vlc to use so i can play midis with it. Can you perhaps point me to a soundfont public domain file?

---

### Post by andrew.46 on 2011-12-24
> **JazzPotato said:**
> It says audio/midi is handled by the vlc multimedia plugin, so i think ineed a soundfont .sf2 for vlc to use so i can play midis with it. Can you perhaps point me to a soundfont public domain file?

Unless things have changed most packaged forms of vlc have not been compiled against libfluidsynth and thus do not play midi files. However in case things have changed you can find free soundfonts here:

[http://www.personalcopy.com/linuxfiles.htm](http://www.personalcopy.com/linuxfiles.htm)

---

### Post by Lampi on 2011-12-25
you can change mime type for midi in your browser settings to use gecko instead of this vlc thingy.

---

