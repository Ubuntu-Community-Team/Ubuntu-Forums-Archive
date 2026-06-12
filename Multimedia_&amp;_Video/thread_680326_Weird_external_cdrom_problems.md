---
title: "Weird external cdrom problems"
date: 2008-01-27
forum: Multimedia &amp; Video
---

### Post by slowpoke115 on 2008-01-27
I've got an LG slim CDrom which works a treat on my windows computers (plays everything) and also works well 90% of the time on un by gutsy ubuntu install.  The major problem i'm having is it won't play any DVD's at all. It's mounted and I've ammended fstab to include a reference to it but dvd movies definitly do not play. I'm using VLC to play them and the same setup works fine with XP (same disks, program CD rom drive). I also get errors when I try to move the .vob files about. dmesg shows the following:

Buffer I/O error on device sr0, logical block xxxxxx

repeated a few hundred times. The disk is perfect, it's brand new and as I've already emphasized it plays ok on everything else. The menu shows up and video seeking seems to work (it knows how long the clips I attempt to play are and I'm able to seek through them, just not play them).


P.S. thanks for the help, I know this is my first post n'all and it's hartd to assess my technical abilities but I really appreciate any help at all, thanks.

---

### Post by slowpoke115 on 2008-01-27
Fixed, just missing libdvdcss and w32 codecs, silly me, should of worked it out when seeking worked ok.

---

