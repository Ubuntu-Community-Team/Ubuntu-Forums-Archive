---
title: "mythtv clean reinstall"
date: 2009-12-19
forum: Mythbuntu
---

### Post by elegant55 on 2009-12-19
It is a frustrating story.
 
First I happened to changed the sql password and I found I can't connect to database any more. So I deleted the mythconverg database and the user mythtv. I then ran mysql -u root -p < mc.sql to regenerate the database and user. 

I then ran backend and frontend setup all over again. But this time when I click watch tv button the screen shows 'please wait' for several seconds and go back to the menu.

I tried to purge the mysql and mythtv packages and reinstall but the installation doesn't show again the initial setup like I installed them the first time.

is there a way to clean up mysql, reinstall mythtv and let it trigger the database setup just like I install them the first time?

---

### Post by nickrout on 2009-12-19
what errors do you see in the logs when you go to watch TV?

---

### Post by elegant55 on 2009-12-20
The error states no permission to write in the video folder I set.
I changed the folder perssion and I can watch TV now.
Thanks.

---

### Post by nickrout on 2009-12-20
Thats why we have logs, I just wish more people would read them :)

---

