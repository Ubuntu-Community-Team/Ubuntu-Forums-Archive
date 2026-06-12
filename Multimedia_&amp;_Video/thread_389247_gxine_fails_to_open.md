---
title: "gxine fails to open"
date: 2007-03-20
forum: Multimedia &amp; Video
---

### Post by drpaul on 2007-03-20
when I try to open gxine I get the following

Creating link /home/paul/.kde/socket-hppaul.
can't create mcop directory

Someone have a clue as to what and where it is trying to do this?

TIA

Paul

---

### Post by drpaul on 2007-03-20
This was one of many sound problems that seemed to be getting progressively worse over the last week or so.

Since Alsa released a final .13 version I decided to wipe my .13rc3 driver and put in the final .13.  Compiling and installing the driver and rebooting seemed to reenable sound.

I looked at adding the same version of the utils, but ./configure failed due to not having appropriate version of libasound headers [don't think I had any]. 

Would like to find a good set of instructions for how to do up the complete set of alsa packages.

Anybody?

Paul

---

