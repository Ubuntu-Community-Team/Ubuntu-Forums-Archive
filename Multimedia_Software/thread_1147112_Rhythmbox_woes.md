---
title: "Rhythmbox woes"
date: 2009-05-03
forum: Multimedia Software
---

### Post by RichardCain on 2009-05-03
Rhythmbox won't play anything.  Whenever I select a track it just sits there and doesn't do anything.
I tried starting Rhythmbox from the terminal and got

(rhythmbox:13763): Rhythmbox-WARNING **: Could not open device /dev/radio0

I tried looking in the /dev folder and sure enough there's no such file as "radio0".
I've tried reconfiguring rhythmbox, and also uninstalling/reinstalling it, but it still comes up with the same problem.

---

### Post by kostkon on 2009-05-03
Try this:

Press ALT + F2 and then give
```
gstreamer-properties
```
In the window that will appear, select the *Audio* Tab. Make sure that in the *Default Output* section the *Plugin* drop-down menu is set to *Autodetect*.

If it already set to *Autodetect*, try changing it to *ALSA* or *PulseAudio*, whichever is available.

---

### Post by RichardCain on 2009-05-04
Thanks for that, but the problem wasn't with the sound, but that Rhythmbox won't actually play the song.  If I select a track, it comes up in the title bar, the artwork appears in the bottom corner just like normal, but it doesn't start to play.  The slider doesn't start moving along and the counter doesn't start counting.  Also, when I try to close it, a box pops up telling me that rhythmbox is not responding and do I want to force quit?

Any more ideas?

---

### Post by mikezila on 2009-05-04
> **RichardCain said:**
> Thanks for that, but the problem wasn't with the sound, but that Rhythmbox won't actually play the song.  If I select a track, it comes up in the title bar, the artwork appears in the bottom corner just like normal, but it doesn't start to play.  The slider doesn't start moving along and the counter doesn't start counting.  Also, when I try to close it, a box pops up telling me that rhythmbox is not responding and do I want to force quit?

Any more ideas?

It sounds like something is gumming up your sound mixer.  Do other apps that play sound work?  Do other apps that use gstreamer work?  Try playing a music file with totem and see what happens.

It sounds like RB is trying to use the wrong sound mixer.

---

### Post by RichardCain on 2009-05-04
> **mikezila said:**
> Try playing a music file with totem and see what happens.

It sounds like RB is trying to use the wrong sound mixer.

Totem, GNOME Mplayer and gxine all do the same thing.  VLC appears to play the track, but no sound.

---

### Post by xc3RnbFO8P on 2009-05-04
In System> Preferences> Sound> Music and Movies, try to change it to Alsa

---

### Post by mikezila on 2009-05-04
> **RichardCain said:**
> Totem, GNOME Mplayer and gxine all do the same thing.  VLC appears to play the track, but no sound.

Then your ALSA setup is borked somehow.  Are there any apps on your system that play sound correctly?  Do you use MPD (music player daemon)?

---

### Post by RichardCain on 2009-05-05
Thanks.  Just tried it but still no joy!
Any more ideas?

---

### Post by RichardCain on 2009-05-05
The sound in Skype is OK for a test call, but my current satellite connection won't allow a proper call.
And what's this "radio" file?  Why could it be missing?

---

### Post by RichardCain on 2009-05-05
Problem solved!!!

I had a quick brainstorm, thinking "seeing as everyone thinks it's the sound settings, what have I changed since it was last working?"
The answer lay in the Skype settings.  It seems that Skype was monopolising things.  I went into the Skype options and changed the sound devices to "default" and hey presto, rhythmbox works again!
It seems that I have to change the settings every time I want to use Skype, and then change them back afterwards.
I do think it's strange how this can happen though.  Has anyone else had this problem?

Thanks for all your help, folks.  You might not have fixed it, but you pointed me in the right direction.

---

### Post by RichardCain on 2009-05-05
By the way, how do I mark this thread as "solved"?  :)

---

### Post by mikezila on 2009-05-05
Edit the first post and change the title.  Glad you got it working.

---

