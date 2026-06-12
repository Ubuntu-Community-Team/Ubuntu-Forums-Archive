---
title: "MythTV"
date: 2007-05-27
forum: Multimedia &amp; Video
---

### Post by playswithdogs on 2007-05-27
Last night mythtv just stopped working
Every time i launch mythtv front or backend i get Myth could not connect to the database then 5 options


HostName
DataBase
User
Password
DataBase Type:


Anyone who whats causing this

---

### Post by barney_1 on 2007-05-28
Are you sure the backend is running?  Try:
```
sudo /etc/init.d/mythtv-backend start
```

Has the IP address of your backend machine changed?  Is your network funtioning properly other than the mythtv problem?

---

