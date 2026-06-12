---
title: "mythtv-setup won't store my settings"
date: 2007-06-15
forum: Multimedia &amp; Video
---

### Post by Seantiago on 2007-06-15
Here's a weird mythtv installation issue:

After religiously following the how-to at this site:

[https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop](https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend_Desktop)

I seem to have run into a bit of a snag at the mythtv-setup step. I choose to run mythtv-setup from System > Administration > MythTV Backend Setup, add myself (gray@graytivo) as a mythtv user, log out and then back in, and start mythtv-setup again. It lets me into the setup screen no problem, but whenever I make changes (adding a tuner, storing the channel listings, etc.), it doesn't save them. This is totally lame! What am I doing wrong here?

---

### Post by newlinux on 2007-06-15
I've seen this happen with database corruption. What do your backend logs state?

tail /var/log/mythtv/mythbackend.log

Try running mythtv-setup from the terminal and see what it outputs in the terminal. If it is database corruption (which I may be able to tell from these outputs) and this is a new install try:

```

sudo apt-get remove --purge mythtv-database mysql-server-5.0
sudo apt-get install mysql-server-5.0 mythtv-database

```

to reinsall the database.

---

### Post by Seantiago on 2007-06-15
That fixed it perfectly. Thank you.

---

