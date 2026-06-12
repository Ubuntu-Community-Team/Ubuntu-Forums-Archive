---
title: "Problem backing up a new DVD"
date: 2010-03-24
forum: Multimedia Software
---

### Post by Garnett on 2010-03-24
I've been putting my DVDs onto my home network for a while without any probelms until now.

When I put in *Doubt* and try to rip it, the title tree (in both K9 and DVD::Rip) shows several titles of a large filesize and the same time duration (that of the film). About three of the multiple titles are exactly the same file size and duration and then there are about 3 more that differ slightly in both.

I think this must be some kind of anti-piracy measure. Obviously 6 files of 5 GBs wouldn't fit on a DVD so it must be some kind of error/trick.

When I try to backup the DVD it doesn't work.

Has anyone else experienced this problem?

---

### Post by Garnett on 2010-03-29
Anyone?

Are these DVDs with "dummy files" incapable of being backed up?

---

### Post by mc4man on 2010-03-29
> Are these DVDs with "dummy files" incapable of being backed up? 

If meaning backed up as dvd video (VIDEO_TS, chapter stops, menus, ect.) then that would depend on the degree of .ifo butchery.
Otherwise a player like vlc can 'rip' the movie to a .mpg file fairly easily

At the very least, with k9, you'd need to find the titleset that has the 'real' movie and exclude the bogus ones from the rip. (open the movie in vlc, start playing and ck. what title is being used.

You may need (in k9), to do a main movie only, no orig. menus, though possibly you could salvage then menus's, extra's if desired.

Otherwise, if you just wish to have a full disk .iso to use on your pc or network,(no further processing or burning to disk possible), then you can do a 'rip' to a encrypted, structure protected .iso that will play back just like the disk. (this assumes you can play the disk...

Note that the .iso's size will be the actual size on the disk, not the mis-reported one.

If so, a simple misuse of dvdisaster will work quite well and fast depending on the number of unreadable sectors which in this style of structure protection is usually low.

If that's the way you want to go just ask.
(I use dvdisaster for this, usually only takes about 10 - 12 min., plus has the added adv. of technically not circumventing any protections (css and structure.

---

### Post by Garnett on 2010-06-23
> **mc4man said:**
> open the movie in vlc, start playing and **ck. what title is being used**.How do I do this?

Edit: Apologies - found it with some googling:

[http://superuser.com/questions/81660/new-dvds-with-99-title-tracks-which-one-is-the-correct-track](http://superuser.com/questions/81660/new-dvds-with-99-title-tracks-which-one-is-the-correct-track)

*"start the DVD in VLC and start the movie/select TV show. When it runs you can check under Playback>Chapter what the corresponding chapter# is"*

---

