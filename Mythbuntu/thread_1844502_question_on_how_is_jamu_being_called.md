---
title: "question on how is jamu being called"
date: 2011-09-15
forum: Mythbuntu
---

### Post by bfg100k on 2011-09-15
Hi all,

I am new to MythTV and have recently completed a Mythbuntu 11.04 install and have managed to set up the storage groups, tv channels and even managed to get the recordings to work. Being a techie, I'm keen to figure out how things work and the wiki has been a big help in that area. However, one thing that I've not managed to find information on is how and where jamu is being triggered. I read from the jamu wiki page that its via cron but I looked through all the cron scripts for root, mythtv and my current user and couldn't find it. It doesn't appear to be a daemon since I can't find it via ps. Can anyone shed some light on this topic please? Also, in on of the wiki pages, I read that jamu is deprecated. is that true?

---

### Post by nickrout on 2011-09-15
have you looked in /etc/cron.*/  ?

---

### Post by ZedThou on 2011-09-15
specifically, /etc/cron.daily/mythvideo

edit: apparently /etc/cron.daily/mythtv-frontend too, don't believe I've ever noticed that until now

---

### Post by tgm4883 on 2011-09-16
I didn't think Jamu was being used anymore in 0.24

---

