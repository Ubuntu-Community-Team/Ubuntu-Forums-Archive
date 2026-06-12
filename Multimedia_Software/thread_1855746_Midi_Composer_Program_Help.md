---
title: "Midi Composer Program Help"
date: 2011-10-06
forum: Multimedia Software
---

### Post by Lord_Solrac2 on 2011-10-06
Hey I've followed the recomedations around and Installed RoseGarden, LMMS, and MuSe

I don't have MuSE Score because, I only know how to work with Piano Roll (not Scores)

The Problem ::
As For The RoseGarden FAQ told me, I ran in Terminal the jackd command, works but still in RoseGarden I can't hear anything.. Same is for LMMS and MuSE... I also used the GUI for JACK but no progress either... It Runs and Goes OK but the Sound Server Stays in ALSA D:

Originally I used Anvil Studio in Windows (Wich I have Portable :D) Afterwards, My HDD Crashed badly and Windows 7 got "Poof'd"  Therefore I had to withdraw back to Linux, I picked Xubuntu 11.04 (DIEING FOR 11.10 x3). And The Problem is explained Upside

Stuff I Have Installed:: 
rosegarden, lmms, muse, qjackctl, jack-mixer, wine, virtualbox, jackd, jackd2, timidity

Systems Specs::
Ace Aspire One, 250 HDD, 1GB RAD, Intel Atom

Any Help?

---

### Post by shantiq on 2011-10-07
for rosegarden 

start sound thus

```
timidity -iA
```


extra info [**here**]("http://ubuntuforums.org/showpost.php?p=10528034&postcount=2")


if you want pointers for midi composition on rosegarden  there is a tutorial **[here]("http://www.youtube.com/watch?v=0-X6_q1iRzc")**

---

### Post by davidlondonuk on 2011-10-07
Start qjackctl and then say rosegarden. You then need to use the 'connect' tab on qjackctl to connect rosegarden to the sound sytem as if you were using patch cables. Sometimes it does it automatically sometime not. 

Your best bet is to start something like zynaddsubfx soft-synth connect it via qjackctl, load a sound and see if you can play sounds with your pc keyboard. If not, check you mixer settings and make sure the volume is not muted etc.

---

