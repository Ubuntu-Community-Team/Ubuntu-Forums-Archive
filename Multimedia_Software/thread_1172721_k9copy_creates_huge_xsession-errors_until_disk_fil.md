---
title: "k9copy creates huge xsession-errors until disk fills"
date: 2009-05-28
forum: Multimedia Software
---

### Post by maestrobwh1 on 2009-05-28
I have had great luck using k9copy until recently.  It is picky on every other DVD Using Kubuntu intrepid.  Some just work.  Is this the result of better copyright protection?  If so, no big deal...

When I open some dvd's in k9copy, the hard drive goes nuts.  
It just goes forever until I terminate k9copy.

It creates this in xsession-errors

[INDENT]X Error: BadWindow (invalid Window parameter) 3
  Major opcode:  20
  Minor opcode:  0
  Resource id:  0x460144c
*** Zero check failed in ifo_read.c:1539
    for c_adt->zero_1 = 0x43b6

*** libdvdread: CHECK_VALUE failed in ifo_read.c:1543 ***
*** for info_length % sizeof(cell_adr_t) == 0 ***


*** libdvdread: CHECK_VALUE failed in ifo_read.c:1571 ***
*** for c_adt->cell_adr_table[i].vob_id > 0 ***[/INDENT]

And that continues forever.

At one point, when I did not know why it was taking so long in the preview screen, I got a disk full error.  The xsession-errors file was 2.3 GB!

---

### Post by glancep on 2009-06-12
I am having the same issue with my xsession-errors file filling my partition... did anyone ever figure this out?

Thanks...
Gideon

---

### Post by maestrobwh1 on 2009-06-14
It is because the DVD is protected.  I just figured this out.  I had no problems with DVD's I made, but I did from ones that I rented (and didn't have time to watch yet - the whole reason I copy anything is because of this).  There are a variety of tools to "deauthorize" a DVD.  I found one that works from the command line but I can't remember the name off hand, and there are a variety of freeware programs for XP as well.  They basically just copy the contents of the DVD to a folder so it is pretty quick because it doesn't need to re encode the files, then you can open the folder with K9 re encode it to a smaller DVD like you would by opening the CD itself.  

It didn't take long for the program to work.   K9 seemed much much faster reading from a hard drive so I am going to experiment and see whether doing this before using K9 (and not have K9 read from a DVD) actually makes the entire process more quick.

Most of the time I just copy it to the drive now and open the folder as if it were a dvd and watch the movie that way then just delete the folder... no need to shrink and encode most of the time. Still, it is nice to make compact iso files made with K9 which VLC will open and play.   Good way to have movies on your laptop when traveling and using the HD is much less power hungry than using an optical drive.  I can't remember the last time I actually burned a movie to a DVD disk.

---

### Post by glancep on 2009-06-14
Thanks for the reply.  I just figured it out last night, too.  What I found, though, is that if you install libdvdcss (which is what is used to decrypt the DVD) then K9Copy will work!  I imagine that is accomplishing the same thing as the other app that you found (except that you don't have to copy it to your HDD first if you don't want to).  Now, it is not the most straightforward process to install libdvdcss because it is not in the default repositories that are set up with KPackageKit--it is part of the Medibuntu repository.  Details about how to add the repo and install libdvdcss can be found here:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

K9Copy is working quite nicely for me now--about the same as using DVD Shrink with Windows.

Good luck!
Gideon

---

