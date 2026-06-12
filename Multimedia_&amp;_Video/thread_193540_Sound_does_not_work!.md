---
title: "Sound does not work!"
date: 2006-06-10
forum: Multimedia &amp; Video
---

### Post by shiznatix on 2006-06-10
I have 2 sound cards on my system, one is integrated and the other is a PCI card. I use the PCI card one because the other has lots of problems. Now in Breezy the sound worked no problem. Now after I upgraded I get no sound and the volume control thing just shows a red x over it and when i click it, i just get 'current mixer' then a menu that has absolutly no options in it.

How do I get my sound back?

---

### Post by Sutekh on 2006-06-10
It could possibly that after the upgrade, the volume control is trying to use the wrong device.

Can you post the output from this command in a Terminal (Applications -> Accessories menu), which lists your cards and their order. ```
cat /proc/asound/cards
``` Then open the alsamixer
```
alsamixer
``` Is the alsamixer using the correct sound device?  You might aswell check that the channels are unmuted too.

---

### Post by shiznatix on 2006-06-10
> 
natix@natix:~$ cat /proc/asound/cards
cat: /proc/asound/cards: No such file or directory
natix@natix:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

is what I got. I am assuming thats a bad thing.

---

### Post by BitTorrentBuddha on 2006-06-10
Try disabling the integrated sound at the bios setup utility, this is what worked for me when I was having a very similar problem.

---

