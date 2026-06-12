---
title: "Firefox bookmarks and history gone and disabled"
date: 2009-09-03
forum: Networking &amp; Wireless
---

### Post by fishexe on 2009-09-03
I am running Firefox 3.0.13 on Ubuntu 9.04 on a Dell Inspiron 1420.

I got up this morning and fired up Firefox, to find that it had no knowledge of my home page and history, and the bookmarks menu and toolbar were both blank.  It still had my saved passwords, but as I navigated around looking for solutions I noticed it was not creating any new history, and the back button was not even available.  After quitting and checking around I found the following directory contained two files owned by root:

~/.mozilla/firefox/wo032cn1.default

had the files sessionstore.js and places.sqlite-journal owned by root.root.  While in that directory, the command:

chown fish.fish *

(where fish is my user name) followed by restarting Firefox solved the problem.  I believe the problem was caused when a program which was running sudo as root (for configuring system-wide settings) attempted to open its help dialogue in firefox.  Hopefully this is helpful to anyone else who experiences the same problem.

---

### Post by r.osmanov on 2009-09-03
Ah, you solved it. I didn't notice it first time. 
Nevertheless, here is the command I wanted suggest:
```
ls -aohR ~/.mozilla/firefox/ | grep -iP '(key|bookmark|signon).+(json|db|txt)$'
```just to see both availability and permissions of the files.

---

### Post by Dawa Lhamo on 2009-11-18
I'm having this same problem, except I'm still running 8.10 and I can't seem to log on to anything, not even here (the search field of this forum is also problematic).  

I had firefox (3.0.15) running and woke up in the middle of the night to hit refresh (for the wootoff), and nothing happened.  I could change tabs, but neither the refresh button nor alt+f5 would work.  I went back to sleep and then restarted my computer in the morning.  I then realised that I had no history or bookmarks.  Thinking maybe an update would help, I updated my kernel, but that didn't do anything but knock out my wireless (which thankfully I know how to fix).  I thought maybe it's possible my cats may have done some sabotage while I was sleeping.  

Anyway, I ran the command you suggest, r.osmanov, and I got (have patience, I can't cut and paste, as I'm logged in here with my windows computer):

```
-rw------- l dawalhamo  16K 2009-11-18 22:30 key3.db
-rw------- l dawalhamo 5.6K 2009-10-29 18:16 signons3.txt
-rw-r--r-- l dawalhamo    0 2009-11-18 22:06 urlclassifierkey3.txt
-rw------- l dawalhamo  17K 2009-11-12 16:36 bookmarks-2009-11-12.json
-rw------- l dawalhamo  17K 2009-11-13 16:49 bookmarks-2009-11-13.json
-rw------- l dawalhamo  18K 2009-11-14 20:08 bookmarks-2009-11-14.json
-rw------- l dawalhamo  18K 2009-11-16 08:59 bookmarks-2009-11-16.json
-rw------- l dawalhamo  18K 2009-11-17 09:00 bookmarks-2009-11-17.json
-rw------- l dawalhamo    0 2009-11-18 14:31 bookmarks-2009-11-18.json
```

I tried the chown command, even though my sessionstore.js and places.sqlite *seem* to be owned by dawalhamo, to no avail (I'll note that I really don't know what I'm doing).  Any suggestions?

---

### Post by r.osmanov on 2009-11-19
Probably, you should do the following:
```
find ~/.mozilla/firefox/ -name key3.db -exec chmod 0775 {} \;
find ~/.mozilla/firefox/ -name signons3.txt -exec chmod 0775 {} \;
find ~/.mozilla/firefox/ -name urlclassifierkey3.txt -exec chmod 0775 {} \;
```

---

