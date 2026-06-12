---
title: "Update Manager"
date: 2011-04-22
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by ibrrfarr on 2011-04-22
So, I am working with an Acer Aspire One D255 and running Ubuntu 11.04

I click Alt-F2 and it brings up Update Manager and Update Manager -d.  I have been simply clicking the Update Manager.

My question is twofold:  first is this what I need to be doing to get the most current, up-to-date *build* I guess the word is?  Or should I be doing something else?  And why doesn't my computer tell me that new stuff is available like 10.10?

Second, I am averaging 140+ Megabytes per update.  This has been over a period of several weeks now.  My question here is first, is this going to make 11.04 ultimately several gigs heavy and second what is the best way to get rid of all the BS that is being left behind dormant.

I used to have something I think was called Ubuntu Tweak which allowed me to clean up the stuff in a no brainer style; however, all I have is Desktop Janitor.

Thank you for any advice/answers!

---

### Post by MadCow108 on 2011-04-22
if you have the the repository to natty and upgrade regularly you have the most up to date build. 

the stuff downloaded gets cleaned up automatically after a certain amount of time (see APT::Periodic::AutocleanInterval in man apt.conf)
To do it manually:
sudo apt-get clean
to remove all cached packages or
sudo apt-get autoclean
to only remove stuff which got superseeded

do sudo apt-get autoremove to remove packages not needed anymore and aptitude search ~o to check for obsoleted packages not supported anymore.
(you should be able to do all this in the synaptic gui too)

---

### Post by KegHead on 2011-04-22
Hi!

If you want tweak;

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

KegHead

---

### Post by kerry_s on 2011-04-22
when it's released it's best to do a clean install.
don't count on it being usable, grab a copy of daily at least once a week to have a installer ready. i always have a usb installer waiting to go just in case.
[http://cdimage.ubuntu.com/daily-live/current/](http://cdimage.ubuntu.com/daily-live/current/)

i personally don't worry about the cruft as i know i will do a clean install at release, after all this is testing & shouldn't be dependent as a main install.

---

### Post by ibrrfarr on 2011-04-23
Thanx for all the replies!

---

