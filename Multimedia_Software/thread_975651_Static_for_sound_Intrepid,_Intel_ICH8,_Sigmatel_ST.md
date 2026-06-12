---
title: "Static for sound: Intrepid, Intel ICH8, Sigmatel STAC9271D"
date: 2008-11-08
forum: Multimedia Software
---

### Post by stormzen on 2008-11-08
I've been reading up on sound problems for far too long.  I'm nearing the point to accepting linux-driven-deafness again, but I seem to really the hearing sense.

I took a look at a stickied comprehensive guide to sound problems.  It was dated 2006.  I make it a point not to follow guides that are years old in Linux, as it is a good way to mess up things where solutions have since been made.

I saw another link for getting sound to work for Gutsy: [https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller](https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller) ... surprisingly, Gutsy was the last version where sound did work properly for my config.

I've asked on #ubuntu.  No one had anything to say.

I checked out #pulseaudio.  Best advice I got there was this pasuspender.  In theory, as I hear static when I issue: pasuspender madplay mp3file.mp3, it's ruled out pulse-audio, right?

I consulted #alsa.  They told me to quit all of my audio programs and work from there.  This was sound advice.  ( No pun originally intended. ), as one of the symptoms is fluctuating background static.  So I asked #ubuntu how to determine all the audio software that needed to be shut down.  No one answered.

In my research on sound, I have learned that there are many different software packages that seem to implement sound in different ways.  And they can conflict.

I'd like to start from the beginning -- silence.  ( The kind from my speakers, not responses. )  Can someone tell me how to kill all sound and how to activate the many players to see which ones are involved in the fighting?

Many thanks --

---

