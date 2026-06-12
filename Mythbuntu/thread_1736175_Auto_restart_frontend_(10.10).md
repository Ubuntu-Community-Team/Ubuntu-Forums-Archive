---
title: "Auto restart frontend (10.10)"
date: 2011-04-22
forum: Mythbuntu
---

### Post by blinnov.com on 2011-04-22
Hi,

I had an install of Mythbuntu 10.04 for quite a while (upgraded from 8.04). One nice thing about it was that if mythfrontend crashed (as it does every now an then), a nice little pop-up would appear saying "frontend crashed unexpectedly, restarting" and frontend is then restarted automagically. 

I did not do anything special to get that behavior in 10.04 and thought that was a nice new cool feature. But I had to install 10.10 (RIP old hdd) and I cold not get it there at all.

I assume that would be a feature of the session manager, but I have no idea how to enable it. Googled, found nothing.

Any ideas?

---

### Post by superm1 on 2011-04-22
First enable autobuilds and grab the most recent build.  I want to say that functionality is only on 0.24 builds.

To use it, you just need to start mythfrontend from the mythbuntu login session or from the menu item in gnome.  Starting from a terminal will not activate this functionality.

---

### Post by LowSky on 2011-04-22
yup its in the autobuilds of .24. you can enable them form mythtv control center

---

### Post by blinnov.com on 2011-04-23
Thank you guys, you saved my day! That worked.

---

