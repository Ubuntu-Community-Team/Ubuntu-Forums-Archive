---
title: "rhythmbox 0.12.5 on ubuntu 9.10"
date: 2010-04-05
forum: Multimedia Software
---

### Post by cupoange on 2010-04-05
having a problem with rhythmbox:

i have mt-daapd installed on my karmic server at home.  everything works fine in that regard.  when i try to access the share from my laptop running karmic (home, office, anywhere), it retrieves all the songs fine but seems to 'stick', meaning it will continue to say 'retrieving songs from share' in the bottom then eventually freeze.  i can play a song but once it freezes (window goes dark) it'll keep playing til the end of the song but i can't interact with rhythmbox anymore.  the only way to end it is to kill the process.

any ideas?

---

### Post by cupoange on 2010-04-05
fyi, i had all this running fine in jaunty...not sure if it was the karmic upgrade that killed it or something else, but it was working at one point just fine.

---

### Post by cupoange on 2010-04-06
seems to be working right now, but nothing changed.  I've had this problem off and on, any suggestions on how to trap the issue and figure out what's causing the freeze?

---

### Post by cupoange on 2010-04-14
bump

happening again....and I can't figure out what's causing it.  I've tried restarting the mt-daapd...

I even tried installing the 10.04 beta and running rhythmbox from there, and it freezes as well.  so i'm not sure if it's a rhythmbox client thing, or the daap server...

any suggestions??

---

### Post by cupoange on 2010-04-26
bump

please help....i've tried upgrading to rhythmbox 0.12.8 and i'm still getting this problem.  tried debugging and i can't really tell what's going on.  when it does work, the status of "retrieving songs from music share" eventually goes away, but when it freezes this stays up the whole time, and in the logs you can see rhythmbox continually updating this status.  it's also trying to insert stuff into a database.  everything works fine if i connect to my share from itunes.

any suggestions on things to try would be much appreciated.

---

### Post by vahnx on 2010-04-27
Does the same hang for me on 9.10 and latest 10.04 release. I'm trying to connect to my iTunes share.

---

### Post by theWrkncacnter on 2010-05-04
Does the same for me in 10.04: Says "retrieving songs from music share" forever. It wouldn't even connect to a password-protected share. Are there any programs that can connect to DAAP shares?

---

### Post by cupoange on 2010-05-04
it seems like if i just leave it, let it freeze, and don't touch it for 10-15 minutes, eventually it will regain control and everything works.  it could be just the size of the share?

---

