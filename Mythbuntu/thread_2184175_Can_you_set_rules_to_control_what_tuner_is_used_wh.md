---
title: "Can you set rules to control what tuner is used when recording?"
date: 2013-10-27
forum: Mythbuntu
---

### Post by benlyboy on 2013-10-27
Hi all looking for some info.

I have a system with 4 analog tuners, and I just got a HDhomerun prime. With our cable most of the lower channels can be viewed with a analog tunner but the upper channels need a cable card.  So what I want to know, is can I set up my system so as to make it use the analog tuners for the lower channels there by saving the HDhomerun for upper channels?

At the same time i don't want to completely stop the homerun from being used. If the wife needs 5 things on the lower channels taped i want it available,  or I may be in trouble :)   

thanks for your thoughts :)

---

### Post by newlinux on 2013-10-29
First, I'm not sure if you need to do this. If you have a situation where you have multiple simultaneous recordings and 1 of them is only available on a channel associated with the video source of your HDHR Prime mythtv will know to use the HDHR Prime and use the analog tuners for the other recordings (assuming you haven't messedwith any chennel or input priorities). IF you want your tuners used in a certain order delete all your cards and then create the cards and input connectionsin the order you want them to be used - starting with your highest priority card (sounds like you'd want to add your analog tuners first).

---

### Post by benlyboy on 2013-10-30
Thanks newlinux for your help...

If I read what you posted correctly, I should be in good shape. If i go ahead and just add the homerun to my system, it will be been added after the analog tuners so they should be used first.

Do i have that right..?

One other question do I need to set up a separate video source for the homerun or can i use one source for all the tuners ? 

thanks again

---

### Post by mtbdrew on 2013-10-31
Yes you can set the preference for what card is used. This is done under recording rules preferences. Don't remember the exact location but it is there that you set the card number for the recording. However, use caution as this can lead to conflicts between different recordings. Best to let the system handle the allocation itself as much as possible.

---

### Post by newlinux on 2013-10-31
> **benlyboy said:**
> Thanks newlinux for your help...

If I read what you posted correctly, I should be in good shape. If i go ahead and just add the homerun to my system, it will be been added after the analog tuners so they should be used first.

Do i have that right..?

One other question do I need to set up a separate video source for the homerun or can i use one source for all the tuners ? 

thanks again

Yes you have that right. As mentioned above, you can specify input preferences for individual recordings in the recording rule - you can even set an input to have an overall higher or lower priority, or even a channel, but this may cause you some unintended consequences and I don't believe it is necessary for what you want to do.

If they all have access to the same channels use the same video source. I think in your case you will need two video sources -- one for your analog tuners and one for your prime. If you want certain recordings to be able to record on either type of tuner you need to be careful about how you setup the recording rule and the channels in the video sources (e.g. don't specify it record on a channel that doesn't exist on both video sources).

---

