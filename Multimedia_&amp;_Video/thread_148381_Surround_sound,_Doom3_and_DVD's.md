---
title: "Surround sound, Doom3 and DVD's"
date: 2006-03-22
forum: Multimedia &amp; Video
---

### Post by drobvice on 2006-03-22
I have installed Doom 3 on ubuntu (gnome) and when I switch from stereo to surround in the settings, the music is garbled.  My card is C-Media 8738 using alsa mixer.  In Multimedia Systems Selector, both the Default Sink and Default Source are set to Alsa.  In Volume Control Line In is "Bass Mode", Mic In is "Center/LFE" and both are unmuted.  Also, the command  "speaker-test surround51 -c6" gives me no sound.  Before I changed some the settings, I got noise with this command but the front and rear channels acted as one.  I still have system sounds and as far as I can tell, 5.1 is working in xine.  Not sure what to do.  I have seen a number of suggestions and some were for Hoary.  Specifically this one... [http://www.ubuntuforums.org/showthread.php?t=44753&highlight=surround+sound](http://www.ubuntuforums.org/showthread.php?t=44753&highlight=surround+sound) but the poster mentioned doing this for AC97 sound.  Also, I just now am noticing that when the DVD movie starts playing, the channels get really quiet and I have to turn the volume up really loud.  The menu music is fine and normal volume.  Any suggestions?

---

### Post by shelbydz on 2006-03-25
1 idea is to make sure the GAME volume setting is NOT all the way up. I seem to remember having the same prob when I had it installed, and that fixed it.

---

### Post by drobvice on 2006-03-26
I thought you were on to something with that but it didn't seem to help.  I found a driver on the cmedia website with a couple of kernel patches (latest patch is 2.6.4).  Maybe if I can figure out how to install it, I'll give it a shot.  Also, I assume you meant the voume slider in the game settings and not a system volume control labeled "GAME".

---

