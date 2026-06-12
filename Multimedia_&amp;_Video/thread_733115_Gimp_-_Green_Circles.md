---
title: "Gimp - Green Circles"
date: 2008-03-23
forum: Multimedia &amp; Video
---

### Post by tjasko12 on 2008-03-23
Hi Everyone,

I have a strange problem in Gimp I would like to be solved. Every time I start up Gimp, in Ubuntu 7.10, and then I open a picture, then after this, I drag my mouse cursor over the opened image. When ever I move the cursor, some green circle follows the cursor... It adds these green circles on the image, but when ever I save it, the circles are not there. I have attached a photo on what it looks like. The circles followed my mouse. I was on the pencil tool.. It seems that it only happens with the drawing tools. The brush, the pencil, circle, etc...

Does anyone know on how to get rid of this? It is quite disturbing...

Thanks,
Taylor

---

### Post by tjasko12 on 2008-03-24
Bump.....

Does anyone know how to fix this. Wow, this thread went to the bottom fast...

---

### Post by tjasko12 on 2008-03-25
Anyone know how this circle problem can be solved. It doesn't do this in the Windows version... Although I don't use Windows much anymore...

---

### Post by xc3RnbFO8P on 2008-03-25
Have you tried to reinstall Gimp? 
Do you dual boot?

---

### Post by tjasko12 on 2008-03-25
Yes, I do dual boot. But only because not everything runs on Linux... I don't go into Windows that much...

I'll try to reinstall GIMP. Thanks for the advice. I'll try that...

---

### Post by xc3RnbFO8P on 2008-03-25
How do you divide the harddisk drive between windows and ubuntu?
and how much space does windows use of its partition?
Did you defrag (windows) and run chkdsk before installing Ubuntu?

---

### Post by tjasko12 on 2008-03-25
Currently, there are 2 partitions on my disk. One for XP (~10gb), and Ubuntu (~8gb). Yeah, I use it on a 20gb disk... It works nicely though. Yes, XP is clean of fragmented files, and I ran checkdisk many many times... I actually had a problem installing Ubuntu, but I really don't want to get into that now... I figured it out... It's some problem with Dell laptops mostly...

---

### Post by xc3RnbFO8P on 2008-03-25
How much space does windows use of its partition?  Reason why I ask is, that windows partition free space could be dangerously low.

---

### Post by tjasko12 on 2008-03-25
I have 3gb of space left in Windows... I really don't care. It runs fine. I have plenty space left... ;)

---

### Post by xc3RnbFO8P on 2008-03-25
Once my son over wrote windows (dual boot with Ubuntu) and I got problem with Gimp in Ubuntu :) couldn't open photos.

---

### Post by Skimmer on 2008-07-01
Solution that worked for me:

The problem vanished after doing this adjustment in gimp:
File -> Preferences -> Image Windows -> Mouse Pointers -> Uncheck "Show brush outline"

After a search I located [this]("http://www.murga-linux.com/puppy/viewtopic.php?search_id=1501567748&t=29714") post which helped to solve the green circle problem.

My thanks to the discoverer!!
Side note- I'm running Xubuntu Hardy 8.04 on the box that had the problem, and Ubuntu Hardy 8.04 on a laptop with no evidence of the problem. Re-installing Gimp didn't help. My Xubuntu has an older Rage Mobility video card and runs Linux only.

Hope this helps!
Cheers, SK

---

### Post by tjasko12 on 2008-07-01
Sorry, but I cannot test this fix now. Mostly for the fact that I upgraded to a newer laptop made by Hewlett Packard....

This might help someone else who is having the same issue as we did.

Thanks for you help anyways,
Taylor

---

