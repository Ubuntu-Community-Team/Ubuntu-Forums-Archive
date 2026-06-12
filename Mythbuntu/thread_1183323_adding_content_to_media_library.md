---
title: "adding content to media library"
date: 2009-06-09
forum: Mythbuntu
---

### Post by niemo810 on 2009-06-09
Hi, I'm having a bit of trouble with mythbuntu 9.04, and it's making me feel really, really stupid. I'm hoping someone can help.

I can't figure out how the heck to add any content whatsoever to my media library. Going to Utilities/Setup>Setup>Media Settings>Music or Movies, and changing the folder to the proper directory does nothing for me. I've verified that there is actually content in the folder I'm trying to add, from both an internal and external drive. I'm stumped. And I tried searching the forums...

What the heck am I doing wrong?

-Rob

---

### Post by nickrout on 2009-06-09
In the case of videos go to video manager (under utilities/setup). This will scan for new videos and add them to the database.

Theres a similar mechanism for music. Under startup/utilities then music tools then scan for new tools.

---

### Post by niemo810 on 2009-06-10
I tried going to video manager, but the only thing that's in there is a dialog box that asks for an IMDB #, and it won't let me type anything in...

As for music, it found my music and I added it, to which it said something along the lines of "added successfully" but... there is nothing in my library.

Thanks for the quick reply

---

### Post by Bucky Ball on 2009-06-10
Sounds like perhaps its sticking them in the wrong place (not the one you expected). Can you open a terminal and try to find one of your music or video files with:

locate YOURFILENAME

... for instance:

locate killbill

... and see where it has put them. It is saying 'added successfully,' so they are going somewhere.

---

### Post by newlinux on 2009-06-10
> **niemo810 said:**
> I tried going to video manager, but the only thing that's in there is a dialog box that asks for an IMDB #, and it won't let me type anything in...

As for music, it found my music and I added it, to which it said something along the lines of "added successfully" but... there is nothing in my library.

Thanks for the quick reply

The imdb # thing may be this bug:

[https://bugs.launchpad.net/mythbuntu/+bug/339880](https://bugs.launchpad.net/mythbuntu/+bug/339880)

fix is in the bug report

If you don't care about metadata, you can change your settings so that you can browse videos that aren't in the database (under the video settings where you set the path - set the views (list, gallery, browse) you want to allow for browsing.

---

