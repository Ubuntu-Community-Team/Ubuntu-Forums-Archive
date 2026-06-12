---
title: "odd problem with running k9copy under gutsy"
date: 2008-01-06
forum: Multimedia &amp; Video
---

### Post by porphiron on 2008-01-06
Lo folks!

I have had a look at other peoples posts but no one seems to quite match this one.....

k9copy / feisty worked like a dream i used to run multiple instances of k9copy, usually around three and be able to leave it running, goto work comeback and watch nice shiney avi files without messing around with dvds. 

I recently upgraded to gutsy and all seemed to work and look great, until installing k9copy.  when encoding avi files I use xvid for vid, copy for audio and 2pass and the version of k9copy that comes in the deps 1.1.3 afaik......now under gutsy I can only run one instance as the first pass, if it works just seems to lock when it gets to 100% and the counter just carries on, say if it is going to take 2hrs 10mins, it reaches that and just carries on going......and going....and going.....last night it went up to 10 hours before I stopped it.

so far one dvd worked but that took 6 hours and its not like its a slow machine i am using its a sempron 2600+ with 2GB of matched mem!!

like I said under feisty it ran fine so its not the machine, I have tried dvdrip but it wont allow multiple instances and I use decrypter under wine to rip the discs to hdd (I like it it works!)

any ideas??

Ta for reading and an even bigger TA! if you can shed any light on this problem....


Jan

P.s. I tried compiling the lastest sources it configured ok but just errors about 2 or three mins into compiling at the same time everytime...will post the exact error later as am at work

CHEERS!

---

### Post by porphiron on 2008-01-07
Just to update, the problem seems to be machine independant....but I think I may have sorted the problem.....

machine 1: sempron 2600+ 2GB mem, i managed to install k9copy using the link below (many thanks to the original author!!)

[http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy](http://ubuntuforums.org/showthread.php?t=607991&page=3&highlight=k9copy)

k9copy runs slower but have managed to get 2 instances running side by side at an acceptable speed.

on machine 2: Athlon 3400 2GB mem, I added the deps from the k9copy webpage to my sources list, which allowed me to install an older version 1.1.3 which works like a dream. (this did not work with machine 1 as it just runs like a steamtrain but doesnt do anything, where as for some reason no matter what, even having followed the above link it will not compile on machine two)

go figure.........hope any of this helps!

Porph!

---

### Post by mc4man on 2008-01-07
If you compile it using checkinstall you can use the .deb created in the k9copy1.xxxxx folder to install in any other machine

edit; while i don't use mpeg4 encoding I did test it last week for the hell of it and ran in to a similar issue as you, though in this case it happened in pass 2. It looks like mencoder was silently crashing and the k9 process was continuing (while doing nothing really). When I read your post last night I decided to try again using some small samples (reauthored 2 chapters into a new video_ts) and the same thing happened on 1st. attempt. Yet on subsequent attempts it ran perfectly and completed the job. If you pull up the system monitor you can see the activity should stay mainly with mencoder except for a few seconds here and there and when going from the first to second pass. I guess that mencoder may crash once and a while for some unknown reason and at this point hasn't again.

---

### Post by porphiron on 2008-01-08
Think I may have nailed the problem......

It looks very much like k9copy / mencoder dislikes lvm2 volumes, I have been trying to encode files from an lvm volume and .in a bid to cover every corner i slapped on an external hard drive copied the backups to it and have accessed them from there, lo behold k9copy 1.2.1 seems to work.....still cant get 1.2.2 to compile tho...but no matter



Porph

---

### Post by mc4man on 2008-01-08
I don't mind compiling , I find it interesting but as someone else suggested
[http://www.getdeb.net/app.php?name=K9Copy](http://www.getdeb.net/app.php?name=K9Copy)

---

### Post by porphiron on 2008-01-08
Cheers mc4man!

I looked on getdeb a couple of days back but didnt find the latest version,

 I must admit am now getting a bit obsessed with this, but did a speed test between 1.2.1 and 1.1.3 and actually found little difference in speed and tbh I prefer the remote countdown bar from 1.1.3 that I can stick in the corner of the screen as a reminder, against the preview window of 1.2.1.

Oh and also with 1.2.1 i keep forgetting to untick the subs as it encodeds em automatically so keeping having to dump the encodes!

Having said that now that a .deb of 1.2.2 is sat infront of me I'le have a bash

thanks again mc4man


Porph!

---

