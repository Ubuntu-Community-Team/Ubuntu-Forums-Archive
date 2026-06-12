---
title: "Horrible sound quality! Help!"
date: 2006-07-19
forum: Multimedia &amp; Video
---

### Post by kwatz on 2006-07-19
I run a Ubuntu Dapper /w dual-booting win2000 pro.

Everything in my shiny ubuntu works perfectly, except for the sound. If it didn't work at all, that'd be easy to fix, but this time it works - sort of. What i get is terrible extra hissing and screeching alongside the music. Ie. if a certain part of a song is louder (say, a drum solo) the extra noises will equally grow alongside of the music. The extra noises are there all time i play music. It's really a pain because i listen all my music through my cpu. 

On the Windows side, sound works perfectly, so we can safely assume there is no fault in the amplifier, cords, or other aux-things. 

I thought dist-upgrade to Dapper would have helped, but the problems stick. So far i have tried removing OSS drivers in favor of ALSA and different player / sound server combos, but every combination produces exactly the same garbled sound. 

I have seen various solutions to this in this forum before, like dropping PCM volume to 70% and utilizing Master volume instead, but many people complain that it does not really solve the problem. Most problems also seem to concern ac '97 mobo - integrated chips which i also have. So far i have not come across any solution. If you got anything, please post.

---

### Post by frühstück on 2006-07-19
Dropping PCM to 70% is the solution, no soundcard sounds good at 100% PCM. I have seen windows drivers that set PCM to about 30% (i dont know exactly, because i dont know a way to see PCM in windows...)

---

### Post by kwatz on 2006-07-19
I decreased PCM volume before, but it didnt work. Decreasing PCM volume  helps (mine's aroung 50%), but it does not make the hissing and scratching go away, it drops the volume altogether and thus makes more exquisite sounds fade. 

I use a test song which is ripped from a vinyl LP, and with Windows i can easily hear the cosy vinyl scratches behind the music. In linux, all the atmoshphere is replaced with more disturbing scratching and hissing and i can not even hear the vinyl scratch at all.

I do not own a hi-fi set or hi-fi mentality, i prefer sound quality that is decent to my ear. And this, well, it is not even close. [-(

Considering the amount of similar reported problems with AC'97 i can find from this forum, i guess it's reasonable to suppose the easiest way to get rid of this nuisance is by purchasing a different sound card. I'm still hoping somebody has found a way through these woes..

---

### Post by Oblong_Cheese on 2006-07-20
[Join the club, mate](http://www.ubuntuforums.org/showthread.php?t=218690).

I'm having similar annoying sound issues, though apparently only with mp3.

---

### Post by bratliff on 2007-04-03
Thanks a bunch. I have had sound problems for several weeks, re installed ubuntu several time to fix the problem. I turned the sound volume up never suspecting that it would make my sound level go down and sound garbled.

Ratliff


> **frühstück said:**
> Dropping PCM to 70% is the solution, no soundcard sounds good at 100% PCM. I have seen windows drivers that set PCM to about 30% (i dont know exactly, because i dont know a way to see PCM in windows...)

---

