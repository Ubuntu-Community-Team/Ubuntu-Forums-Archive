---
title: "Mythbuntu Major Meltdown"
date: 2009-12-12
forum: Mythbuntu
---

### Post by zuixro on 2009-12-12
I think my Mythbuntu 9.10 box may have just suffered a massive meltdown. It's my primary backend/frontend. I have one other backend.

I was watching a recorded show. I had to go run an errand, so I paused it and walked away. When I got back, I hit play, and it jumped out of the show and into the "Watch Recordings" menu. There were no shows there. I checked MythWeb and it showed that there was nothing recorded, or set to be recorded. The files are still there but there's nothing in MythTV.  I exited out of the frontend, restarted it, still nothing. I went and watched some videos and they were fine. I went to check the database in MythWeb, and it timed out. I went to check the database in "MythTV Configuration." When I click the "Optimize Tables" button, it flashes to the terminal, then flashes back to that window. I rebooted. It didn't automatically log in. I logged in manually, and I got an error in the lower right hand side that said:
"Install Problem!

The Configuration defaults for GNOME Power
Manager have not been installed correctly.
Please contact you computer administrator."

When I tried to log in, the screen flashed, went to a  loading screen, then went back to the login prompt. After 1 or 2 tries I got in though. I went back into the Frontend, and there was still nothing recorded. I rebooted again later and now I can't log in at all. It just keeps going back to the login screen with the error.

I have nightly database backups, and I would restore one if I could log in. I've tried logging in to another session, but that hasn't helped.  I don't know what else to do. I really don't want to reinstall, and lose everything I've recorded.

What should I do?

---

### Post by zuixro on 2009-12-12
I've determined that it's not related to GNOME Power Manager. I ssh'ed in and uninstalled, then reinstalled it and I still can't log in. Samba shares are still functional though, so I guess that's how I'll watch my recorded shows till I get this fixed...

---

### Post by indulis on 2009-12-13
are any filesystems at 100%? otherwise you may have a corrupted DB so run a manual check of the mythtv databases, the info on how to do this is on the mythtv wiki- basically using myisamchk
[http://ubuntuforums.org/showthread.php?t=507267](http://ubuntuforums.org/showthread.php?t=507267)
[http://wiki.mythtv.org/wiki/Database_errors](http://wiki.mythtv.org/wiki/Database_errors)
[http://ubuntuforums.org/archive/index.php/t-507267.html](http://ubuntuforums.org/archive/index.php/t-507267.html)

Also, what does the mythtv log say?
[http://www.mythtv.org/wiki/Status_Monitoring_How_To](http://www.mythtv.org/wiki/Status_Monitoring_How_To)

---

### Post by zuixro on 2009-12-13
I kept getting "target device is full" errors, but there were 9 gigs free. I ran fsck and it said that it fixed some stuff. I rebooted. I still can't log in.. The screen flashes and changes resolution, goes to the Mythbuntu loading screen, then jumps back to the Login screen.

I've restored the database from the backup two nights ago (Dec 12). MythWeb is giving me errors (yeah I should have waited to restore the backup, I know)

I'm gonna run SpinRite on it (it's the only thing I can think of to do).

---

### Post by zuixro on 2009-12-13
When I try to run the mythconverg_restore.pl script, I get an error, something about Database does not exist (or something like that). I duplicated, then gunzip'ed the the backup that I wanted, then dropped the old database, ran mc.sql to make the new database then ran "mysql -u root -p mythconverg < [backupfile].sql". It sits there for a minute, then finishes. MythWeb still doesn't work. I can't connect from another frontend.  Of course none of this really matters because I can't log in on the computer. I'm about to the point of reinstalling. It wouldn't really be that bad I guess...

---

### Post by zuixro on 2009-12-13
Ok, I've gotten everything fixed.... Except now the sound doesn't work.  I've checked the speakers and they are fine, they're plugged in to the right port.  Something weird has happened to my desktop too, which I think is what caused the sound to go.  Take a look at the screen shot and you'll see what I mean:
[IMG]http://img.photobucket.com/albums/v322/zuixro/Screenshot2009-12-13at70823PM.png[/IMG]
I think it's in some kind of Xfce safe mode or something... I don't know.

Right now I'm thinking reinstall Xfce, but I don't want to screw anything up. Suggestions?

---

