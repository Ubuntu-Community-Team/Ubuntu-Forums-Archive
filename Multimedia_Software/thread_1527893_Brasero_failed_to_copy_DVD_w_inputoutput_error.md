---
title: "Brasero failed to copy DVD w/ input/output error"
date: 2010-07-09
forum: Multimedia Software
---

### Post by uRabbit on 2010-07-09
Working on backing up my DVD library. Anyone know why Brasero would fail to copy data due to an input/output error? Movie was Toy Story 2, disc 1.

---

### Post by mc4man on 2010-07-09
Possibly due to structure protection which would include some number of unreadable sectors.
(Disney almost always uses sp of some sort.

Sometimes brasero can read past those sectors though it would be 50-50 if you have a playable rip, (based on limited tests.

That's a 2 yr. old or so release - k9copy may be able to handle the sp.

I don't have installed, though you'd probably want to use the wizard, and set the target size above the disk size to avoid k9 from trancoding the rip. (trancoding - requantization - has definite limits as to maintaining acceptable quality, though 'acceptable' is subjective and also depends on other factors

---

### Post by uRabbit on 2010-07-10
Not even using a disc, yet. Creating ISO. 

Anything that can handle it all?

---

### Post by mc4man on 2010-07-10
> Not even using a disc, yet

Isn't your movie on a 'disk'?
You're somewhat implying that you're trying to use brasero to "copy disc.."
If so and it's erroring then, as mentioned, try k9copy  to rip the dvd. (disk)

Or run this in wine, will do most all titles/structure protections - there is a free version within the program - it's a bit 'hidden'

> Note: The setup file includes the trial version of DVDFab Platinum as well as Free DVDFab HD Decrypter.
[http://www.freewarefiles.com/DVDFab-HD-Decrypter_program_41940.html](http://www.freewarefiles.com/DVDFab-HD-Decrypter_program_41940.html)

---

### Post by wannabegeek on 2010-07-10
would dd work from command line to make the .ISO ?  or does the sp still get in the way ?
I am thinking of backing up some stuff too....
thx
wbg

---

### Post by uRabbit on 2010-07-10
I've copied two Pixar movies thus far with no issues.

Okay, I'm trying dvd::rip. But it's so geared toward advanced users that I can't even figure out how to BEGIN the rip. Ugh!

edit: Using k9copy. Hope this one works. Wish Brasero would do it; I do enjoy that one much more.

---

### Post by uRabbit on 2010-07-10
k9copy worked with that one.

---

