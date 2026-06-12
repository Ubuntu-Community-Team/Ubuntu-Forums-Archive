---
title: "rip dvd doesnt show dvd"
date: 2007-10-24
forum: Mythbuntu
---

### Post by edrock on 2007-10-24
my issue is regarding the rip dvd feature. currently no matter what dvd i put in, im presented with "No Jobs. Checking and/or waiting for DVD."

my first problem was that myth wouldn't play dvd's, to fix that i went into dvd settings>general settings and had to change the location of dvd devices from /dev/dvd to  /dev/dvd this worked for me, and now i can play dvd internally. (though it works, im not sure if its correct)
side note:( i have 2 drives, one is a dvd player, the other cdrom1 is a cd-rw.. when i hit eject, only the cd-rw ejects.. i cannot get the system to eject the top drive(the dvd drive))
side note 2:(totem player? always auto plays the dvd, even though i have selected the dvd to play internally through mythtv..how do i turn off autoplay)

since i was able to get the dvd playback working, i then wanted to rip a dvd, and now im here asking for help(after looking for hours around the web for a solution)

i checked my mtd log, it shows that is running, that its listening on port 2442, and that a client socket has been opened / a client socket has been closed (im assuming that is written when i am in mythtv and i click rip dvd

so from what i can piece together, it seems as though mtd doesn't recognize that there is a dvd in the drive.
which i would then assume that my rip settings are incorrect..though i dont know what to change on it to fix it.

I have libdvdcss2

im very new to linux/myth

i used the latest version of mythbuntu

any help with fixing this issue would be great.
thank you in advance

---

### Post by edrock on 2007-10-26
bump.. please help.

---

### Post by edrock on 2007-10-31
This is still and issue for me. Please help

---

### Post by superm1 on 2007-10-31
> **edrock said:**
> my issue is regarding the rip dvd feature. currently no matter what dvd i put in, im presented with "No Jobs. Checking and/or waiting for DVD."

my first problem was that myth wouldn't play dvd's, to fix that i went into dvd settings>general settings and had to change the location of dvd devices from /dev/dvd to  /dev/dvd this worked for me, and now i can play dvd internally. (though it works, im not sure if its correct)
side note:( i have 2 drives, one is a dvd player, the other cdrom1 is a cd-rw.. when i hit eject, only the cd-rw ejects.. i cannot get the system to eject the top drive(the dvd drive))
side note 2:(totem player? always auto plays the dvd, even though i have selected the dvd to play internally through mythtv..how do i turn off autoplay)

since i was able to get the dvd playback working, i then wanted to rip a dvd, and now im here asking for help(after looking for hours around the web for a solution)

i checked my mtd log, it shows that is running, that its listening on port 2442, and that a client socket has been opened / a client socket has been closed (im assuming that is written when i am in mythtv and i click rip dvd

so from what i can piece together, it seems as though mtd doesn't recognize that there is a dvd in the drive.
which i would then assume that my rip settings are incorrect..though i dont know what to change on it to fix it.

I have libdvdcss2

im very new to linux/myth

i used the latest version of mythbuntu

any help with fixing this issue would be great.
thank you in advance
Have you tried some other dvds to see if the problem was just the ones you were trying?

---

