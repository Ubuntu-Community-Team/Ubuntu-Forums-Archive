---
title: "MythTV cannot connect to database"
date: 2008-05-08
forum: Mythbuntu
---

### Post by joyntkid on 2008-05-08
I installed MythTV for the first time on a new 8.04 install.
I added a MySQL password when it asked, but later saw a tutorial on installation where it said i shouldn't use a password.
Now when i try to configure the backend-setup, it tells me it "Cannot Connect To Database"

I'm guessing its because of the password i put on MySQL, so is there anyway to reset that to nothing or what should i do?

---

### Post by dinger1986 on 2008-05-08
Is that the root password you set?

If it is you should be able to change it by typing in:
sudo dpkg-reconfigure mysql-server

This time when it asks for a password do not set one.

Regards,
Daniel

---

