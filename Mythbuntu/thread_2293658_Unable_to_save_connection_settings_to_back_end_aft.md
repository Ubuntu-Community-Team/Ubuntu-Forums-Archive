---
title: "Unable to save connection settings to back end after reboot"
date: 2015-09-06
forum: Mythbuntu
---

### Post by todd-4 on 2015-09-06
Posting this more as an aid to others in the same situation rather than a question...

Periodically over the last six months, when I reboot my MythTV server it is unable to load the backend, comes up in "Database Configuration" mode - first asking me for country/language, then asking for password.  

Often when that happened, even entering the right password and "finish" did not work - continued to loop through this sequence.  Every once in a while, seemingly at random, it would "save" after perhaps the third or fourth attempt.

This morning, no luck.  Continuous attempts and reboots did not change anything - I could not get past the database configuration screens to get the Myth backend to run.

I was about to post here when I also noticed that automatic software updates were failing...  

Initially I thought "hmmm... some required update did not install, which is leading to my problem - I should fix that first."

In fixing that, I discovered the updates were not occurring because there was not enough space in the /tmp folder.  

Investigating, I found my 50G boot partition only had 800M free.  Yikes!

How could this be?  The machine is divided between boot partition and "everything else" (for data, etc) and it's 90% MythTV (plus a few random handy bits of software I've installed, like Plex....), so how could Ubuntu and Myth be occupying 49.2GB?  That would be..... Windows-like.....

Disc Usage Analyzer - which I had to download, it doesn't come with the Mythbuntu distro - showed me the culprit - almost 20G of files in the trash/expunged folder.

A bit of googling turned up a known issue when using Nautilus to delete folders that it owns, which contain files it does not own....

One of those posts gives instructions on how to run a command to fix that and delete those files.

[http://askubuntu.com/questions/351400/deleting-contents-of-local-share-trash-expunged](http://askubuntu.com/questions/351400/deleting-contents-of-local-share-trash-expunged)

Once I did that, I then was able to load the myth DB just fine....

Would have been nice if some error had said "unable to initialize DB, out of disc space" or something similar, though...

Anyway, if you're having this problem, make sure you have enough free space on the disc...

Todd

---

