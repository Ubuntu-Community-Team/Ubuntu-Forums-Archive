---
title: "dvds don't play on set top box"
date: 2009-10-03
forum: Multimedia Software
---

### Post by jayem on 2009-10-03
Hello,

I've tried a plethora of linux dvd applications to no avail.  All seem to work.  The created dvd burns with no reported error and then will play back reliably on any computer irrespective of operating system.  However, the dvds don't play back reliably on set top boxes, certainly not mine.  Interestingly, using the same .iso file and media and the same machine only when running windows the dvds work reliably on set top boxes including mine.

Has anyone else experienced this?  If so, does anyone know of a solution?

---

### Post by inobe on 2009-10-03
i haven't had any troubles, in fact i needed to replace my last set top box with a newer one and they still play fine.


you may want to tell us how you setup things to do this in order for us to determine if you've missed something ?

---

### Post by jayem on 2009-10-04
I first had the machine set up with Mythbuntu 9.04.  I then loaded up all kinds of burning software (brasero, k3b, ImgBurn under Wine, etc...).  All of these programs seemed to run well.  In fact I assumed that my problem was that my set top box and the dvd players of my friends were faulty or just didn't work well with the media. The dvds created with mythbuntu and the other applications that never worked on my dvd player worked just fine on any computer I tried.

I thought that my problem was my dvd burner so I replaced it recently but the problem persisted.  Exasperated, I loaded up Windows XP on my Ubuntu box, used the same ImgBurn file I was using under Wine and successfully burnt a dvd that played really well on my dvd player attached to my TV.  I then thought that I'd give Ubuntu 9.10 beta a whirl to see whether this would work but unfortunately I am having the exact problems I had before.  I burnt the same .iso to dvd with brasero and it didn't work in my dvd player despite working well in the computers.

I can work around the problem by simply putting the .iso images onto a memory stick and then burning it to dvd on my windows machine but I would really like to work through this (bug?).  I'm also wondering whether many others either work around the problem by reverting to windows to burn the dvds or whether they simply assume that the media they've chosen is no good, when in fact it is just fine and the problem is Linux or Ubuntu.

---

### Post by inobe on 2009-10-04
what app did you use to create the .iso, also on what platform were they created ?

what type of media are you using ?

that's my last questions...

i am assuming these .iso's are not authored for a specific region ?


sorry' i am dumbfounded as to why you are experiencing this.

---

### Post by jayem on 2009-10-04
I used DeVeDe.  However, I've had the same problem using QdvdAuthor, Avidemux, k9copy and whatever Mythbuntu uses.  I don't know what you mean by "platform" unless you're referring to the operating system which is linux (Mythbuntu 9.04 or Ubuntu 9.10 as mentioned in my previous reply).

I've tried several media.  Memorex, Fujifilm, Imation and Sony.  All of which work on stand alone dvd machines when burnt with windows and none of which work any better than unreliably when burnt under linux.  If the linux made dvd plays at all it freezes, shakes and otherwise presents a horrible video stream on the stand alone dvd players.

The .iso disk images are not being authored for any particular region.

---

### Post by inobe on 2009-10-04
i think i'm seeing the picture here, devede will take say an avi and convert to dvd, hmmm


do you have the medibuntu repo ? **be sure to understand the copywrite laws in your country prior to using said software** just sayin......

i swear by handbrake and devede, i have never had "ever" any problems.

---

### Post by jayem on 2009-10-04
The issue is not copy protection.

The problem has something to do with writing the dvds.  For example, when I burn a dvd that won't be recognized in the dvd player attached to my TV but copy it in a windows machine then the copy will play perfectly.

I'm convinced that there's something messed up with the way in which Linux or Ubuntu writes the dvd.

Any help would be appreciated.

---

### Post by inobe on 2009-10-04
> **jayem said:**
> The issue is not copy protection.

The problem has something to do with writing the dvds.  For example, when I burn a dvd that won't be recognized in the dvd player attached to my TV but copy it in a windows machine then the copy will play perfectly.

I'm convinced that there's something messed up with the way in which Linux or Ubuntu writes the dvd.

Any help would be appreciated.

i hope you get it worked out, apparently you are the only one experiencing this and i can only suggest what works.

restricted-extras

medibuntu repo

handbrake and devede

ffmpeg

xine

nvidia vdpau

---

### Post by jayem on 2009-10-18
Anyone else with any similar experience?

---

### Post by dhj on 2009-11-12
Hello, I noticed something similar yesterday when trying to burn a DVD with DVDStyler on Hardy. The disc plays on the Ubuntu box but two different Windows XP machines can't even see the contents of the disc, showing a format error instead.

---

### Post by dhj on 2009-11-12
Follow up - I tried DeVeDe in place of DVDStyler and got the exact same results on the two Windows XP boxes - a different error on each, one was Service Pack 2 and the other was Service Pack 3. Each iso was burned once on Ubuntu and once on XP SP3, just to be sure.

However all four discs played fine on an ancient Humax combo VHS/DVD player (as well as on Ubuntu with gmplayer or totem). I checked out the DVD disc structure using IsoBurner on Windows XP which showed a hybrid ISO9660/UDF filesystem with UDF 1.02 - just as it should be. I can only conclude that Ubuntu with DVDStyler or DeVeDe can make perfectly valid video DVD's on DVD-R, but Windows XP doesn't want to read them.

Since the Windows XP machines can read commercially produced DVD video discs, I'm inclined to think that XP's support for home made DVD-R videos is buggy, or at least not standards-compliant (wouldn't be the first time...)

Cheers!

Daniel

---

### Post by jayem on 2009-11-15
Hello,

Thank you for your reply.

I'm fairly technical but I don't know how to compare disc structures.  Anyhow, my set top box is a DVD recorder that only burns DVD +Rs.  Since buying this thing years ago, I've been in the habit of only buying DVD +Rs even though I've long ago stopped using it to record TV shows (especially as so much has since gone digital).

I suspect that Linux has trouble with the DVD+R discs.  Since my last post I've purchased an ASRock 330 and repeated the above experiment and have had the same conclusion (Linux continues to do something funny while copying the Linux created DVD+R to the same medium on a Windows machine produces a DVD thay plays on my set top boxes.).

I've not had a chance to really try out my theory by repeating the above excercise with DVD-Rs but I have tried with DVD+RW and the disc produced entirely with Ubuntu 9.10 plays perfectly well on my dvd set top box.

In the mean time I've been copying the .iso files I've created to my wife's Vista machine which burns the DVD+Rs flawlessly onto my DVD+R media.

---

### Post by jayem on 2010-01-06
Well I finally bought some DVD-Rs.  I've only tried two so far.  The first was a coaster.  The second seemed to work fine.

I bet that the trouble with linux is only with the dvd+r disks.

I'll post again as I try burning other DVD-R disks.

---

### Post by cscj01 on 2010-01-08
Folks, I can confirm the exact problem jayem has.  I have Ubuntu 9.10.  After using everything in sight (Brasero, DeVeDe, Avidemux, QDVDAuthor, ISO Master, GnomeBaker, and probably some I cannot recall), I have yet to produce a DVD that will play in a set top box with DVD-R or DVD+R media.  If I burn the same thing under XP using ImgBurn, Infrarecorder, Roxio, etc), they all will play on set top boxes.

I do not know enough to find out what is wrong, but I can play all these coasters on my computer.  I can mount the iso before burning and play it.  I have tried to use the lowest speed setting as well as the highest speed setting.  I have tried this on my Sony burner and my Samsung (TSSTCorp) burner.  At the rate I'm using blank DVD's, I may own stock in those companies in a couple of days.

There must be someone who knows something that can help.  I certainly need it.

---

### Post by boredpcguy on 2010-01-11
I didn't see this mentioned anywhere, so as basic as it is, I have to ask.

Is everyone choosing the proper default format for their country (not neccesarily regional settings)?

PAL format vids won't work in the USA/Japan/parts of South America.  
Check this link, [http://en.wikipedia.org/wiki/File:PAL-NTSC-SECAM.svg](http://en.wikipedia.org/wiki/File:PAL-NTSC-SECAM.svg) , to make sure you have chosen the correct format (NTSC/PAL) for your country.  I use the same setup as everyone else and have no issues on home equipment.  DeVeDe seems to install with PAL as its default format as well as selecting it when you add a new video sometimes.  Just a thought, because my 9 year-old computer transcodes [EDIT: and burns] just fine, albeit 4-5x slower than everyone else's computers. :P

[EDIT AGAIN:  BTW, I use only DVD+R's.]

---

### Post by djb0110 on 2010-01-11
I'm having trouble as well, I first tried to copy using Brasero, then I used DeVeDe (NTSC for America) , then tried to render to a different format using Cinelerra and then use DeVeDe again, had the same result. The video would not play in the dvd player.   In the past I had no problems with using DeVeDe or Brasero, but today I suddenly can't get a copied video to run in a dvd player. I am using DVD-R  made by Sony. Ubuntu 9.04 is the operating system. I have made many copies in the past with no problems untill today. I make copies here were I work (in a museum) to display in numerous dvd players. I used up my last 3 dvd's before leaving today so I will try again to copy a different video to see if problem goes away. I suspect it's the specific video I'm trying to copy. It plays fine in VLC on the computer. But in two differnent dvd players (known good ones) The copied DVD doesn't play in them.

---

### Post by jayem on 2010-07-13
I just burnt a coaster with Brassero running on Ubuntu 10.04.  The disk played on the computer but not on the set top box.

... The problem persists ...

---

