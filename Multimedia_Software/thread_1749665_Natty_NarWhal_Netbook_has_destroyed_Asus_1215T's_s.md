---
title: "Natty NarWhal Netbook has destroyed Asus 1215T's sound."
date: 2011-05-04
forum: Multimedia Software
---

### Post by Swashy on 2011-05-04
My sound worked fine for the first few days.. then I noticed the mic wasn't working in skype so I tried messing with it in sound preferences. Now my speakers explode with this horrible distorted noise(semi-recognizable as whatever I'm trying to play) and sometimes freezes when I try to play any sound. Reinstalling just the drivers to avoid a fresh install, according to the stickied thread at the top, did nothing. Attempting to place the settings back to their defaults also does not appease this bloodthirsty beast.

I've been on a rampage through every lead I've found on trying to fix this problem but nothings worked so far.. it seems the problem is that the onboard speakers (Internal Audio; Analog Surround 4.0 Output) hates it's life in an Ubuntu OS too much to continue living. Not sure if the RS880 Audio Device [Radeon HD 4200] output is ******* with it either. Any suggestions? 

Also heres my.. file report thingy(alsa-info.sh): [http://www.sendspace.com/file/wua02m](http://www.sendspace.com/file/wua02m)
The laptop in question: [http://www.newegg.com/Product/Product.aspx?Item=N82E16834220857](http://www.newegg.com/Product/Product.aspx?Item=N82E16834220857)

Any help is of course *greatly* appreciated. Well, as long as you don't tell me I need a new laptop.

**BREAKING NEWS! I'M RETARDED!** Looked in the other thread next to this one about the 1215t mic problem (which I also am having problems with) and aparently I didn't try **duplex mode** for my internal audio. Its fixed now!

---

### Post by HDave on 2011-05-04
I have exactly the same problem...what is this "duplex mode" and how to do I set it up!?!?!!?  :confused:

---

### Post by lidex on 2011-05-05
> **HDave said:**
> I have exactly the same problem...what is this "duplex mode" and how to do I set it up!?!?!!?  :confused:
Click on the volume/speaker icon in the panel and select 'Sound Preferences'. 
Cick on the 'Hardware' tab, choose the correct device, 
then select the analog-stereo-duplex profile at the bottom.

---

