---
title: "Submitting to CDDB"
date: 2008-04-22
forum: Multimedia Software
---

### Post by toastyspoon on 2008-04-22
Hello all,

I am new to both Ubuntu and this forum, and have a rather urgent need to submit to the CDDB database as soon as humanly possible! I used to use winamp to do this but of course I can't now. Could someone point me in the right direction for this probably quite obvious query?

Thanks in advance
Toasty

---

### Post by OzzyFrank on 2008-07-16
Yeah, I wouldn't mind knowing too guys. I assume someone knows this out there?? And is there any plugin or something for the default player, Rhythmbox?

---

### Post by OzzyFrank on 2008-12-18
Still no takers on this guys?? I just got a new album that comes up as unknown, and would like to submit the info. I've ripped the album ("The Unseen" by EYEFEAR) via Rhythmbox, and entered the artist, album and track titles prior to doing so (so the tags are now there). If there is a program (or way via Rhythmbox) to scan these files and upload the info, please let me know.

---

### Post by OzzyFrank on 2009-02-04
So there's no way to do this in Ubuntu?

---

### Post by krggb on 2010-12-03
It's some time since your question, but let me anyway give an answer that I just figured out. Warning: I will assume you are not afraid of some geeky command line tools. ;) I hope this is better than nothing.

I will also assume that you have an email system such as postfix set up and working (so that you can send email from the command line using a command such as "mail").

Install the abcde, lame and id3v2 packages and run:

  abcde -o mp3

When prompted whether to edit the CDDB data, answer yes, enter your contribution, and when the program starts ripping, press Ctrl-C to abort it. Now you will have a subdirectory called abcde.something, where something is your disc id. Go to that directory and run:

  cddb-tool send cddbread.0 [email]freedb-submit@freedb.org[/email]

There may well be a more "user friendly" way to do this, too, I hope.

---

