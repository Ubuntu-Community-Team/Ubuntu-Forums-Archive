---
title: "Audigy 2 ZS Notebook"
date: 2008-05-20
forum: Multimedia Software
---

### Post by moot1 on 2008-05-20
Hi there, 


I have a faulty onboard audio card that cracks and hisses very often, which is why I bought a creative card. But the problem is audio is coming through the onboard audio card instead of my creative card. I checked the search function and the best I could come up with is that the onboard audio needs to be disabled? If I am unable to resolve this issue I'm afraid I'll have to uninstall ubuntu. :(

I am not very tech savy and just installed ubuntu a couple of minutes ago. 


Any help would be great.

Edit:

I found this code, and I believe substituting the names of my onboard card and pcmcia card will disable my onboard card, and have audio go to my pcmcia card?

How can I find out the names of the card, and check to see if my pcmcia card recognized at all?

options snd-emu10k1 index=0
options snd-intel8x0 index=1

---

