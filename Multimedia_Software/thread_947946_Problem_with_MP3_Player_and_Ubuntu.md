---
title: "Problem with MP3 Player and Ubuntu"
date: 2008-10-14
forum: Multimedia Software
---

### Post by Onizuka89 on 2008-10-14
Okay, I might have posted this in wrong category, didn't know where to post it.
Anyway the problem I have is that I connected my MP3 Player (I am not too sure what it is called) anyway... I deleted some files from it to make up space but then it turned out that I had lost the space those files took all together. So each times a file get deleted through Ubuntu it gets less and less free space. Is there any way to undo this? I would be very grateful if anybody could help me.
And yes I have tried to search for answers but didn't find any...

EDIT:
I have been using Ubuntu for about a month now and I must say I am pretty happy with it. Most the problems I got was easily solved because members of this forum had been kind and helped others when they had problems.

---

### Post by kostkon on 2008-10-21
> **Onizuka89 said:**
> Okay, I might have posted this in wrong category, didn't know where to post it.
Anyway the problem I have is that I connected my MP3 Player (I am not too sure what it is called) anyway... I deleted some files from it to make up space but then it turned out that I had lost the space those files took all together. So each times a file get deleted through Ubuntu it gets less and less free space. Is there any way to undo this? I would be very grateful if anybody could help me.
And yes I have tried to search for answers but didn't find any...

EDIT:
I have been using Ubuntu for about a month now and I must say I am pretty happy with it. Most the problems I got was easily solved because members of this forum had been kind and helped others when they had problems.
It just keeps them in a hidden trash folder in your device.

Thus, access the files of your player using the file browser (i.e. *Nautilus*) and select *View -> Show Hidden Files* from its menu. After doing this, you should be able see this hidden folder; it will have a name like
```
.Trash-something
```
Inside this folder you will find the files you had deleted. Selecting and deleting them it will remove them for ever and you'll reclaim your lost space.

There is an option to disable this hidden trash folder thing, but doing this I think it will disable the trash functionality for your whole system. Thus, I believe it's wise not to do it.

---

### Post by Onizuka89 on 2009-02-07
Well... that's the problem... I have already done that, yet there was no space freed, but thanks anyway.

---

### Post by ohgodnotanother1 on 2009-02-08
Open a terminal and "cd" to the mount point of your MP3 player.
Then enter "du -h" and check what's taking up your space.

---

### Post by Onizuka89 on 2009-02-08
well according to the du command I only have filled 156M. 
This is just plain weird :S

---

### Post by Zimmer on 2009-02-08
Do you have a file delete function on the MP3 player itself?

My suggestion is you see if you can still see the deleted files with the MP3 player standalone, and try using the player's delete function.

I had this once with an MP3 player, too. It did not like a delete by a PC filing system (even XP) .

I have taken the paranoid step of NOT deleting files from external devices using a computer, only the device's own delete function.

Unless someone comes up with a better idea....
If you get no other answers....
You may need to take the drastic (well, not too drastic) step of copying your remaining MP3 files from the player to the PC, disconnect, then use the functions of the player to reformat/wipe the file storage area of all the MP3 files and then see if you have recovered the space. Then you can  start moving the MP3's back from the PC to the player, remembering in future to ONLY delete files using the Player's delete function.

---

### Post by Onizuka89 on 2009-02-08
Yeah, there is a delete function in the player itself, started to use it after this event.
Unfortunately it didn't find the files that were deleted.
I'm in a bit more luck, it seem to delete files just fine with XP (not that I am using it any more at home).
The player don't seem to have such a function as to where it wipes the memory clean.
And I don't really use my MP3 Player much any more anyway, so I guess the 100 Mb isn't that big of a deal, still got 156 more.

I think I shall go for your advice if I want to remove more from MP3 players

Thanks for the help everyone.

---

