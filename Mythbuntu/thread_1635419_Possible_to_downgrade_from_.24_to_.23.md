---
title: "Possible to downgrade from .24 to .23?"
date: 2010-12-01
forum: Mythbuntu
---

### Post by webbles1 on 2010-12-01
I'm wondering if it is possible to downgrade from .24 to .23 and if so, what I need to do?  Can I just switch the autobuilds from .24 to .23?

---

### Post by thatguruguy on 2010-12-01
Is there a particular issue you're trying to address, or are you just doing it for giggles?

---

### Post by azmyth on 2010-12-01
The database scheme is probably different so you'd have to swap out your 0.24 db for a backup of your 0.23 db. I believe mythtv still makes backups of db on scheme changes either that or it makes weekly backups. You can look in your /var/backup directory.

I agree post your problem and see if someone can help you.

---

### Post by webbles1 on 2010-12-01
I've posted one of my problems at [http://ubuntuforums.org/showthread.php?t=1634020](http://ubuntuforums.org/showthread.php?t=1634020) (Unable to change channels on Live TV).  I'm also seeing problems where MythFrontend crashes when watching recordings, old recordings unable to play in .24 (but did play in .23), lirc stops working after a while, and sound not playing correctly at random times.

So, for me .24 is pretty much broken.

---

### Post by thatguruguy on 2010-12-01
A lot of your problems may stem from the sound issue.  You may want to refer back to the thread you mentioned in your earlier post or my how-to on the 950Q (available [here]("http://ubuntuforums.org/showthread.php?t=1634328")) to get my instructions on getting myth .24 to work nicely with pulseaudio.

---

### Post by webbles1 on 2010-12-02
I posted a reply on your thread you linked.  It didn't seem to work for me.

---

