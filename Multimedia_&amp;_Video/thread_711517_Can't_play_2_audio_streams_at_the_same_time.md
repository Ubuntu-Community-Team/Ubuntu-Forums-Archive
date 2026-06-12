---
title: "Can't play 2 audio streams at the same time"
date: 2008-02-29
forum: Multimedia &amp; Video
---

### Post by wingnux on 2008-02-29
This is kind of annoying... Whenever I play an audio stream (i.e. an mp3 file on amarok) I can't play another one on any other program, even flash videos on firefox! I can only listen to one audio stream and it makes any other streams mute and that applies for amarok, totem, firefox (flash), vlc (movies) and such...

Is there any way to fix that? I'm sure I was able to do it on Gutsy (I'm using Hardy now)...

Thanks in advance.

---

### Post by Melcar on 2008-02-29
Make sure all your sound settings (from both your gnome desktop and on individual apps.) are set up right.  For gstreamer global settings (this will affect things like Totem and Rhythmbox) check Sound and Multimedia Systems Selector (both in System>Preferences)  and make sure everything is set to ALSA and nothing is tied to your sound card.

---

### Post by wingnux on 2008-02-29
There's only the "Sound" option on the Preferences menu but setting everything to ALSA worked (it was set to "autodetect")! 

Thanks for the help! =)

---

### Post by Melcar on 2008-03-01
To get the Multimedia System Selector just open up the menu editor and look under Preferences; check the box next to it so it shows on your menu.  Make sure everything there is set to ALSA and not directly to your sound card.

---

