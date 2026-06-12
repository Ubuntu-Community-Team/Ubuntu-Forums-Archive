---
title: "Cannot play wav files ???"
date: 2009-03-27
forum: Multimedia Software
---

### Post by deb2006 on 2009-03-27
In Intrepid I seem to be unable to play and listen to wav files. aplay gives the error message: 

aplay: set_params:954: Sample format non available

And totem has: 

GStreamer encountered a general stream error.

Anyone?

---

### Post by jordilin on 2009-03-27
pretty strange, as I can listen to wav files. Could you open a terminal and type:
```
file filename.wav
```
and show the output.

---

### Post by elliotn on 2009-03-27
Ja strage as I too can play wav without hustle

---

### Post by deb2006 on 2009-03-27
> **jordilin said:**
> pretty strange, as I can listen to wav files. Could you open a terminal and type:
```
file filename.wav
```
and show the output.

03 - Audience.wav: RIFF (little-endian) data, WAVE audio, Microsoft PCM, 24 bit, mono 22050 Hz

Hm ---- I also cannot play CDs therefore (well, naturally I cannot play them, since they display as wav files ...)

---

### Post by deb2006 on 2009-03-27
> **deb2006 said:**
> In Intrepid I seem to be unable to play and listen to wav files. aplay gives the error message: 

aplay: set_params:954: Sample format non available

And totem has: 

GStreamer encountered a general stream error.

Anyone?

Ok, apparently I have tried to rip them from a CD with sound-juicer - and sound juicer seems to be broken. When I copy a file directly to my Desktop it plays with aplay. Totem seems still to be unable to play that wav file - it only shows "0:00 (Streaming)" in the lower left corner.

---

### Post by jo4hnc on 2009-03-27
Try going to Applications>Add/Remove. Look for the GStreamer plugins for mms, wavpack, quicktime, musepack. I'm pretty sure this might solve the problem. If not check out the other Gstreamer plug in packs in Add/Remove or Synaptic to see if there's something there that might resolve your issue.

---

### Post by Stochastic on 2009-03-28
Moved to Multimedia & Video

---

### Post by bimmermz3 on 2009-03-29
i'm having a similar problem.  i can play the cd, but i cannot copy or even try to convert to mp3 with "sound converter".  it shows in the prog. but it will not let me select it.  i have downloaded the GStreamer packages....any more suggestions?

---

### Post by jo4hnc on 2009-03-29
Have you tried Audio CD Extractor? If you don't already have it in your Sound and Media Application menu, you can get it by going to ADD/REMOVE. You can set the file type you want to convert the music to in preferences.

---

### Post by logos34 on 2009-03-29
> **bimmermz3 said:**
> i'm having a similar problem.  i can play the cd, but i cannot copy or even try to convert to mp3 with "sound converter".  it shows in the prog. but it will not let me select it.  i have downloaded the GStreamer packages....any more suggestions?

If you use Sound Juicer (aka 'audio-cd extractor'), be sure to get the -bad and -ugly suggested pkgs as well (->mp3 support)
> 
sudo apt-get install sound-juicer ubuntu-restricted-extras eject

---

### Post by jo4hnc on 2009-03-29
> **logos34 said:**
> If you use Sound Juicer (aka 'audio-cd extractor'), be sure to get the -bad and -ugly suggested pkgs as well (->mp3 support)

My bad! Forgot to mention that.

---

### Post by bimmermz3 on 2009-03-29
thanks alot guys!  i set it up to save as a .m4a type. everything works great.  i was being a noob and was looking for sound-juicer and with your help i went for the audio extractor.  
thank you again

---

### Post by jo4hnc on 2009-03-29
Enjoy!

---

