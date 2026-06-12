---
title: "Tvtime sound solution....almost....HELP me wizards!!"
date: 2006-01-13
forum: Multimedia &amp; Video
---

### Post by ZarathustraDK on 2006-01-13
Alot of people (myself included) have experienced being able to view different channels in pictureperfect quality, but without any sound.
The different solutions to the problem I've read about in here is mostly comprised of turning off mute and buying a cable that goes from the tvtuners audio out to the soundcards line in.

Another solution, which I can't remember where I saw (another distro), is about using the following line :

sox -t ossdsp -r 48000 -b -c 2 /dev/dsp2 -t ossdsp /dev/dsp

...and supposedly the sound should work.

Problem is, I don't have a /dev/dsp2, only a /dev/dsp.
Any ubuntu-wizards who can think of a workaround for this? I'm so close... :-(

---

### Post by ZarathustraDK on 2006-01-14
Ok, I've gotten it to work perfectly now. I was about to give up on the whole thing because noone seemed to know what to do. I kept on trying to figure out a way to use sox on it when it occurred to me. The reason I didn't use a cable from the tvtuner to the line in was because my tvtuner seemingly didn't have an audio out on it. It didn't...on the outside of the cabinet...but on the inside however...D'oh!

So I snatched the audiocable from the cd and tried the three possibilities the inside of the cabinet had to offer (memo to self, audio out on a tvtuner is the red port) and hooked it up to the motherboard. A little screwing around with the tvtime gui's audio options and finally TV on Linux is mine MUAHAHA!

That only took me two days of continued selftorment. :-D

So the verdict is clear : Ubuntu stays, Windows blo...eh...goes...

Next task is getting my ATI Radeon 9600 TX to show 3d (omg he's insane...), something that has been well under way for over a week now.

---

### Post by gitfiddler on 2006-01-15
Thanks for sharing your solution. I'm sure it will help many others who take the time to search this forum.

---

### Post by codebox on 2006-01-16
can u tell me what tv card are you using? and how do you make linux remember the driver you load in int :) thanks

---

