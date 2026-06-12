---
title: "mp3 player ipod clone help 2 partitions?"
date: 2007-06-28
forum: Multimedia &amp; Video
---

### Post by sdowney717 on 2007-06-28
I have a lisong wilson mp3 player that has a problem with the usb flash partitions.
It should I assume have only one partition for storing files.
The device can only see the first partition of 16mb
The device can not see the second partition of 1.88gb.

I tried gparted and it shows

sda my main computer drive.
sdb mp3 player 16mb
sdc mp3 player 1.88gb

I can partition each of these sdb and sdc as separate drives, but they need to be all in one.
When set up as fat32 partitions, I can copy files to each separate partition. BUT the device will only ever see the sdb 16mb partition
Any thoughts on eliminating these 2 into 1?

---

### Post by moore.bryan on 2007-06-28
*don't know about your type of player, but chances are the 16mb partition holds firmware for the functioning of the player... my guess would be it should stay.  i know that still leaves you with your second problem.  could it be ubuntu is not mounting your sdc?*

---

### Post by sdowney717 on 2007-06-28
The player has a problem.
The 1.88gb partition is not recognized by the player.
If I put an mp3 song in the tiny 16mb partition, the player sees the file.
If I put the mp3 song in the 1.88gb partition, the player does not see the song.

Also, under the memory menu for the player, If the 16mb partition is deallocated by gparted, then the player reports c: 0

If the 16mb partition is allocated as fat32 by gparted, then the player shows 16mb.

Its strange to see 2 partitions, And strange to see the firmware calling it c:
who knows could the players firmware be somehow defective? It used to work fine, but I dont know if it used to have 2 partitions or only one.

---

### Post by moore.bryan on 2007-06-29
*why would you wonder if it used to have only one partition?  did you do some playing with the partitions?  if so, that could help solve the problem.*

---

