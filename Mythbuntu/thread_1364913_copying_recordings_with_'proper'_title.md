---
title: "copying recordings with 'proper' title"
date: 2009-12-26
forum: Mythbuntu
---

### Post by wilma92010 on 2009-12-26
I have been using Mythtv for about 6 months with an WinTV-HVR 1600 with OTA HD using MythBuntu 9.04 and it works quite well and I have numerous recorded shows. I would like to ulitimately 'backup' some of these recordings, but there are some missing pieces of info I need.

The WinTV card has a hardware mpeg 2 encoder as that is what OTA HD uses. This is an OK format for me to backup with, and I can use familiar and workable tools on my Windows 7 desktop to further transcode them, not better, but familiar and works with other stuff I have.

I can successfully, meaning without error, 'trancode' recordings, the logs say it is successful, but it looks like it processes the file to a similarly named temp file in /var/lib/mythtv/recordings, and it does this without error. Then it renames the 'transcoded' file to the original filename. This doesn't seem very useful. (However, if I can figure the commercial thing, it would be useful).

The first question, then, is whether there is a utility or script that will simply copy the mpg file, but with a name derived from a user-friendly name from the database, to some other directory from which I can copy, scp, etc. It seems like the transcode process should put it somewhere configurable and give it a user-friendly name of some kind. Am I wrong about this?

Any suggestions will be appreciated.

Wilma

---

### Post by ian dobson on 2009-12-26
Hi,

Maybe have a look at mythrename.pl [http://www.mythtv.org/wiki/Mythrename.pl](http://www.mythtv.org/wiki/Mythrename.pl) maybe that'll do what you want.

Regards
Ian Dobson

---

### Post by nickrout on 2009-12-26
> **ian dobson said:**
> Hi,

Maybe have a look at mythrename.pl [http://www.mythtv.org/wiki/Mythrename.pl](http://www.mythtv.org/wiki/Mythrename.pl) maybe that'll do what you want.

Regards
Ian Dobson

Never EVER use that script without the --link option!

---

### Post by wilma92010 on 2009-12-26
Awesome, worked perfectly (with the --link option).

Thanks!

Wilma

---

