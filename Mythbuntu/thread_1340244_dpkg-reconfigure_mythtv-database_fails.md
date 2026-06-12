---
title: "dpkg-reconfigure mythtv-database fails"
date: 2009-11-28
forum: Mythbuntu
---

### Post by movieman on 2009-11-28
Anyone know what's wrong? I just upgraded to 9.10 and remove the mysql root password because I was tired of a bazillion programs assuming that there isn't one. Now I get:

```
>sudo dpkg-reconfigure mythtv-database
sudo password for xxx:
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database
```

So the reconfigure fails and it suggests I reconfigure.

MythTV otherwise seems to be working, except for the fact that it replaced my symbolic link at /var/lib/mythtv/music with an empty directoy when installing.

---

### Post by tgm4883 on 2009-11-28
> **movieman said:**
> Anyone know what's wrong? I just upgraded to 9.10 and remove the mysql root password because I was tired of a bazillion programs assuming that there isn't one. Now I get:

```
>sudo dpkg-reconfigure mythtv-database
sudo password for xxx:
Failed to create or modify database (incorrect admin username/password?)
Try:
sudo dpkg-reconfigure mythtv-database
```

So the reconfigure fails and it suggests I reconfigure.

MythTV otherwise seems to be working, except for the fact that it replaced my symbolic link at /var/lib/mythtv/music with an empty directoy when installing.

It should be prompting you for the mysql admin password after you run that command. The password should be the same password of the first user when you installed Mythbuntu

---

### Post by movieman on 2009-11-28
Yeah, it always used to ask for the password in 9.04, but now it doesn't seem to bother anymore.

---

### Post by movieman on 2009-11-30
So, anyway, it appears that the 'debian-sys-maint' password in the database was different to the one in /etc/mysql. So fixing that made it work.

Would be good if it could actually tell me that rather than tell me to run the same program again.

---

### Post by lofgren on 2010-07-24
Sorry to resurrect an old thread, but I upgraded from 9.04 to 9.10 yesterday and am experiencing this same error.

I have seen the fix mentioned above (make sure the passwords match) and done that. I have subsequently logged into the database with the debian-sys-maint account using the password in /etc/mysql/debian.cnf

I have also seen mention that running mythfrontend updates the tables as required.. doesn't seem to have done the trick for me.

Is there anywhere else that myth-database could be getting the debian-sys-maint password from?

Any other suggestions?

Thanks,
Lofgren

---

