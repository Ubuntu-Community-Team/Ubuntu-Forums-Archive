---
title: "Please Help me !!!!  i think i screwed up my ipod!"
date: 2007-06-24
forum: Multimedia &amp; Video
---

### Post by Opeth115 on 2007-06-24
Ok well i tried using my ipod in Linux because i have all of my music here and i wanted to try to put some new music onto my ipod.  So i tried using yam pod and it said it transfered all the songs to it but when i went to my ipod they weren't there but it said that my available space had gone down...  so i tried again and the same thing.  i decided to just use the apple updater and my windows machine to restore the ipod and try again but! the ipod wasn't recognized and it wouldn't let me restore it.  So i read around a little and came to a thread that said to use g parted to re partition my ipod as fat32 so i did it and planned to use rock box as my firmware... Do i have no way of loading rock box onto my ipod now since it's just an empty hard drive??  someone please help me with this!

---

### Post by tpg on 2007-06-24
Have you been using your IPod on Windows previously? If so it is already Fat32 formatted, and I would strongly advise against reformatting it unless it is absolutely necessary, as I think there are two partitions on the iPod, one containing the apple firmware (which I think might be needed by the rockbox installer).

Rockbox should install over the apple firmware, just follow the instructions at [www.rockbox.org](www.rockbox.org). You then have to re-copy over your music to a directory on your IPod, and you can then delete the apple specific directories (sorry, can't remember the names).

---

### Post by Opeth115 on 2007-06-24
i know that's the problem =( i already reformatted it. i don't understand how i can install rock box i really hope i didn't screw up my ipod...  do u know how i could install rockbox in any other way?

---

### Post by NilsE on 2007-06-24
Somewhere in the instructions for the iPod there is a way to "re-initialize" it.  If it won't re-initialize you can then download the firmware from Apple and reset it that way. Then in windows see if it recognizes it and it should reformat it for you.  If not then there is a way in the iPod desktop software to do that or force it to recognize it.

---

### Post by tpg on 2007-06-24
Take a look at the appropriate manual (I don't know what model iPod you have), at [http://www.rockbox.org/manual.shtml]("http://www.rockbox.org/manual.shtml"). If you've already formatted it, never mind, try following the instructions anyway (it'll work from windows or linux). If it really doesn't work, try the apple ipod updater again to restore the iPod to the default state (I think it will redo the partitioning, but I'm not sure).

---

### Post by Opeth115 on 2007-06-24
i tried installing rockbox but it can't find any ipod to install the bootloader to =( im gunna go try the apple updater right now

---

### Post by Opeth115 on 2007-06-24
woo wooooooooooooooooo fixed it lol.  thank you all very much ofr ur help!

---

