---
title: "stopping mythtv backend autostart"
date: 2009-05-31
forum: Mythbuntu
---

### Post by enchesss on 2009-05-31
Is there a safe way to stop the backend from starting up on log in?

Would it be ok to delete the

/etc/init.d/mythtv-backend file?

or is there a setting so that it is easy to start again later?

---

### Post by ahood on 2009-05-31
> **enchesss said:**
> Is there a safe way to stop the backend from starting up on log in?

Would it be ok to delete the

/etc/init.d/mythtv-backend file?

or is there a setting so that it is easy to start again later?

Instead of deleting, you can either move or rename it..

**Moving**
> sudo mv /etc/init.d/mythtv-backend /home/username/mythtv-backend

Replace 'username' with the appropriate folder name is under /home

**Renaming**
> sudo mv /etc/init.d/mythtv-backend /etc/init.d/mythtv-backend.old

I hope this helps; however, I think there is probably a better way...I just don't know what it is at the moment.

---

### Post by ian dobson on 2009-06-01
Hi,

Why not just delete the symbolic link in /etc/rc2.d.

You can still manually start myth backend.

Regards
Ian Dobson

---

### Post by AboveTheLogic on 2009-06-02
sudo apt-get install rcconf

---

### Post by dr_dred5 on 2009-06-06
> **AboveTheLogic said:**
> sudo apt-get install rcconf

Just to clarify the above post.

After installing rcconf, start it in terminal sith ```
sudo rcconf
```
Use the arrow keys to scroll down to Mythbackend and use the space bare to de-select it. Tab and enter to quit.

Restart the backend with. ```
sudo mythbackend
```

---

