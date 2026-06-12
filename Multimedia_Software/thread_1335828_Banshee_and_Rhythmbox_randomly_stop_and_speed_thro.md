---
title: "Banshee and Rhythmbox randomly stop and speed through songs."
date: 2009-11-23
forum: Multimedia Software
---

### Post by example6 on 2009-11-23
I just recently fixed all of my sound problems and was happy to listen to music again, but when I play songs through Rhythmbox, randomly in the middle of it the song would stop and the progress marker would speed through the rest of the song choppily.

I downloaded Banshee, and had the same problem. The song files are being held on a NTFS partition on a separate drive which I am only able to mount via ```
sudo mount /dev/sdc1 /media/STORAGE
``` This leads me to believe that it may be a problem with NTFS, or transferring data between partitions.

Any help would be greatly appreciated!

---

### Post by jerrrys on 2009-11-24
try moving a song file to the ubuntu drive and run it from your music player.  I do not use NTSF, but I think ubuntu will let you do that.  also, how much ram do you have?

---

### Post by cool_penguin on 2009-12-02
I have exactly the same problem on my Dad's computer. Wonder what is going on with his desktop computer. It has an internal SATA disk with a NTFS partition containing music (his former Windows D drive).

Hope somebody finds a fix. 

Cheers,
Harish

---

