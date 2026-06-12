---
title: "Disabling a sound card"
date: 2007-01-22
forum: Multimedia &amp; Video
---

### Post by Sarah13 on 2007-01-22
Hi all.

In an effort to get the sound to work on my computer (see[ this post]("http://www.ubuntuforums.org/showthread.php?t=289408") for the explanation) I want to disable one of my sound cards. I think the problem is that they are both are enabled, and therefore the computer is a bit confused and no sound emerges. When I enter```
cat /proc/asound/cards
0 [AudioPCI       ]: ENS1371 - Ensoniq AudioPCI
                     Ensoniq AudioPCI ENS1371 at 0xd800, irq 5
1 [Live           ]: EMU10K1 - SBLive 5.1 [SB0060]
                     SBLive 5.1 [SB0060] (rev.7, serial:0x80611102) at 0xe400, i rq 12
 
```

That's what I get. According to [this FAQ]("http://alsa.opensrc.org/FAQ026") it says that the primary sound card, or the one in use, is indicated by a ```
irq
``` and both of my sound cards have that, leading me to believe that both are enabled. I also want to set the default to the SB Live.

This is what the FAQ said to do.
> Ok, if you want to change the default device on your soundcard, you need to edit your ~/.asoundrc 


How do I do that? Where is the file located and should I 'cd' into it?

Sorry if the answers are really obvious, I'm still a newbie. :D

---

### Post by budgie9 on 2007-01-22
You would be better off disabling the sound card on the m/board itself and using the SB as it gives a better sound, to my mind. 
You can do this in two ways. 
You can disable the on board sound card in the BIOS or better still, look in the manual for your m/board and move the jumper the disables the internat sound card.
This way you will free up the used IRQ so your SB card can use it and it will give you less troubles.

---

### Post by Sarah13 on 2007-01-22
> **budgie9 said:**
> You would be better off disabling the sound card on the m/board itself and using the SB as it gives a better sound, to my mind. 
You can do this in two ways. 
You can disable the on board sound card in the BIOS or better still, look in the manual for your m/board and move the jumper the disables the internat sound card.
This way you will free up the used IRQ so your SB card can use it and it will give you less troubles.

I don't have the manual so I disabled the on board sound in the bios, but I'm still not getting any sound. 

Do you have anymore suggestions?

---

### Post by budgie9 on 2007-01-22
You are probably going to have to go the through the settings via the volume control.
Make sure your SB card is selected, by checking through the menus options of that program. Sorry can't see it at this time, to give you better guidance  as I am in XP, yuk. But do those checks paying attention to the PCM control being up high, as well as the master control.

---

### Post by Sarah13 on 2007-01-22
> **budgie9 said:**
> You are probably going to have to go the through the settings via the volume control.
Make sure your SB card is selected, by checking through the menus options of that program. Sorry can't see it at this time, to give you better guidance  as I am in XP, yuk. But do those checks paying attention to the PCM control being up high, as well as the master control.

Thanks. I've also tried that though, even going so far to test random combinations to see if that would make it work. My PCM and master volume are all at 100%.

Anything else I can try? I was looking at a FAQ on how to install the SB 5.1 card from scratch, but the problem is I already have most of it done, and I don't want to double load it.

So in my mind, the next logical step would to completely uninstall SB 5.1 card through terminal, then using [THIS]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Creative+Labs&card=Sound+Blaster+Live+5.1.&chip=emu10k1&module=emu10k1#Inst")
completely reload it from scratch. Afterall, there's not much to lose.

Unless there's another option out there, I think that is what I should try to do.

So then the question becomes, how do I uninstall it completely?

---

### Post by Erlander on 2007-01-23
Have you tried System/Preferences/Sound and selected your card rather than leaving it on Auto?  You can test it there too.

Rob

---

### Post by Bobcatben on 2007-08-20
iam looking for a way todo this as well, iam running a motherboard that has onboard audio(which i use for my headset in windows) and a sblive for my speakers, the problem is in the 32bit version of ubuntu my onboard audio is default, and the most ive been able to get it todo is to have the system sounds come out it, and the volume control to use it, other then that i have to manually change the option for every single program that does sounds(which alot of programs dont have the option, games, flash, firefox etc), yet, in the 64 bit version, the sound works perfectly out the sb live with absolutely no changes to settings, but i cant run that cause the 64bit nvidia driver still blackscreens me.

---

