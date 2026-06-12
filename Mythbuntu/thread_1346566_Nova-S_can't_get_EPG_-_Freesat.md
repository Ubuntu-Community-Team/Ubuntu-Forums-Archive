---
title: "Nova-S can't get EPG - Freesat"
date: 2009-12-05
forum: Mythbuntu
---

### Post by My Name on 2009-12-05
Hi,
I'm nearly there with my freeview/freesat setup with a little help from my friends here. the last thing I'm having trouble with is getting the guide to work for freesat.
i have it setup to use EIT, which is the same as the freeview, but i'm getting no information.
The card is a nova-s (not plus) with the philips chipset, and is getting channels from the Astra satallite.

Any ideas??

Thanks

---

### Post by My Name on 2009-12-05
Also the only xml grabber option is for north america...

---

### Post by My Name on 2009-12-08
Well I have fixed the problem with the xml guide, I needed to install tvxml;)
Anyway I would still prefer to use the over-the-air EIT info like I do with freeview as I don't think the radio Times is complete, in fact it misses a lot on info.
Maybe if I use the eurobird satellite instead??

Any ideas?

---

### Post by Neon Dusk on 2009-12-08
Are the channels set to use the over-the-air guide?
You can check in MythWeb Settings ->TV -> Channel Info -> useonairguide

Does starting mythbackend with the "-v eit" logging option return any useful details?

---

### Post by SiHa on 2009-12-08
I can't help much other than to say that I have exactly the same card in my 9,10 backend, and I do get EIT data. So it definitely *should* work. Maybe delete the card, setup new sources and rescan?

---

### Post by My Name on 2009-12-09
I have set it up to receive the EIT in fo but It didn't work.
Is your card the one with the philips chip?
I have tried a number of times with no luck.
What channels do you get info for?

---

