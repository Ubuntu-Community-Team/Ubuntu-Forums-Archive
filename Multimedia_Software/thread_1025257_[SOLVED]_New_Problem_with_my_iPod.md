---
title: "[SOLVED] New Problem with my iPod"
date: 2008-12-29
forum: Multimedia Software
---

### Post by GNUway Tech on 2008-12-29
Ok, so I solved the 1st problem only to have another one show up.

I am trying to use gtkpod to sync tracks to it, and all it keeps telling me is that the iPod is a read-only drive. I've tried running dolphin as root to reset the permissions on the iPod, and I can change them, but I can't save them. Even running gtkpod as root won't let me sync the tracks to it because it's set as read-only.:confused:

How do I change the permissions on the iPod????

---

### Post by qrst629 on 2008-12-29
Jordan 11 at Finish Line just won't quit - ever. Constructed for athletes who continue to pound the pavement day after day,Jordan 11 are comfortable, stylish and built to last, which is what you have come to expect from Jordan 11. Grab a pair of Jordan 11 and never look back.brandshoeswholesale.com carries a wide range of Jordan 11 Shoes, below is some more information and in depth links to our shoes catalog and products. [Jordan 11 Shoes](http://www.brandshoeswholesale.com/wholesale_Jordan_11_cid_425.htm)

---

### Post by pytheas22 on 2008-12-29
Have you looked at [this page]("http://www.damonkohler.com/2008/09/how-to-run-rise-of-nations-with-wine.html")?  Step 5 in particular might help you (you can probably ignore the other steps because you've already accomplished them).

---

### Post by GNUway Tech on 2008-12-30
I don't see how this has anything to do with my problem. I'm trying to sync tracks to an iPod, not play a game in Wine.

As I said, I can connect and mount the iPod. I cannot sync tracks to it because it is set as a read-only drive, and I cannot change the permissions on it through "sudo dolphin."

I need some way to change the permissions on the iPod, or a program that will sync the tracks regardless of the permissions. I wonder if I can't do that with "sudo chown."

---

### Post by GNUway Tech on 2008-12-30
Doesn't look like "chown" is working, or "chmod." Any suggestions????

I know someone in another thread suggested using Rockbox. I tried downloading that and checking it out, but it told me my iPod was an unsupported variant.

---

### Post by GNUway Tech on 2008-12-30
Problem solved. Anybody else can find the solution [here]("http://ubuntuforums.org/showthread.php?t=999300&highlight=mount+read+ipod#7")

---

### Post by GNUway Tech on 2008-12-30
I take it back, that didn't help. Would it help if I had it reformatted to Windows instead of Mac???????

---

### Post by mc4man on 2008-12-30
> Would it help if I had it reformatted to Windows instead of Mac

Never had any problems after setting up the ipod on a windows box.

---

### Post by pytheas22 on 2008-12-30
> Have you looked at this page? Step 5 in particular might help you (you can probably ignore the other steps because you've already accomplished them).

Sorry, I posted this in the wrong thread.

As for your real problem, please post the output of these commands while the ipod is plugged in:
```

ls -l /media
lsusb
```

Also, does it make a difference if you boot your computer with the ipod unplugged, and don't plug it in until you're logged into Gnome under the use account that you want to use to connect to the ipod?

---

### Post by sleepyjon on 2008-12-30
I had a problem similar to this using amarok for my ipod. 

If you have the this file on your ipod, nothing else will read/write to it:
```

(Ipod mount point)/iPod_Control/iTunes/iTunesLock

```

---

### Post by GNUway Tech on 2008-12-30
Problem solved. I finally broke down and had it formatted to Windows. This is only my 1st experience using an iPod, and it was easily a little more trouble than I would have liked it to be.

I swear, Apple needs to port to GNU/Linux. They have been stalling on that for too long. It would make everything so much easier if we could just run iTunes on GNU/Linux. Not to mention, let them appeal to a broader customer base.

---

### Post by pytheas22 on 2008-12-30
> I swear, Apple needs to port to GNU/Linux. They have been stalling on that for too long. It would make everything so much easier if we could just run iTunes on GNU/Linux. Not to mention, let them appeal to a broader customer base.

Unfortunately Apple is too obsessed with keeping things super-proprietary to ever think about Linux, I imagine.  Steve Jobs is perfectly happy to steal the work of free-software projects (the BSD-based kernel in OS X and the KHTML engine of Safari are the most famous examples), close it up and profit off of it, but Apple's relationship with free software is sadly only one-way.  Perhaps if more people realized that Apple is worse than Microsoft when it comes to cooperating with Linux, they'd stop treating Steve Jobs as a messiah and gobbling up everything he sells just because it's made by him.  But as long as the cult of Apple persists, I don't see it having much incentive to do anything nice for Linux users.

Sorry, I couldn't resist a shot at Apple...  I am glad your problem is solved, and sorry again for my misplaced post in your thread yesterday.

Also FYI: you can run iTunes through wine (or so I'm told) and use most of its features, it just can't sync with the iPod.

---

### Post by GNUway Tech on 2008-12-30
I have to say, at least Apple hasn't been so obsessed with trying to destroy GNU/Linux and free open source software. Microsoft has, in the past, all but made it their mission statement to rid the world of free open source software by any legal means they can. Of course, they always lose. But, I still think that pretty much makes Microsoft the one for us to fear the most. Especially since they actually managed to talk Novell into working with them to make SUSE "more interoperable" with Windows. If I were Novell, I wouldn't have trusted them for a second.

I have tried using iTunes in Wine, and I have never been able to make it work. I have long since given up on it.

---

