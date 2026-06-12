---
title: "trying to install OSS killed my sound! I can't revert back to alsa."
date: 2009-04-05
forum: Multimedia Software
---

### Post by kylescha on 2009-04-05
I have the Ubuntu 9.04 beta. Against my better judgement, I went out to buy an x-fi notebook card for my laptop in hopes that maybe i could get it to work (i know some people have been successful). However, after unsuccessfully installing OSS, I decided to scratch this whole thing and return it. However, every guide I have tried to revert back to alsa has not worked. 

Still, when I try aplay -l i can't get it to recognize the sound card, however when I show the list of devices, the onboard audio is shown. 

I've tried purging/reinstalling alsa, but nothing seems to work. I have got it to where under sound preferences it shows the device but then says (not connected) after it. 

I know it uses the hda-intel driver. 

Some help would be hugely appreciated. I've tried everything short of reinstalling ubuntu. If I do this do I lose everything? Is there a way to reupgrade to 9.04 again so it downloads the whole distribution again?

---

### Post by theozzlives on 2009-04-05
> **kylescha said:**
> I have the Ubuntu 9.04 beta. Against my better judgement, I went out to buy an x-fi notebook card for my laptop in hopes that maybe i could get it to work (i know some people have been successful). However, after unsuccessfully installing OSS, I decided to scratch this whole thing and return it. However, every guide I have tried to revert back to alsa has not worked. 

Still, when I try aplay -l i can't get it to recognize the sound card, however when I show the list of devices, the onboard audio is shown. 

I've tried purging/reinstalling alsa, but nothing seems to work. I have got it to where under sound preferences it shows the device but then says (not connected) after it. 

I know it uses the hda-intel driver. 

Some help would be hugely appreciated. I've tried everything short of reinstalling ubuntu. If I do this do I lose everything? Is there a way to reupgrade to 9.04 again so it downloads the whole distribution again?

Ubuntu 9.04 is not for production machines yet (hence "Beta"). If you have a seperate /home partition, you can re-install without losing your files and settings.

---

### Post by kylescha on 2009-04-05
Yeah, I understand that. And thats fine if I messed it up and I have to wait a few weeks. Is this why some of the updates for alsa isn't working?

Also, when the full version comes out will it be the entire system or will it just be a series of update?

---

