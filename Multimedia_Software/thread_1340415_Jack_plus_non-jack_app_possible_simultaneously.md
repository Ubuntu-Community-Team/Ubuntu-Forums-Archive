---
title: "Jack plus non-jack app possible simultaneously?"
date: 2009-11-28
forum: Multimedia Software
---

### Post by Tim_Magee on 2009-11-28
Hi,

I'd like to be able to run a Jack app (let's say Ardour) at the same time as a non-Jack app (a flash audio player in Firefox).

Is that going to be possible, or am I barking up the wrong dead herring?

I'm using an Acer 5715z laptop with onboard Intel ICH8 HDA chipset.  I'm on Karmic 9.10, recently updated from 9.04.

Original behaviour: 

[LIST]
[*] start with flash audio playing
[*] start Jack, FF audio is paused
[*] stop Jack, FF audio resumes
[/LIST]
While researching I read a variety of opinions about pulseaudio ranging from 'install it, it will solve everything' through to 'uninstall it, it ate my hampster'. Since I was starting with it installed, I uninstalled it using instructions from the forum.

After pulseaudio is gone, behaviour is:

[LIST]
[*] start with flash audio playing
[*] Jack won't start: 'hw0 is already in use'
[/LIST]
 So: (how) can I use Ardour to tinker with some audio files while listening to some tunes in my browser?

Thanks,
Tim

---

