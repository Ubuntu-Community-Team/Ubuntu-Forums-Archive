---
title: "MythWeb - recordings link when using more then one drive?"
date: 2008-05-31
forum: Mythbuntu
---

### Post by OldGaf on 2008-05-31
Hi all,

I have just installed Hardy Kubuntu desktop and installed MythTV. I have been using myth under Kubuntu for a few years now and have a fair grasp on how it works.

However, with the latest MythTV release, you can have separate drives and folders for your recordings so I figured I would try it. 

My setup:

1 - 80 gig sata2 drive for the OS and music.
2 - 160 gig sata2's for my recordings.
1 - hauppauge 150
1 - hauppauge 500
1 - AMD 3600+ x2

I used to LVM the 2 160's into one big storage unit mounted at /media/data with all recordings in /media/data/recordings. So, if I wanted to stream / download a recording to another box in the house I had to make a soft link to the recordings in the Mythweb data dir pointing to /media/data/recordings.... pretty strait forward.

In the new setup, I kept the 2 160's separate and put live TV, kid’s stuff,  sitcoms etc in folders on one drive:
/media/data1/live
/media/data1/nikki
/media/data1/tom
/media/data1/sitcoms

and other (more important stuff) on another drive:
/media/data2/rome
/media/data2/movies

It is more complicated, but I can easily copy a folder if I want to back something up etc... though I probably went too far.

Anyway, my question is..... how do we point to all these locations in mythweb/data with a soft link in order to allow them to be streamed / downloaded?

Even if I went back to LVM, or just replaced the 2 with one 500 gig drive, I still would have a problem using folders to separate / organize the media.

Any ideas anyone?

---

### Post by OldGaf on 2008-06-01
bump

---

### Post by OldGaf on 2008-07-03
Nothing eh?

Oh well.... I pulled my 160's and put in a 750 gig and reverted back to the "old way".

---

