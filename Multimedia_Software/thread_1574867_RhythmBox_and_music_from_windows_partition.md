---
title: "RhythmBox and music from windows partition"
date: 2010-09-14
forum: Multimedia Software
---

### Post by Akpsp on 2010-09-14
Sup fellas. I need help with rhythmbox. I open music and put them on the rhythmbox, but when im done at the end of the day I shut down the laptop. But when i reboot into linux, the music files arent there. I always have re-add them. is there any way to save them, and not use up space on the ubuntu partition, on the box without having to keep re-adding them?

And yes, i do dual boot windows 7 and ubuntu 10.04.

---

### Post by Rasa1111 on 2010-09-14
I think as long as you keep them in a separate partition,
youll have to keep re-adding them. 

Only other way Im aware of is to keep them on an external drive. 
Thats what I do,
and they are always in the list when I open the music player. 
They just wont play until the external is plugged in. (obviously) lol
But I never have to re-add them.

but perhaps there is another way that im unaware of (very possible) lol

---

### Post by dirtyburger on 2010-09-14
i had this problem

wat u have to do is first mount the partition that has the music files, in ur case the windows one

then you can open rythembox and start playing!

if it cant find the files, it deletes the entries because it cant read the unmounted partition,

so mount the partition first then open rythembox so that it thinks that the drive never unmounted, and your just opening it up again

u gotta trick the program lol

at least thats what i do

HOPE I HELPED

---

### Post by shadowlemon on 2010-12-10
Never had any problems with this.

I just added it to my library locations when the partition is mounted. When I open and forgot to mount, I just mount it and it automagically appears.

if you have any problems, i'll be happy to look at them.

---

### Post by noogs on 2011-01-08
Sorry to bring this thread back up but I thought I should suggest adding an entry to your fstab for the windows partition so its mounted when you boot. That way all you have to do is open up rhythmbox, the partition is already mounted.

---

### Post by Vimmander on 2011-01-21
So, I have a related question.  I also have a Windows7/Ubuntu dual boot setup, and I'd like to use Brasero to burn a CD.  However, all my music is on my Windows 7 partition (since after testing it, I determined that 7 was better at syncing to my Sansa Fuze).  Will anything freaky happen if I mount my Window partition and burn music from it to a CD through Ubuntu?  Things like trashing the NTFS filesystem, overwriting something important during the burn or unmounted, etc...I mean, sometimes Ubuntu gives me a message that says to not disconnect my Windows drive until it finished writing to it.

Thanks:KS

---

