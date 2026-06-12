---
title: "DVD Rip doesn't work - where I went wrong"
date: 2009-02-14
forum: Mythbuntu
---

### Post by acodring on 2009-02-14
Hi,
I wasn't able to rip dvd's and searched google for clues. An old thread describing my problem was here in the archives, but didn't seem to provide an answer. I figured out where I went wrong and figured I'd publicly shame myself while providing Google with a more recent search result, including an answer...

I was able to play DVDs, but mtd didn't appear to go anywhere when I started a rip. The GUI just said "Nothing to do..."

Here's the process I went through to figure out what was wrong:

[LIST]
[*]opened a terminal, 
[*]found the mtd process number (ps ax | grep mtd), 
[*]killed the mtd process (kill [insert the process number you found last step here]),
[*]started the mtd process again in the terminal so I could see the log output (mtd)
[*] watched mtd complain that the configured output directory didn't exist! (bad destination directory in job request...)
[/LIST]

Doh! After that it was quick work to create a video folder (mkdir /media/storage/video; mkdir /media/storage/tmp) and then use the myth GUI (Utilities/Setup | Setup | Media Settings| Videos Settings | [General Settings & Rip Settings]) to point DVD ripping to those directories.

Hope that saves someone a few minutes.

Cheers,
Andrew

---

