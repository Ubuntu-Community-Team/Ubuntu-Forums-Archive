---
title: "Amarok collection"
date: 2010-05-02
forum: Multimedia Software
---

### Post by mplf on 2010-05-02
Hi

I've just followed the upgrade path from 9.10 to 10.04 and am having an issue with Amarok and my local collection.

I have my local collection indexed in an external MySQL database so it can be shared with all computers on my network, however amarok in 10.04 is not showing the collection at all. It has all the settings configured correctly (database, username, password, host, etc), I've checked the database and its fully populated. I've even tried deleting all of amaroks configuration settings and re-configuring it as a new install but for whatever reason the collection seems to not exist.

The amarok user on my database has all privileges except GRANT, I can connect to the database as the amarok user via the console and read/write as that user so I'm sure that that isn't the issue.

I've tried running amarok from the console with --debug enabled but there is nothing there that seems to indicate a problem

Any help would be greatly appreciated.

---

### Post by karhulitos on 2010-05-04
I have exactly same but with internal DB. No songs in collection no matter what I do..

---

### Post by karhulitos on 2010-05-16
OK, it was me. I tried to remove Amarok and all KDE stuff and reinstalled afterwards and now I have my collection back! Must have been due to some PPA version I had in Karmic. User error.

---

