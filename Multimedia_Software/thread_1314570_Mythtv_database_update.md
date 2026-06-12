---
title: "Mythtv database update"
date: 2009-11-04
forum: Multimedia Software
---

### Post by mrdek11 on 2009-11-04
I'm trying to use a laptop as a frontend to my mythtv server.
The laptop is running Ubuntu 9.10 and the backend Ubuntu 9.04.
When I run the mythfrontend on the laptop, it connects, and says that the database schema needs to be updated, but says it doesn't have permission. It tells me to run mythtv-setup or mythbackend to update it.

I assumed that the database being updated is the one on my backend server. (Because the frontend doesn't have mythtv-setup or mythbackend)

However, I see nothing about updating when I run either command, and I can't find anything about it online.

Does anybody know how I can fix this?

Thanks in advance,
Derek

---

### Post by andrewc6l on 2009-11-04
I'm not 100% sure, but I have a fair guess: the frontend you're using is MythTV 0.22 and the backend is MythTV 0.21. The two can't be mixed. You might want to upgrade your backend to 0.22, or maybe just boot your laptop with a Mythbuntu 9.04 disk to see if that's really the issue.

---

### Post by mrdek11 on 2009-11-05
Thanks for your help! Myth worked successfully after installing the version from the jaunty repositories.

Part of the problem was caused by my not having a backend running on the frontend machine. I thought that you only need the frontend running to connect to a master backend, but apparently you must have a slave backend running.

Thanks again, I appreciate you pointing me in the right direction!

---

### Post by fenian on 2009-11-05
> **mrdek11 said:**
> Thanks for your help! Myth worked successfully after installing the version from the jaunty repositories.

Part of the problem was caused by my not having a backend running on the frontend machine. I thought that you only need the frontend running to connect to a master backend, but apparently you must have a slave backend running.

Thanks again, I appreciate you pointing me in the right direction!

No the reason you couldn't connect was because mythtv 0.21 is not compatable with mythtv 0.22.The frontend and backend both need to be the same version.There is no need to have a backend on the frontend if you already have a master backend setup elsewhere on the LAN.

---

