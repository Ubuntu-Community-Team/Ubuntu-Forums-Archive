---
title: "Surround Sound in 9.04  with creative x-fi"
date: 2009-05-14
forum: Multimedia Software
---

### Post by jasone on 2009-05-14
I managed to install my soundcard driver but i cant make my 7.1 speakers to work surround. I tried instructions in this thread [http://ubuntuforums.org/showthread.php?t=795525 ]("http://ubuntuforums.org/showthread.php?t=795525")but it doesnt work. There is not an option in ALSA volume control for Side and rear speakers neither in preferences.
Any ideas?
Should i switch to OSS?

Thank u

---

### Post by ElementTi on 2009-05-18
Hey,

Go to System -> Administration -> Synaptic Manager, search for "pulse". Remove all items
associated with pulse. Compile the Creative X-Fi driver. Go to Synaptic Manager and search for pulse again. Install everything related to the search. 

Go to Applications -> Sound and Audio -> PulseAudio Control your card should be listed and at least 5.1 will work. Let me know if this helps.

---

### Post by ElementTi on 2009-05-18
Also, put in a CD to test and open the PulseAudio Volume Control click the Playback tab it should list all of your speakers.

---

### Post by jasone on 2009-05-18
After many days of googling i managed to make my 7.1 speakers to work with ALSA. I could not do this with Pulse.  I upgraded ALSA to version 1.0.20 using these instructions [http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)  and i downloaded the unstable x-fi driver from the ALSA site. After the driver installation the driver works fine and i can see all my speakers in alsamixer.

---

### Post by catphive on 2009-06-16
Could one of you put together a guide or something? It sounds like both of you have figured out different ways to get surround sound working with x-fi, but I don't think I can reproduce given the limited information here.

What's the point of adding then removing packages? Which ones specifically?

I just need to get 5.1 working so if you know how I would love to hear about it...

---

### Post by MrPasty on 2009-06-25
> **catphive said:**
> Could one of you put together a guide or something? It sounds like both of you have figured out different ways to get surround sound working with x-fi, but I don't think I can reproduce given the limited information here.

What's the point of adding then removing packages? Which ones specifically?

I just need to get 5.1 working so if you know how I would love to hear about it...
Same here! I would love 5.1-sound from my X-Fi, but have always thought it as impossible.

---

### Post by vhurry200@aim.com on 2009-06-30
USE THE LATEST VERSION OF ALSA:
[http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/](http://monespaceperso.org/blog-en/2009/05/09/upgrade-alsa-1020-on-ubuntu-jaunty-904/)

THEN LOAD THE XFI DRIVER:
[http://wiki.debian.org/X-Fi](http://wiki.debian.org/X-Fi) OR [http://www.kernel.org/pub/linux/kernel/people/tiwai/snapshot/](http://www.kernel.org/pub/linux/kernel/people/tiwai/snapshot/)

NOW I AM GETTING 7.1 SURROUND ON UBUNTU 9.04

---

### Post by catphive on 2009-07-04
Could you clarify?

1. You don't use the Drivers from the creative website. Why is that? Are an updated version of those included in alsa?

2. You install alsa 1.0.20 in link 1, then in link 2, you download some alsa driver snapshot and install those drivers.

Why aren't those drivers included in 1.0.20 that we just downloaded? Is 1.0.20 really necessary for installing these drivers? What's the connection?

Thanks,

---

### Post by GingersK on 2009-07-27
Has anyone had any luck getting surround sound to work with a x-fi card?

---

### Post by hyperAura on 2009-07-27
hey jasone just out of curiosity which speakers do u have? if it is creative do u have the software mediasource go!?

---

### Post by xjgnsdof on 2009-08-23
I am pleased to report that I now have true 5.1 surround sound on a Creative X-Fi XtremeGamer in 64-bit Ubuntu 9.04 after following the above instructions re: upgrading ALSA and installing the ALSA X-Fi driver.

For the sake of completing this discussion, I must remind you to set every dropdown setting in Sound Preferences to "ALSA - Advanced Linux Sound Architecture" and the Default Mixer to "Creative X-Fi (Alsa mixer)." Also, in Volume Control, raise all volume sliders to the max for initial testing purposes.

This should be marked as solved and/or made stick, btw.

---

