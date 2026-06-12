---
title: "Sound goes quiet when new movie played"
date: 2009-07-21
forum: Mythbuntu
---

### Post by chipppy on 2009-07-21
**[SOLVED with thanks]**

Good Evening

I have yet another weird problem with my Mythbuntu HTPC

When I start a movie the sound goes quiet.  After a lot of looking around I finally have what is happen sort of figured out but I dont understand why or how to fix.

What happens is the volume is automagic reduced/set to approx 60%.  I can use **aumix** (terminal sound mixer application) to increase the volume back up to 100% and all is good again.
I then play another movie and the volume is set to 60% again.

This is an easy but very annoying fix.  I would like to permanently stop the volume from being adjusted.

The reasoning is that I run the sound through my amp and I also run the radio through the amp.  If the kid wind up the amp volume to watch a movie then when I put on the radio or a LP (old black record for those to young to have seen one before) it blasts the widows out.  If the Mythbuntu volume is at 100% then various sound sources are all the same and I never need to adjust the amp volume.

Any and all assistance is greatly appreciated.

Cheers
chipppy

---

### Post by trevs.bronco on 2009-07-21
I came across the setting for that the other day, iirc it is in the frontend settings for the video player, I'd have a look for exactly where it is, but i'm not infront of a frontend machine right now. I think the default was 75%.
 
Trev

---

### Post by chipppy on 2009-07-22
Good Morning

I must be going blind.  I have looked through the video setting and I am unable to spot something that looks like the culprit.  

Can you please have a look through and tell me what I am looking for.

Thanks for the assistance

Cheers
chipppy

---

### Post by chipppy on 2009-07-26
Good Evening

After much searching i have finally found this setting it is located at

Utilities/Setup ==> Setup ==> General ==> Pages 3
About 2/3 of the way down there is a slider called 'Master Mixer Volume'  


I found that this was set to approx 70%.  Wound it all the way up to 100% and all is fixed.


Cheers
chipppy

---

