---
title: "Banshee sometimes won't play tracks"
date: 2011-05-21
forum: Multimedia Software
---

### Post by George_ on 2011-05-21
I'm running Ubuntu 11.04 on a Virtualbox VM under a Windows 7 host.

Sometimes Banshee won't play anything. The play button doesn't change, the progress bar doesn't start moving, and Banshee says it's idle. This doesn't always happen, sometimes I can play a few tracks fine and then suddenly in the middle of a track Banshee will stop and nothing will get it going again. Other times it happens from startup. Neither restarting the player nor rebooting the VM necessarily helps.

I've checked whether the libGL.so.1 and libGL.so.1.2 are in /usr/lib/ and they're not.

---

### Post by George_ on 2011-05-23
Anyone? Please?

---

### Post by futralistic on 2011-09-10
I had this same problem today,it happened after a reboot. Before the reboot banshee worked fine. 

I went to my music folder and selected a song there, chose open with banshee and it worked. After I did that it would even play songs from within banshee again. 

Not sure what will happen after the next reboot

I am running it through an actual Ubuntu 11.04 install though.

---

### Post by butsuriboy on 2011-09-14
@futralistic
I had the same problem, was about to use your solution, and then realized, I had not mounted the drive my music files were stored on (they're on my windows partition, so for banshee to access them, that partition has to be mounted).  I'm guessing our issue is the same?? (esp. considering how rebooting will dismount everything :P

@George_
I can't really help, but based on my "problem" (written above), my best guess would be a similar "mounting" problem.  Perhaps the VM software has trouble accessing certain files, perhaps, say, when some other program is using them natively in Windows?

cheers

---

### Post by a_movingtarget on 2011-09-16
Hi everyone,

I have the same problem on my Asus netbook.  I just installed the Jolicloud OS 1.2 (awesome for a netbook) and after loading about 2k songs onto banshee, i tried to play some, and nope.  The sliderbar says "idle" all my music is in my "music" folder in the file system, not actually stored on another partition.  Therefore, it couldn't be the mounting issue, right?  I did this on the same machine w/ another Ubuntu based OS and it worked fine...  Someone?  ANyone??  Me needs some music.  ):P

---

### Post by |edmund| on 2011-09-16
This happens to me every time I reboot. All I do is go to "Import Media" and import anything (I just import one song) and after that it works. Really weird fix.

---

### Post by futralistic on 2011-09-24
@butsuriboy- Yes that was the exact problem I was having.

---

### Post by xSyNisTeRx on 2011-09-24
It just happened to me too. I actually made an account just to post my problem lol. I fixed it though.. I found the problem was that I changed the location of my media files that were attached to the banshee library. Basically I reorganized my media and threw everything out of sync. what I did to fix it was went into banshee clicked on music went over toi the right and right clicked "all artists" and removed from library. Next I re-imported my music as normal. Works good now!

---

