---
title: "Answer to Brasero DVD burning issues"
date: 2009-10-09
forum: Multimedia Software
---

### Post by a4000 on 2009-10-09
[SIZE=2]OK I've noticed a lot of people having questions or issues about burning dvd in Brasero and mostly its the same problem

"I can't burn dvds because it says unsupported or I need plug-ins"

When you open up Brasero most people are trying to create a dvd that works with their dvd players to watch on their tv, so they click the "Video projects" button to create a dvd that works in their dvd player according to the decription.

Most of the files being used are either .avi or mp4 video files and then when you try to burn the files it says you need plug ins and the "burn" button is grayed out. 

Answer:

Brasero does not convert files at all and it automatically assumes the files you put in the "Video projects" section are either mpeg2,.iso or a video ts folder (basically a dvd rip).

These files do not work because Brasero does not encode or convert files at all so avi and other video files need to be converted to a proper format before they can be burned, for this I recommend using DeVede that you can get throught the terminal (sudo apt-get install devede) or with synaptic package manager.

(if your dvd player can read .avi,divX,Xvid, etc then just burn them with Brasero as a data dvd and it will work fine since no conversion is needed)

I use and like Brasero a lot and think it's the best choice for any type of burning in Gnome, it is not broken and does not have many bugs just little misunderstandings like this. K3b is king of burning in linux of course but if your a Gnome user like me i would give Brasero a chance.

thank you for your time
A4000[/SIZE]

---

### Post by ed bear on 2012-04-05
a4000, I don't think your answer could be correct.

I have burned all manner of files to DVD+R with Brasero, including complete commercial DVDs small enough to fit on a DVD+R. I have a Dual-Layer drive (an LG H54N) and have no problems burning to single-sided disks, but I get that old "the medium is not writable with the current set of plug-ins" message when I try a to write a DL one with ANY data.

ED BEAR

---

