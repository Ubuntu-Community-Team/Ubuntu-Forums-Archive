---
title: "Mythbuntu setup problems"
date: 2010-07-23
forum: Multimedia Software
---

### Post by jsanford on 2010-07-23
I installed the backend on one machine and all works good. Installed just the frontend on a second machine and it will not connect to the database. I tried doing it live from the CD and everything worked. Checked and all settings are the same between live and installed. Any help would be appreciated.

---

### Post by &lt;mike&gt; on 2010-07-25
Hi.
Please post some more information, like:
- what distro are you using (cat /etc/issue)?
- what are the settings for the database for the backend (/etc/mythtv/mysql.txt) and what in your frontend (~/.mythtv/config.xml)?
- do you have mysql remote access enabled on the back end? (I presume you do if using the live CD worked)
- the log files from your front end and back end (both reside in /var/log/mythtv/) for when you tried but failed to connect.
I wonder (idly) whether users running a remote front end need to be added to the mythtv group like users running the front end on the same machine as the back end. I can't see any specific instructions for this on the web, though.

---

