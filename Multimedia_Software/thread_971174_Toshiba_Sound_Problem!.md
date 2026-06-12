---
title: "Toshiba Sound Problem!"
date: 2008-11-04
forum: Multimedia Software
---

### Post by Toshibawarrior on 2008-11-04
Well, I've been messing with ubuntu for almost a year, and last night I decided to use Kubuntu...and what a great version of ubuntu this is!

I just have one problem...sound sucks on my Toshiba Satellite A135-S4527....It sounds thin, tinny and very very low...

I added the "**options snd-hda-intel model=lenovo**" to "**/etc/modprobe.d/alsa-base**" and that revived my sound, but it sounds sucky...so I tried the Pulseaudio fixes posted by psyke83 in this forum like I always do on a fresh install of Ubuntu and they didn't work at all...in fact I had to make a fresh install of Kubuntu again...

So any help will be greatly appreciated! I'm always listening to music on my laptop, and this sound is horrible...I miss my equalized ALSA-Pulsaudio sound...

So if anyone has any input on this let me know!!!

Thanks in advance! :popcorn:

---

### Post by Toshibawarrior on 2008-11-20
BUMP?!.......please

---

### Post by psyke83 on 2008-11-20
Kubuntu doesn't use PulseAudio.

Look at the PulseAudio guide, Appendix D.

Create the ~/.asoundrc file as described in that section, but change the text marked in blue from "plughw" to "plug:dmix".

Also add to the end of this file:
```
pcm.!default {
 type plug
 slave.pcm "equalizer"
}
```

All ALSA applications should now use equalized sound by default (but you may hear distortions when mixing sounds, unfortunately).

---

### Post by Toshibawarrior on 2008-11-20
THANK YOU!!! As soon as I make an extra partition I'll reinstall Kubuntu and try this! Although I liked openSUSE with KDE more than Kubuntu, but I dunno if I'll wait for the new release.

Thanks again psyke83! Keep up the great work!

---

### Post by mostholy on 2008-11-28
okay, I'm missing something here.  I have the same hardware and a fresh install of 8.10 and I've got silence from the speakers.  Was there something I'm overlooking?  I tried the addition of the line to my alsa-base file but to no avail.  

thanks.

---

### Post by Toshibawarrior on 2008-11-28
If you're using KDE add the line and reboot your machine. I can't help you very much outside of that because I still haven't got to reinstall Kubuntu/KDE on my laptop.

You may check you **kmixer** too. Make sure everything is all the way up and test with some tunes. 

Let me know if something changes...:)

---

### Post by mostholy on 2008-11-28
okay, followed your lead and had the speakers chime when I went into reboot but silence since then.  I've got the alsamixer up across the board but amarok does not play a cd through the speakers.  Appreciate any further thoughts....

---

### Post by Toshibawarrior on 2008-11-29
Hmmm...weird...Try installing **kubuntu-restricted-extras** (if you're in kubuntu) from Synaptic and try playing the CD again.

Also, check the Sound options in YaST and make sure that **HDAxxXXxxXX** is selected as the output device...the one that says HDA and ALSA somewhere in the name.

It' very strange, it's supposed to work with no further fixes, but it will sound crappy and tinny,....you'll need to configure PulseAudio for that.

Anyways, inform me of any new changes.

---

### Post by mostholy on 2008-11-29
Not sure exactly what fixed things but did reboot a few times and readjusted the sound in Kmixer (it was at full volume to start with but tweaked it around a few times) after adding the line to alsa-base you started this thread with.  

Now I'm ready to make the sound less tinny.  Can you link me to your PulseAudio advice?

thanks in advance

---

### Post by Toshibawarrior on 2008-11-29
Here's the guide I use for adjusting Pulseaudio:

[http://ubuntuforums.org/showthread.php?t=789578&highlight=unnecessary+files]("http://ubuntuforums.org/showthread.php?t=789578&highlight=unnecessary+files")

It's pretty easy to follow. Check it out!

And check out this post:

[http://ubuntuforums.org/showpost.php?p=6219751&postcount=3]("http://ubuntuforums.org/showpost.php?p=6219751&postcount=3")

---

