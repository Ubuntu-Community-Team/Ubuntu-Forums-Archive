---
title: "Problem with my mp3 player - free space not showing up"
date: 2006-09-22
forum: Multimedia &amp; Video
---

### Post by ruimoura on 2006-09-22
Hi. I have a Samsung YP-U1 with 512 MB, that it's totally formated (has about 490 of free space, has it shows on windows xp and on the player it self).

Problem is when i try to copy some albuns the copy fails saying that there is not enough free space. On the properties says it only has 140 MB of free space !!!

I would like to use my player on my Ubuntu without having to restart to windows just to copy some mp3 over there ...

Thankx in advance :sad:

---

### Post by ropers on 2006-09-22
Does the volume show up under System -- Administration -- Disks?
Is it mounted? Ie. under Partitions, is the Status Accessible or Inaccessible? Does it correctly tell you its free space there?

---

### Post by ruimoura on 2006-09-22
It opens correctly (rithmbox pops up), it's correctly mounted, everything works fine. If i open gparted it shows up, but it tells me that only has 140 MB of free space (if i click on properties on the icon desktop the same happens) ...

Undre partitions the satatus is acessible, and the same happens (only 140 MB of free space).

I repeat. It is formated, and under windows (and on the player it self) says it has the full space avaiable ... :sad:

Ps: i can copy less than 140 MB of mp3 (or other stuff) to it, but if i try to copy more than that it says the disk is full ...

---

### Post by Jussi Kukkonen on 2006-09-22
I'd try formatting it again -- vfat is notorious for breaking easily.

---

### Post by barisurum on 2006-09-23
Hmm thats odd. I use the same player but have no problems. I use kde. Maybe that would be some bug with gnome.

---

### Post by Jussi Kukkonen on 2006-09-23
> **barisurum said:**
> Hmm thats odd. I use the same player but have no problems. I use kde. Maybe that would be some bug with gnome.
Come on barisurum, is there *any* reason to suspect that the Desktop Environment would affect something like that?

---

### Post by ropers on 2006-09-23
So in Windows, is the Recycle Bin empty, and are neither a swapfile nor a hibernation file configured to be stored on that partition? Is viewing hidden and system files enabled? Have you run a chkdsk? (Just brainstorming here, some of this may be besides the point...)

---

### Post by ruimoura on 2006-09-25
Thankx for the replies ...

Well, the way i solved it, for now, was filling it with 480 MB of mp3 from my windows boot and later i&#314;l try to format it again. 

I'll report soon if that worked or not. I'll also try everything that you guys sayd above ;)

---

### Post by delryn on 2006-10-12
I know that this thread hasn't been active for a few weeks, but I have a suggestion.

do a 'ls -a' on the player when it is connected
I suspect that you have a .trash folder there that is taking up some room
Had that happen to me, and it drove me nuts for a few weeks 

worth a shot anyway
cheers

---

### Post by ruimoura on 2006-10-12
Weel i forgott to say here that the problem is solved. I formated the player with the software from samsung (on windows) and now it is everything just fine.

---

