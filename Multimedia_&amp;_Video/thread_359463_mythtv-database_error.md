---
title: "mythtv-database error"
date: 2007-02-12
forum: Multimedia &amp; Video
---

### Post by tekno62 on 2007-02-12
Im getting this error using synaptic to install mythtv-database


mythtv-database: subprocess post-installation script returned error exit status 1 


thanks

---

### Post by Titus A Duxass on 2007-02-12
What exactly did you do before this message appeared?

---

### Post by tekno62 on 2007-02-12
was in synaptic and installed mythtv-frontend, mythtv-backend,



was working down the howto 

[https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop)

---

### Post by T3h_Dohtem on 2007-02-16
same problem here :(
bump?

---

### Post by majoridiot on 2007-02-17
try:

```
sudo dpkg --configure -a
sudo apt-get install mythtv-database
```

---

### Post by T3h_Dohtem on 2007-02-17
Did a fresh ubuntu install then installed mysql-server, then mythtv packages. I changed the mythtv linux and mysql user passwords to mythtv, and updated the mysql password in /etc/mythtv/mysql.txt to show the change and no db errors now.

Not that it will work for everyone, but I lucked out, so it's worth a shot to someone I hope.
Good Luck!

---

