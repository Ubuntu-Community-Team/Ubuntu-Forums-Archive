---
title: "Intel/Nvidia graphics card issue with ubuntu 12.04"
date: 2014-05-30
forum: Multimedia Software
---

### Post by marino2 on 2014-05-30
Hi,

i'm looking for help about what is likely to be a problem with my graphics card.

i recently installed Ubuntu 12.04 on a DELL Vostro 3750 which has two graphics cards, an integrated one (Intel) and a discrete one (nvidia).
the driver for nvidia is nouveau, no proprietary drivers installed.

the problem i'm facing is the following: the computer starts overheating very early after i turn it on (and fans going like crazy, as a consequence), even without doing anything particularly intensive in terms of CPU.
in addition, when i have to run a video-conference software (vidyo-desktop), after a while everything becomes extremely slow (very high temperature and fan speed, of course), with the CPU usage of the video-conference process going up to 250%.
the problem seems related to the video, as everything slowly goes back to normal by just minimizing (not closing) the video-conference window for a while. 

the discrete graphics card doesn't seem to be used at all by the OS, even though powered-on at startup.
so far i have only managed to switch it off (which maybe brought a marginal improvement of the situation), but not to actually use it (supposing this would solve this whole thing).

on a side note, up to a few weeks ago i had Arch Linux installed on the same computer and i didn't have the above problem.

(i apologize in advance if some relevant information is missing in this first post)

any idea on what the problem is?

---

### Post by mörgæs on 2014-05-31
Hi, welcome to the fora.

These multi-graphics computers have been a problem for some time and I can't promise you that a complete solution is available.

I suggest you do some more experimenting to narrow down the cause. How does it work in a clean install of Lubuntu 14.04?

You could also google for **bumblebee** but I don't have experience with it, sorry.

---

### Post by marino2 on 2014-05-31
Hi[[COLOR=#C61919]****[/COLOR]]("http://ubuntuforums.org/member.php?u=939075"), thanks for the answer.

following you suggestion, i'll definetely try another another distribution as soon as i can, to see if this fixes the problem.
right now though, i can't experiment that much because i need the computer for a number of things... so i was trying to see if somebody knew about a solution for ubuntu

also, i had seen that bumblebee is supposed to help with this kind of stuff, but browsing for that i also saw it that wasn't working for some people with similar problems
so i wanted to ask in the forum before starting messing up with that ;)

even if no quick solution is available, it'd be great if someone who ran into the same issue could comment and maybe help me figure out what the problem actually is... -.-'

---

