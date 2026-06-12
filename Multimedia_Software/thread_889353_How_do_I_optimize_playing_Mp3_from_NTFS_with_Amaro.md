---
title: "How do I optimize playing Mp3 from NTFS with Amarok or Banshee?"
date: 2008-08-14
forum: Multimedia Software
---

### Post by kidwithshirt on 2008-08-14
Hey. I recently got Ubuntu and I looked into amarok and banshee for an itunes alternative

I used amarok for a couple of days and it played my music from my NTFS partition with vista installed. The first couple of times after Amarok made a database, the music played fine, not much problem (I didn't do any syncing though)

But recently Amarok won't play my mp3 from NTFS. I found out the source of the problem. 

1. To make it work, I must manually open up C: drive with explorer. Else it doesn't work
2. If Vista is sleeping and I boot into ubuntu, it won't work.
3. ???

I can't bypass the third one. Today I dont know what happened nothing wont play anymore. I just downloaded a couple new albums (with windows -> imported into itunes -> consolidated library into itunes folder like always) and nothing plays anymore.

I downloaded banshee and nothing plays at all. Hmm

Is there some preparation I should do in order for my music to function correctly?

---

### Post by EarloftheWest on 2008-08-14
I keep my Windows data on a separate partition from Windows itself. I used to use my data drive as the location for my swap partition. I found that Ubuntu wouldn't mount the data partition if I had previously hibernated from Windows.

Are you using the NTFS-3G driver for your ntfs drive? I think you need to change ntfs to ntfs-3g in your fstab to do that.

---

### Post by pietjanjaap on 2008-08-14
Ubuntu connects ntfs only if you go to the partition.
Maybe thats the problem.
Maybe make a script(batch file) that goes to the ntfs partion and ls (list) the directory(in de terminal), i do not know if this helps.

Maybe you could install ntfs-g3(old version ubuntu), maybe that is still possible.

Fstab, maybe you could change something in here so the partition connects on boot.(try storage device manager, system-administration-storage device manager.


Ofcourse there is maybe somethings else wrong.

---

### Post by taseedorf on 2008-08-14
It's actually quite simple.

The reason this is happening is because you're drive with the music is not mounting on boot.  Edit your fstab like stated, and try using pysdm.  It's available in the repositories and will let you edit your drive or partitions to automatically mount upon boot. (it's just a gui to edit fstab)  when you want to run it, type sudo pysdm in terminal, than enter your password.  

In order to find which partition your media is on, if you have multiple like me, type sudo fdisk -l.

---

### Post by kidwithshirt on 2008-08-14
Oh I think I just broke my audio codecs or something because none of the audio players play mp3 now.

ARgh!

I followed this guide yesterday:

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

I dont know if that did anything bad

---

### Post by kidwithshirt on 2008-08-14
used alt-ctrl-bkspace

works now. weird.

---

