---
title: "login as mythtv user?"
date: 2010-09-17
forum: Mythbuntu
---

### Post by barbex on 2010-09-17
I am confused. 

I just set up a new system with mythbuntu after having h"handcrafted" my previous system with mythtv 0.21. Back then I had the system log in as the user mythtv and had all the directories running under /home/mythtv.

When I installed Mythbuntu it forced me to make up a new user, because mythtv was already in use. Now I have all my crap under this new user but I would rather log in as mythtv and have that my home directory.

Is that possible? What is the password then?

---

### Post by tgm4883 on 2010-09-17
No, you cannot log in as the mythtv user

---

### Post by LowSky on 2010-09-17
to expand on this: the mythtv user is only created for mythtv use. your normal user account will also have access to the same files and directories as the mythtv user. The main reason for the seperate user name is so that you can easily backup your mythtv seetings and not worry of it corrupting the PC's  normal user accounts, that may or may not have access to mythtv.

---

### Post by barbex on 2010-09-17
But all the configuration files ended up in My home directory, the mythtv directory is almost empty! ?

---

### Post by nickrout on 2010-09-17
> **barbex said:**
> But all the configuration files ended up in My home directory, the mythtv directory is almost empty! ?

The scheme mythbuntu uses is that the frontend runs as the user you set up during install. Full stop. Don't try and change it.

---

### Post by barbex on 2010-09-26
ok, I'll change the paths in the database then. Thanks.

---

