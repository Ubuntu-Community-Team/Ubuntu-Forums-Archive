---
title: "Audio CDs with Video content. How do I get at the video"
date: 2010-06-10
forum: Multimedia Software
---

### Post by bananabob on 2010-06-10
I have several CDs that have, as an extra, videos available on them.

When I load these CDs into my computer Ubuntu recognises them as audio CDs and I can play the audio. But how do I get to the video. Nautlius just tells me they are audio cds, and will not let me get access to the video content.

Will someone please tell me how I get to the videos?

---

### Post by Chronon on 2010-06-11
> **bananabob said:**
> I have several CDs that have, as an extra, videos available on them.

When I load these CDs into my computer Ubuntu recognises them as audio CDs and I can play the audio. But how do I get to the video. Nautlius just tells me they are audio cds, and will not let me get access to the video content.

Will someone please tell me how I get to the videos?

Can you get access by using "cd" to get to the files?

---

### Post by bananabob on 2010-06-11
cd to what directory?

---

### Post by Chronon on 2010-06-11
The one where the CD gets mounted (such as /media/cdrom).

---

### Post by bananabob on 2010-06-11
fstab puts the disc at
> 
/dev/cdrom        			  /media/cdrom0 udf,iso9660	user,noauto     	   0       0


but there is nothing in the directory
> 
bananabob@thorium:~$ cd /media/cdrom0
bananabob@thorium:/media/cdrom0$ ls
bananabob@thorium:/media/cdrom0$
 bananabob@thorium:/media/cdrom0$ cd /media/cdrom
bananabob@thorium:/media/cdrom$ ls
bananabob@thorium:/media/cdrom$ 


Nautilus also shows an empty directory.

---

### Post by bananabob on 2010-06-12
Just some extra information. I have found that although the audio disc can by accessed by Sound Juicer, and audio players, it is not mounted. See the image:
[http://www.dropbox.com/gallery/283598/2/Link%20to%20images/screenshot?h=7a2bb6](http://www.dropbox.com/gallery/283598/2/Link%20to%20images/screenshot?h=7a2bb6)

---

