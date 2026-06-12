---
title: "Creative Nomad Jukebox Zen Xtra 40GB Not Recognized"
date: 2007-03-03
forum: Multimedia &amp; Video
---

### Post by legzelda on 2007-03-03
Hello everyone!  I am trying to get my old, clunky Creative Nomad Jukebox Zen Xtra to work in Ubuntu.  I have followed several posts suggesting I install libmtp, Amarok and gnomad2.  I have done all these things, and, unfortunately, still have no luck getting my computer to handle my device.  The good news is that whenever I plug in my MP3 player, a window pops up that thinks it's a digital camera (I guess that's libgphoto or something).  Unfortunately, this always freezes with an error message that says a folder does not exist, and then this window provides no further functionality.  

I am more than willing to provide any and all information that may help my plight.  If anyone has had similar experience, or knows how to get this MP3 player working in Amarok, preferably, or gnomad2, I'm listening.  Thanks!

---

### Post by Dekunuts on 2007-03-04
I used my Creative Zen NX (so that's about the same as yours) for a very long time under Ubuntu with GNOMAD 2. It worked perfectly so I think you should definetly keep trying to get Gnomad2 to work. check [http://ubuntuforums.org/showthread.php?t=199250](http://ubuntuforums.org/showthread.php?t=199250)

---

### Post by legzelda on 2007-03-04
GREAT NEWS!  After a quick search through Google, I suppose I discovered my problem.  Using the steps provided [**here**]("http://www.linuxquestions.org/questions/showthread.php?p=2624632#post2624632") , which basically forced me to start, once again, from scratch, I have successfully loaded my Nomad Jukebox Zen Xtra through Gnomad 2.  I think the solution came from typing 
```
ldd `which gnomad2` | grep -i libmtp
```
after installing Gnomad 2.

I am glad this battle is finally--FINALLY--over in Ubuntu.  I have fought this problem for weeks.  Now, I have to move on to getting my PocketPC and Bluetooth to work.  ;) After that, I will be "free" from Windows (still using a PocketPC, though).  Yay!

---

