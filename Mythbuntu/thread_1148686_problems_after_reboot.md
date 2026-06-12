---
title: "problems after reboot"
date: 2009-05-04
forum: Mythbuntu
---

### Post by kadafi69 on 2009-05-04
I have mythtv working for ages, and just got it set up how I like it. (apart from some minor crashes in the music player).

But today it crashed then wouldnt reload. So I rebooted and im greeted with the mythtv language selection screen. Then it pops up with 

>  No UPnP Backends found.
Ok

After that comes up with the Database configuration screen, all the local host, database name/password stuff. All of which is filled in as it should be. When I select finish it pops up with.

> Cannot login to database?
Ok.

The only option is Ok. After that it loops back to the first database config screen where I have to select Cancel to exit the loop.

I have no idea why this has started happening. 

Although I did svn to the 0.21.1-fixes a couple of weeks ago, but this is the first promblem ive had.#

Any ideas?

---

### Post by kadafi69 on 2009-05-05
bump

---

### Post by Dewey_Oxberger on 2009-05-05
Anything interesting in the logs /var/log/mythtv/

?

---

### Post by SiHa on 2009-05-06
Don't suppose th IP address of the backend machine has changed, and the Master Backend Server in the backend setup is stil pointing to the old adress?
I've had the router suddenly change IP's on me before I switched to static IP addresses for all my machines.

---

