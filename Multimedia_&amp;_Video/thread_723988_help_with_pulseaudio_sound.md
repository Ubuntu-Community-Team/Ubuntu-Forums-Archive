---
title: "help with pulseaudio sound"
date: 2008-03-14
forum: Multimedia &amp; Video
---

### Post by rockyraccoon on 2008-03-14
running gutsy with pulseaudio 0.9.9. i have 2 soundcards: the onboard one (ALC882) and a pci card (m-audio delta 1010, which has ice1712). i can get it to output sound to the onboard card but not the delta 1010. 

i tried blacklisting the snd_hda_intel module so that ubuntu wouldn't load the ALC882, which had the effect of eliminating any way for me to playback sound.
without pulseaudio or esd, the the delta1010 will work for most applications, i can play music and connect to it using jackd. i can't get pulseaudio to acknowledge its existence. any suggestions?

---

### Post by rockyraccoon on 2008-03-18
bump*

---

### Post by tkiesel on 2008-03-20
> **rockyraccoon said:**
> running gutsy with pulseaudio 0.9.9. i have 2 soundcards: the onboard one (ALC882) and a pci card (m-audio delta 1010, which has ice1712). i can get it to output sound to the onboard card but not the delta 1010. 

i tried blacklisting the snd_hda_intel module so that ubuntu wouldn't load the ALC882, which had the effect of eliminating any way for me to playback sound.
without pulseaudio or esd, the the delta1010 will work for most applications, i can play music and connect to it using jackd. i can't get pulseaudio to acknowledge its existence. any suggestions?

I have the same issue here with pulseaudio in Hardy.  My sound card is an m-audio Delta 410, also using the ice1712 driver.  pulseaudio doesn't seem to want to recognize that the card exists.

[Launchpad bug here]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442").

---

### Post by rockyraccoon on 2008-03-21
thanks for the link, i'm going to try the workaround that you link from there. much appreciated.


edit: the workaround you link there worked for me. i can now playback sound out of my delta 1010. thank you!

---

### Post by tkiesel on 2008-03-23
> **rockyraccoon said:**
> thanks for the link, i'm going to try the workaround that you link from there. much appreciated.


edit: the workaround you link there worked for me. i can now playback sound out of my delta 1010. thank you!

You're welcome.  :)  Now I just hope that the upstream pulseaudio folks can get the pulseaudio autodetect script working with the M-Audio cards!  I'm going to try this workaround right now myself, with the hopes that I can undo my changes later and keep my install as default as possible.

edit:  The [Pulseaudio workaround for M-Audio cards]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/178442/comments/7") was successful for me too.  Still hoping that this can get some attention and a fix by the upstream Pulseaudio folks.

---

