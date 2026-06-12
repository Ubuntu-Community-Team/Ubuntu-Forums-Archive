---
title: "Mythbuntu schedule information keeps disappearing"
date: 2007-11-19
forum: Mythbuntu
---

### Post by SgtDude on 2007-11-19
I've installed Mythbuntu three times on my machine.  Every time, I get it up and running perfectly and it runs fine for a day or two.  Then, the computer will crash (usually with a blank purple screen), and after a hard reboot all of my scheduling information is gone.  I've tried running *mythfilldatabase* multiple times, without any error messages, but when I go back into the guide, it's just a bunch of *unknown* blocks.

I'm able to watch everything that's been recorded before the crash, and I dont' get any error messages, but I can't record anything new because my backend doesn't know when anything's on.

Has anyone seen this?  Any ideas?  I'm pretty good with Linux, but I'm not too familiar with MySQL, and my money says this is where the problem lies.

---

### Post by ubnewbie2 on 2007-11-19
Sounds like database problems, yes. I am at work now, and don't have the instructions to hand, but search around...

Also try searching  [http://www.mysettopbox.tv/knoppmyth.html](http://www.mysettopbox.tv/knoppmyth.html).

There are instructions around on how to stop the back-end and mysql, and to run a cleanup job on the tables.

---

### Post by uopjohnson on 2007-11-21
I don't think you are dealing with simple database corruption since it has happened on several clean installs.  You may have a problem with your underlying file system.  Possibly you run out of good blocks for the db after a few days of recording and storing info and then you get errors.  I would check that as well. 
If it is database corruption that has happened several times then I would bet there is another underlying cause.

---

### Post by SgtDude on 2007-11-21
Thanks for the pointers.  I'll be re-installing again over the long weekend, so I'll keep you posted as to my success or failure...

---

### Post by SgtDude on 2007-12-08
Ok, it's been what, two weeks or so now?  My Mythbuntu box is working fine, and hasn't died yet, and I don't think it will.  Woo Hoo!

Anyway the only thing I did differently this time is:

During regular updates, there's a package (I think it has something to do with QT) who's configuration file gets updated.  Ubuntu's update manager asks you if you would like to update the configuration file.  The correct answer to this question is a definitive "NO".  I'm sure I'll eventually install Mythbuntu on annother box, so I'll pay attention next time and post the name of the package with the updated config file.

Thanks for your help everyone.

---

