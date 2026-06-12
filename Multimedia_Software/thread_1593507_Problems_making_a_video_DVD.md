---
title: "Problems making a video DVD"
date: 2010-10-11
forum: Multimedia Software
---

### Post by Sylos on 2010-10-11
Hello all and thank you for looking.

I am trying to make some video DVDs from my 9.10 installation and have hit on some snags that are a bit irritating. Some googling and forum searchin doesnt seem to have found a solution so here we go....

I am starting with avi files that need converting to mpeg2/VOB (not sure if there is a difference between the two - any guidance gratefully received). I tried using DeVeDe which converted them and burnt the iso for me. This was ok BUT the DVD would freeze and then skip every few minutes. I have managed to cure this by removing the option for puttin 5min skip markers on it (a bit lame bit still workable). However, the DVD seems to make my DVD player spin and jiggle the disc a lot whenever the menu is up. Im not sure if this is potentially damagin to my DVD player but it doesnt sound good.

So I tried Qdvdauthor - this crashed a lot during the process of creating my menus etc but it did eventually create the videos ready for to mkisofs - sadly the result was 7gig in size and therefore useless as there doesnt appear to be an option to adjust quality to fit the disc.

So I tried Todiscgui - this does nothing when I press the "Run todisc now" button. I ran it from terminal and it did generate some code to feed to todisc. I copied that and pasted into a terminal but todisc complained about:
```
Missing option: -out
```

or something to that effect im not sure what it wants.

Which leads me to here. If anyone has any insights into any of the above (or anything new for me to try) please let me know.


Many thanks

---

### Post by mjitkop on 2010-10-11
Hey there.

For information about VOB files, take a look at this:
[http://en.wikipedia.org/wiki/VOB](http://en.wikipedia.org/wiki/VOB)

My favorite application to make video DVDs is [DVDStyler]("http://www.dvdstyler.org/"). It is in the Ubuntu repository.

You can import pretty much any type of video files in it and it will convert them to VOB files automatically. It is very intuitive and easy to use. 

Does you DVD player work fine with other types of discs? 

Does your burnt disc work the same way in other DVD players?

This is strange.

Good luck.

---

### Post by Sylos on 2010-10-12
Hi there and thanks for the post.

The initial problem of skipping every 5 minutes was replicated on both my ps2, dvd player and my dads dvd player so it seems universal. The noise issue is different on different hardware.

I just tried DVDStyler and got a nice DVD out of it. There are no issues of skipping and it works fine in my stand alone DVD player. However, although it plays it makes the most god awful clattering and twitching in my ps2. It sounds like the reader is spinning it and then hitting something every few seconds then starting to spin it again. Very strange. Any idea why this would be? I have tried other home made disks burned from windows - same batch of DVD-Rs but no problems. I hate it when windows gets one up on me!

Any ideas gratefully received.

---

### Post by Sylos on 2010-10-13
Bump?

---

### Post by Brandel Valico on 2010-10-13
I usually suggest ManDVD for creating DVD's myself. As for the clatter. I get that on occasion when I get a disc that while useable is pressed off balance. Had a batch of Memorex disc's that over half were this way 3 were un-usable, the rest worked just fine. Figured out after a few tries that burning the disc's at the slowest speed I could instead of max seemed to settle them down. Not sure if this is the issue on your end but give it a try if you have a spare dic to burn.

Just as a tip you mentioned Qdvdauthor giving you a 7 gig iso. When I used that program before I switched to ManDVD I would create the iso and then run it through K9 Copy to decrease the size to the 4.5 range for standard DVD disc's. This is also how I make Backups of my Dual Layers.

---

### Post by Sylos on 2010-10-14
Thanks for the reply.

Im certainly going to try the slower speed burning (I normally leave it on auto) with my next DVD. A friend also suggested the cheap DVDs on a spool that I have may well be the culprit (hence some work and some dont). It is interesting that the PS2 is more sensitive to it than the standalone DVD player - perhaps something to do with the reader?

As for qDVDauthor, thanks for the tip but I think Im gonna leave that one. It crashed a good 7 or 8 times before I managed to get it set up to start transcoding the media - DVDstyler has been much more stable for me and seems to have all the features I need. I'll keep the K9 copy trick up my sleeve though for if I every need it.

Many Thanks,

---

