---
title: "Speakers don't mute when I plug in headphones"
date: 2008-04-28
forum: Multimedia Software
---

### Post by arazvan on 2008-04-28
I have alsa .16.
I have sound from speakers and headphones.
I use toshiba satellite A200-14D.
I am using Hardy.
ALC861VD
I tried everything on this forum .... i think. I did see many other threads on this problem but they are old and none of them offer a solution. 
If anyone solved this problem PLEASE help me. I am about to go medieval on my laptop.

---

### Post by olejorgen on 2008-04-28
I got the same problem on a toshiba M7. I haven't found a "propoer" solution, but for me it works to open alsamixer an mute (press m) Front. You can probably use gnome-volume-control too. This mutes the speakers, but not the headphones.

---

### Post by arazvan on 2008-04-28
doesn't work for me ... it mutes everything.

Also I am going to specify that I do not have the "jack sensor" switch.

---

### Post by olejorgen on 2008-04-28
Try different channels/controllers. And you must *mute* it, not use the slider. Might of course be specific to M7 though.

---

### Post by sandman87 on 2008-04-30
iv had the same problem too,  and i was really surprised when i found this thread. i took your advice on using the volume controller and i found something called "headphone sense" which solved my problem. If youv alread solved this problem please have me exused, Im new to both Ubuntu and this forum.

cheers!

---

### Post by ondrisko on 2008-04-30
I have HP Compaq nc6120 and I solved this problem by turning on the Headphone Jack Sense in alsamixer.

---

### Post by pageturner1988 on 2008-05-08
You're not alone.  I'm on my Toshiba and have had the same issue.  I've tried searching everywhere but never found a thing that is meant to work for Hardy.  Hopefully there is someone working on this and we'll soon be able to enjoy our tunes without annoying everyone around us.

---

### Post by coolairin on 2008-05-12
I had the same problem, too; but it has been solved. I just edited my alsa-base adding the following line: 
options snd-hda-intel model=acer
This line may be varied with your sound card/chip.
For a detailed guideline, see here: [http://ubuntuforums.org/showthread.php?t=616845&highlight=headphone+sense](http://ubuntuforums.org/showthread.php?t=616845&highlight=headphone+sense)

---

