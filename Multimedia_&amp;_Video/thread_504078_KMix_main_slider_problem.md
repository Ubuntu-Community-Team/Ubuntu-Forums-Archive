---
title: "KMix main slider problem"
date: 2007-07-18
forum: Multimedia &amp; Video
---

### Post by FSHero on 2007-07-18
Hi all,
I use Kubuntu Feisty Fawn (kick-***!), but have a problem with controlling sound volume.
When I single-click on KMix to show the single slider (I shall call it "main"),  the volume it changes is that of the "PC Speaker", not of the "PCM". However, the PC Speaker doesn't seem to control anything useful.

Subsequently, when using the Volume up/down buttons on my keyboard, there is no effect.

Is there any way to change the main slider to control PCM, which *does* have an effect on sound volume? (I believe that this would fix my keyboard Volume up/down buttons too.)

Finally, there is no Master volume, which would be useful (to be mapped to the main slider). Why am I not seeing it?

Attached: lsmod output, screenshot of KMix.

If more info is needed, I would be happy to provide it.
Thanks in advance!

---

### Post by FSHero on 2007-12-14
Five months later, and I have fixed the problem! I right-clicked the KMix icon in the System Tray, and then clicked Select Master Channel. I changed the radio button from PC Speaker to PCM. (See the attached picture.) Now, the volume and mute hotkeys control the 'wave'/PCM output just like I wanted, plus the balance control in KMix works too.

My Windows-liking brother actually found this, after attempting to bind my keyboard's hotkeys to the volume (which now works, of course). I can't believe I didn't see this... but I am also disappointed that no other user of Kubuntu who reads this forum didn't even reply, let alone give a solution.

Nevertheless, I am happy now, and hope that this information will help others.

---

