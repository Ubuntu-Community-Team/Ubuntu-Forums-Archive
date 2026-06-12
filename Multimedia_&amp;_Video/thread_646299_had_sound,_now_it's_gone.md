---
title: "had sound, now it's gone"
date: 2007-12-21
forum: Multimedia &amp; Video
---

### Post by monkeyking on 2007-12-21
Hi,
earlier this day,
I ad very nice functioning sound.

Now it's gone,
anyone have any idea why_

thanks in advance

---

### Post by nieekou on 2007-12-21
same here. though i did have sound, on both my sound cards (onboard ac97 something and Maudio audiophile 2496), now only the on board works.
what i used to do (ever since 6.10), is set the default card in asoundconf. i typed
asoundconf list (to get the system names for the sound cards)
and then 
asoundconf set-default-card M2496 (for M-audio)
since last night, the on board is suddenly the default card on everything, and the above tip won't work anymore. then, i went to the sound properties from the system tab, and try to set it frmo there. when i selected the Maudio card on the sound playback (it was set in automatic), and press set, i get this message 
"audiotestsrc wave=sine freq=512 ! audioconvert ! audioresample ! gconfaudiosink: Could not open resource for writing."

i suspect that something updated since last night, but i don't know what, or that to fix it :(

---

### Post by monkeyking on 2007-12-22
> **nieekou said:**
> 
... i went to the sound properties from the system tab, and try to set it frmo there....
(

I think my problem is related to me disabling the onboard modem,
so i don't thing our problems are related.

but which system tab are you talking about?

---

