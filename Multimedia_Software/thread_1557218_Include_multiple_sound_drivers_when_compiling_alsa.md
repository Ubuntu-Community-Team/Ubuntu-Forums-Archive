---
title: "Include multiple sound drivers when compiling alsa [Lucid]"
date: 2010-08-20
forum: Multimedia Software
---

### Post by Sintharas on 2010-08-20
Hello!

[COLOR=DimGray]I've recently started to get both my Realtek ALC1200 Onboard and my E-MU 0404 Sound Card to work under Ubuntu Lucid (Scenario under Windows was: All Sound -> Onboard(Headphones), Winamp Music -> E-MU card(Loudspeaker)).[/COLOR]

When I compile the ALSA-Driver with-cards=emu10k1, my E-Mu card works, and when I compile it with-cards=hda-intel, my Onboard Sound works. 

*But how do i compile both into one ALSA-driver?* with-cards=emu10k1, hda-intel    didn't work(only the emu was recognized). [I]
How can I give the with-cards parameter 2 arguments? [/I]
Or is it impossible to use 2 soundcards at the same time for different applications (like standard-sound on card 1, specific application to card 2)?

Thanks in advance for your replies,
Sintharas

---

