---
title: "problems with frontend"
date: 2008-11-25
forum: Mythbuntu
---

### Post by whaase on 2008-11-25
I set up my Myth server/frontend on a machine and got everything working the way I wanted. Last night I tried to connect a front end to it using the live cd. I had no problems connecting to the backend/database. I could see all my movies/music, but it would not play anything. When I selected a movie, the screen went black for a second and then went right back to the moveie description. It was also missing all the movie posters and settings for things like weather, web etc.

Anyone have any ideas of where to start troubleshooting it? Or ideas of what it could be?

---

### Post by whaase on 2008-11-25
Oh, I should say its Mythbuntu version 8.10

---

### Post by tgm4883 on 2008-11-25
Movies music and pictures don't get transfered over the network using the mythtv protocol (yet).  You will have to mount them in an NFS share or something.

---

### Post by whaase on 2008-11-25
> **tgm4883 said:**
> Movies music and pictures don't get transfered over the network using the mythtv protocol (yet).  You will have to mount them in an NFS share or something.

Ahhh, I didn't realize that.so once you mount it from a share you will have to add the posters etc for each front end?

---

### Post by tgm4883 on 2008-11-25
No, what you should do is mount both the videos directory and the posters directory, then you will have all you need.

Make sure you mount them in the same path.  ie, if your videos directory is located at /var/lib/mythtv/videos on your backend, then mount it at /var/lib/mythtv/videos on your frontend

---

