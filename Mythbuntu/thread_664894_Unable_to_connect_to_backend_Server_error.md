---
title: "Unable to connect to backend Server error"
date: 2008-01-11
forum: Mythbuntu
---

### Post by John Lentz on 2008-01-11
Hi,

I've been trying for days to get the mythtv to work, but I keep getting the unable to connect error when I leave the frontend, or do some channel operations.  I am very much a linux noobie and it took me a lot of effort to get the users, samba, etc setup, so I'd prefer not to reinstall everything.  Could someone please tell me how to initialize the mysql db to back where it was when it was installed.  I've been trying different things from different posts, so it may very well be in a weird state.  Once it is initialized, is there a set of steps to do to set it up and get it working.  I don't know how many times I've run backend setup and frontend setup, but nothing is working.  I have both the backend and frontend in the same box, but I'd like to configure it to be usable by a remote frontend, because that is the next step once I get this single box ready.  Thank you so much for any help - I am way beyond frustrated.

John

---

### Post by John Lentz on 2008-01-12
Well, I think I finally got it to work.  I don't know for sure the exact steps, since I was doing the monkey pounding on a keyboard approach.  However, in case it might help someone else, here is what I think finally worked.  I used this guide [http://ubuntuforums.org/showthread.php?t=415488](http://ubuntuforums.org/showthread.php?t=415488)

to drop my mythtv database, since it was totally hosed.  I looked at the /etc/mythtv/mysql.txt file to make sure what passwords were expected, then used those following the steps at the url I gave above.  Then after running the backend setup and frontend setups, it started working.  I'm relieved it is finally working, so hopefully that url will help someone else.  I think the key was to drop the database for mythtv and start over.  I'd been trying to change settings, with no luck.

John

---

