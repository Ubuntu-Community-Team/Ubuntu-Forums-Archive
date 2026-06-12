---
title: "Soundconverter adding clicks and pops"
date: 2009-04-26
forum: Multimedia Software
---

### Post by wastvedt on 2009-04-26
Hi.
  I've been on a mission recently to clean up my music library. I've come across several wma albums, burned in my earlier Windows days, which I converted to ogg using soundconverter. I then noticed in rhythmbox and Movie Player that the songs contain annoying pops or clicks. Is there a fix? Is this documented? Any ideas, or more info I should provide? Thanks for the help.

---

### Post by Sin@Sin-Sacrifice on 2009-04-26
I'd say try converting the wma files again using audacity. Always worked well for me. Alternatively, provided you still have the wma files, you can use vlc and a few other linux apps to play them. Also, if you have the cd, you can re-burn it straight to ogg. Once the audio file has those "pops" they, to my knowledge, cant be fixed without pretty sophisticated software and even then the stream becomes distorted. There is software provided in ubuntu studio for all types of audio manipulations.

---

### Post by wastvedt on 2009-04-26
Hey, thanks for a quick reply!
Certainly in the future I will use some other method. I guess my main question was with soundconverter in particular. It is a very convenient program (when it works). Is this something I should report as a bug?
Thanks!

---

### Post by quisnox on 2011-05-15
> **wastvedt said:**
> Hey, thanks for a quick reply!
Certainly in the future I will use some other method. I guess my main question was with soundconverter in particular. It is a very convenient program (when it works). Is this something I should report as a bug?
Thanks!
It's not a converter bug! Try listening file on Audacious... It's something wrong with gstreamer. All players who using it, plays music with clicks, when it's in ogg format. Try listening *silently*.

---

### Post by The Woozy Fieldmouse on 2011-06-05
This sucks. Now all my ogg files are suspect. I've tried just listening through the popping, but it's driving me nuts and I can't remember which files pop and which don't. It seems random. Did I this sucks already? *tears hair*

edit: I don't seem to be hearing the same pops when played back through  my Mint desktop as I do when I playback through my Android smartphone? Is it possible that he pops are not actually in the data itself but are being created during playback by gstreamer?

---

### Post by Steeperton on 2011-06-06
> **The Woozy Fieldmouse said:**
> This sucks. Now all my ogg files are suspect. I've tried just listening through the popping, but it's driving me nuts and I can't remember which files pop and which don't. It seems random. Did I this sucks already? *tears hair*

edit: I don't seem to be hearing the same pops when played back through  my Mint desktop as I do when I playback through my Android smartphone? Is it possible that he pops are not actually in the data itself but are being created during playback by gstreamer?

Yes. Listen in vlc, and there's no clicks/skips. If you use rhythmbox, use the crossfading backend option, with crossfade time set to 0. All works fine then.

---

