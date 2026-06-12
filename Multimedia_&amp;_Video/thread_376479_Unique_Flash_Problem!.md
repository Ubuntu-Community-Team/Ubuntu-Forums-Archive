---
title: "Unique Flash Problem!"
date: 2007-03-04
forum: Multimedia &amp; Video
---

### Post by Mr Scipione on 2007-03-04
Alright, so here's a good one.  As we all know, flash 9 includes support for ALSA!  Greak, except I don't think ALSA or OSS is working for me.  Now I do have sound however.  If I go to the system/preferences/sound tab under "sound playback" I have quite a few options including: ALSA, OSS, ESD, AUTO, and USB, USB1 and USB2.  If I select USB then I can hear the test sound.  Also I can play mp3s and other files just fine in VLC and MPlayer.  However, if I select any other one I get an error message.  Here is the one from ALSA:  

audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing.

I have a soundblaster Extigy external usb soundcard.  But this isn't a hardware problem because it obviously works fine for some things.  I think my problem is that I don't know which DSP wrapper to tell Firefox to use because I can't use AOSS or ESD or the other wrappers I've been reading about.  If you have any ideas please let me know.  The only other clue is that alsamixer gives me this error message:  

alsamixer: function snd_ctl_open failed for default: No such device

Thanks for any help you might have!!!

---

