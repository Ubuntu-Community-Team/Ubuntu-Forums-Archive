---
title: "Banshee is running  but won't show up."
date: 2012-11-19
forum: Multimedia Software
---

### Post by tomatoe on 2012-11-19
Hello!

Last week I added Banshee repo to my repo list and I updated it to 2.6. But then it didn't start at all. I checked if it is running with ps aux | grep banshee and it was there. So it just doesnt show up. I also tried
```
banshee --show
```Still nothing.

Then I ran it in dbg mode and it told me this:

[1 Debug 23:30:33.018] Bus.Session.RequestName ('org.bansheeproject.Banshee') replied with InQueue


However when I run it as root it starts up normally and everything seems to work fine.
I googled about this and people who had similar problems "fixed" it with reboot, but this doesn't work in my case.  I tried removing banshee with sudo apt-get purge, removed all necessary libs, removde banshee repo and reinstalled but it didn't fix my problem.

So anyone have some ideas?

Any help highly appreciated.

---

### Post by tomatoe on 2012-11-20
bump

---

### Post by Cope57 on 2012-11-20
Have you filed a bug report?

---

### Post by tomatoe on 2012-11-20
Um, I guess no. You mean in launchpad?

---

