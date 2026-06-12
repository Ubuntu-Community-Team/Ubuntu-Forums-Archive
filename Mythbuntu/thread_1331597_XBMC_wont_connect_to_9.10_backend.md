---
title: "XBMC wont connect to 9.10 backend"
date: 2009-11-19
forum: Mythbuntu
---

### Post by robritz on 2009-11-19
When I set up the video source in xbmc and select View Recordings (or anything else), the XBMC progress spinner spins and spins. I have to restart the xbox when this happens. I can't say it's freezing, but I can't cancel out and it never connects.

I have tried the following:

&#8226; Using the generic mythtv mysql user in myth://
&#8226; Using the root mysql user in myth://
&#8226; Using the system user/password in myth://
&#8226; Removing security on mysql allowed IP's on the backend
&#8226; Running the xbmc mythtv python script (which someone stated wouldn't work with 0.2*, and it doesn't)

My backend IP is NOT configured to 127.0.0.1. I have not meticulously searched every config panel on the backend to see if I'm missing something either, although I have looked them all over (and likely went into a glazed state, given the number of panels to look over).

I don't know exactly what version of xbmc I'm running, but I believe it's the most recent stable build. I have not tried to replace my current version with the most recent stable build just in case, but mythtv support seems to be standard via the myth:// connection string (all of the menu options are visible after being added), implying that it should work ("should").

I'm considering switching to xebian and myth frontend on the xbox's. However, I have 4 xbox's in the house to get working, so if I'm missing something simple I don't want to shoot myself in the foot.

---

### Post by nunrgguy on 2009-11-19
check if old passwords = yes in mysql, if wont you won't be able to connect an xbox, all of that malarky gets reset in the upgrade. I've got the same issue except I can't change it so...

Does the xbox have enough juice to run xebian and a f/e. TBH though I prefer xbmc for media.

---

### Post by robritz on 2009-11-19
> **nunrgguy said:**
> check if old passwords = yes in mysql, if wont you won't be able to connect an xbox, all of that malarky gets reset in the upgrade. I've got the same issue except I can't change it so...

Does the xbox have enough juice to run xebian and a f/e. TBH though I prefer xbmc for media.

It's a fresh install. Where do I check for this? I'm not exactly sure what you're suggesting I look for.

There's a version of Xebian that'll run on the xbox. I'd rather use xbmc, I prefer it for media as well and it's already installed on all of the 'boxes.

---

### Post by nunrgguy on 2009-11-19
I'm suggesting you check whether old password compatability is set to on on the backend database because you need it to be able to connect xbmc which uses the 4.0 and before password hashes.

Start mysqld with the --old-passwords option
Then assign old format passwords to each account that needs them:

mysql> SET PASSWORD FOR
    -> 'some_user'@'some_host' = OLD_PASSWORD('newpwd');



To identify which ones are not currently using the old password format
mysql> SELECT Host, User, Password FROM mysql.user
    -> WHERE LENGTH(Password) > 16;


But if you have the same issues I do it won't work

---

### Post by blackoper on 2009-11-19
Has xbmc been updated to support .22? I havn't tried it personally guess I'll give it a go tonight and see. That would be my first guess is it is still trying to connect with the .21 database scheme

---

### Post by nunrgguy on 2009-12-05
Thought I'd update with the xbmc state of play. If you have the latest builds, on linux you can access recordings, guide and live tv. On xbox and windows you can play recordings but at present can't play live tv or access from guides.

---

