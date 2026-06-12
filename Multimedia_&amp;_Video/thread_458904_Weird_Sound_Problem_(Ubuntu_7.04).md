---
title: "Weird Sound Problem (Ubuntu 7.04)"
date: 2007-05-30
forum: Multimedia &amp; Video
---

### Post by Astrodemoniac on 2007-05-30
Using Ubuntu Feisty and it rocks! :) I am having a bit of an issue though 

I have 3 sounds cards on my system:

**_My System_**

Integrated (AC97 Asus A8nDlx) Detected as Sigmatel bla bla (not interested, disabled in BIOS anyway)
Sound Blaster Audigy2Zs(Detected with ALSA)
Terratec Aureon 7.1 PCI Dolby Digital Live(Detect as CMI8738)

**_Problem Background_**
Initially my problem was with the order of the default card. For some reason Ubuntu kept randomly switching the order in which the Sound cards were enumerated everytime I rebooted; curiously though, this only happened between Audigy and Terratec; the onboard sound always stayed third. Anyway, my speakers are connected to the terratec card through the Optical out so of course if the default card was the Audigy, I lost sound.

I managed to fix that problem by manually setting the Terratec Card to grab the 0 index in the alsa base files. 

**_The problem_**
Now that the terratec card is set to always be index 0, instead of randomly switching places with the Audigy card, it just randomly disappears:-?. It's just a matter of rebooting and voila it's back...reboot again and maybe it's gone again, maybe not... it really is random.


Of course I do not want to report a bug for a problem that may well be a configuration error on my part, but I do need some help solving this majorly PITA issue :)

Any help would be highly appreciated 

Thanks :)

---

### Post by eye208 on 2007-05-30
> **Astrodemoniac said:**
> I managed to fix that problem by manually setting the Terratec Card to grab the 0 index in the alsa base files.

Now that the terratec card is set to always be index 0, instead of randomly switching places with the Audigy card, it just randomly disappears:-?.
It's not sufficient to assign a static index to only one of the cards. Whenever the system detects the Audigy first, it will still be assigned index 0. The only difference now is that the Terratec will only work if it is detected first, because it won't accept an index other than 0.

So the solution is to assign static indices to all three cards. This will make sure that the Audigy, even if detected first, will grab an index other than 0, leaving that one free for the Terratec.

---

### Post by Astrodemoniac on 2007-05-30
Oh, ok. Doh! I didn't think of that:-x  makes perfect sense. I'll try it when I get home thanks!:D

---

### Post by Astrodemoniac on 2007-05-30
Seems to work a treat. Thanks a lot :)

---

