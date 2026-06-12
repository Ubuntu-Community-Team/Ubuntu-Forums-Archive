---
title: "Audio Jack doesn't work on Compaq Presario 554 (Newbie)"
date: 2007-07-19
forum: Multimedia &amp; Video
---

### Post by chillfaktor on 2007-07-19
Hi all,

I have installed ubuntu: feisty fawn on my Compaq Presario 554 and I managed to get my wireless going, but i still cant get my head around getting sound out of my audio port. The internal speakers work fine, its just the little 3.5mm port that seems to be dead!
According to Alsa Mixer y card is HDA Intel and chip is Conexant CX20549.

I have found this thread [http://ubuntuforums.org/showthread.php?p=3044527#post3044527](http://ubuntuforums.org/showthread.php?p=3044527#post3044527) that seems to be a quick fix. 
I have tried around a little but unfortunately i made /etc/modprobe.d/alsa-base disappear somewhere during my efforts to try to edit the file (as i didnt have permissions for it and couldn't figure out how to acquire ownership of the file).

I wonder if there is a quick fix for this seemingly very common problem, and if i was on the right track with the mentioned thread. If yes, how do i get that file  back? :D

There seem to be countless people around that have similar problems and some solutions go into recompiling kernels and what not, but do i really need to go there for something seemingly basic like sound?

I'd love to make ubuntu my primary os as i love the overall feel of it!

Cheers, F

Edit: also not sure if this is the right forum

Update: i have followed the advice found here [http://ubuntuforums.org/showthread.php?t=502880&highlight=sound](http://ubuntuforums.org/showthread.php?t=502880&highlight=sound) which didnt make any difference. 
I have also looked on the alsa website but thats way over my head! So as far as i think i know its something to do with the snd-hda-intel driver if that helps

---

### Post by scrooge_74 on 2007-07-19
from a command line type alsamixer check on the headphone and other stuff check for a line jack sense (off) and turn it to on.  That was they way I got my headphones to work.

Probably something is off there

---

### Post by chillfaktor on 2007-07-19
this gives me two columns for "master", "PCM". i also have "IEC985" which seems to be off (doesnt have a column to it) how do i turn it on?

---

### Post by scrooge_74 on 2007-07-19
The letter "m" toggle things off/on if I am not mistaken

---

### Post by chillfaktor on 2007-07-19
can't seem to turn it on or off with enter...
Common guys :)

---

### Post by scrooge_74 on 2007-07-19
not with enter with the letter "m"

---

