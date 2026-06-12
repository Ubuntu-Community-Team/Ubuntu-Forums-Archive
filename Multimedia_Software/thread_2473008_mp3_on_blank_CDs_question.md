---
title: "mp3 on blank CDs question"
date: 2022-03-20
forum: Multimedia Software
---

### Post by jmichaels29 on 2022-03-20
My mother bought an old VW Beetle, which is actually one of the newer beetles and perhaps last year they made one, that had a CD player and it says "mp3" next to the CD player. 
So, I assume I can burn some mp3s as "data" on a bland cd and it will play the mp3s off of the cd disk.
 
A couple of questions:

1) Which type of CD should I buy that would likely be most compatible - I'm asking if a CD-R or a CD+R disk should be purchased.... 
 
2) This is a curious type question.  About how many mp3s, on about average, can one get on a blank CD ?  I know the advantage to the mp3s here is that many many more mp3s can fit on a cd (as a data disk) as compared to simply burning a song disk.... 
 
 
Regards,

MJ

---

### Post by Holger_Gehrke on 2022-03-20
[LIST=1]
[*]The '+' or '-' is mostly an issue for CD-writing. Modern writers recognize and handle both automatically. So it really depends on the drive(s). 
[*]This depends on the compression settings. When I ripped my CDs back in the early 2000s so I could take a good selection along in my portable MP3 CD player, I ripped to variable bitrate capped at 320kb/s - which my player could handle - and got about 6 to 10 Albums on one CD-R. So I'd say more than one hundred tracks at good quality. On the other hand a friend of mine had made a disc of his personal favourites at somewhat lower quality - 128 kbs cbr ? 192 kbs vbr ? - and that disc had about 300 tracks on it. 
[/LIST]
 
Holger

---

### Post by jmichaels29 on 2022-03-21
> **Holger_Gehrke said:**
> 
[LIST=1]
[*]The '+' or '-' is mostly an issue for CD-writing. Modern writers recognize and handle both automatically. So it really depends on the drive(s). 
[*]This depends on the compression settings. When I ripped my CDs back in the early 2000s so I could take a good selection along in my portable MP3 CD player, I ripped to variable bitrate capped at 320kb/s - which my player could handle - and got about 6 to 10 Albums on one CD-R. So I'd say more than one hundred tracks at good quality. On the other hand a friend of mine had made a disc of his personal favourites at somewhat lower quality - 128 kbs cbr ? 192 kbs vbr ? - and that disc had about 300 tracks on it. 
[/LIST]
 
Holger

Thank you so much for your prompt and detailed reply! 
 
I think it's really neat that the 2008 Volkswagen Beetle has not only a CD player, but a CD player that can play mp3 files!
This is the 3rd VW  "New Beetle" that my parents have owned, and the previous 2 only had cassette decks.  
This is especially cool for me, as I recenlty replaced the "read only" CD drive in my HP desktop with a CD/DVD read & write drive.  Mom wants some songs on CD & I told her I could put a bunch of songs on just 1 CD for her - now I can tell her that I can probably get 100 songs or more on each CD.  Way cool !
 
Thanks again for your reply! 
 
Regards,

MJ

---

### Post by SeijiSensei on 2022-03-21
As I recall, some systems of that vintage expected to see a "Music" folder in which the songs are stored.

Also make sure to use a Windows filesystem, preferably FAT32 (or "[vfat]("https://linux.die.net/man/8/mkfs.vfat")" in Linux usage) for widest compatibility, if the CDs need to be formatted.

---

### Post by ajgreeny on 2022-03-21
Surely CDs are not formatted before they're recorded or written to?

Fat32 on a CD? That's news to me!

---

### Post by Holger_Gehrke on 2022-03-21
All data CDs have an ISO-9660 file system (or sometimes UDF with an ISO compatibility bridge). That's why CD and DVD image files are sometimes called iso(s). No formatting necessary, the file system is created during burning.

Holger

---

### Post by TheFu on 2022-03-21
I put an after market player into my vehicle with mp3 support in 2002-ish.  I had the AUX jack plug put in a convenient location and use that with either mp3 players or a smartphone/tablet. Can't remember the last time I put a CD into the CD slot.

I don't remember it being picky about CD-R or CD+R at all. It was picky about certain mp3 options - like the bitrate and variable/constant rate. If you stay with common bitrates and cbr, it should be fine, but test joint stereo and vbr too.

On the CD, I used _ISO9660 with RockRidge extensions_ to support long filenames.

In the end, the AUX jack is just much more convenient.

---

