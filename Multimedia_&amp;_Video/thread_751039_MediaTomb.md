---
title: "MediaTomb"
date: 2008-04-10
forum: Multimedia &amp; Video
---

### Post by MrWES on 2008-04-10
I have mediatomb running perfectly -- as a daemon too. However, when I reboot the database is not save and I don't see any titles from my PS3. I have my files on a 500g My Book external USB drive. Is there some sort of permission setting I'm missing here?

Thanks,
Bill

---

### Post by MrWES on 2008-04-11
Ok...when I run mediatomb as user Bill it loads the config file from /home/bill/.mediatomb, but when I run as a daemon the log says it's loading the config file from /etc/mediatomb. So how to I either edit the config file in /etc to use the db in my home directory, or edit the init file to use the config file in my home dir.

Anyone?

---

### Post by aeiah on 2008-04-11
you should be able to create a symbolic link from your /etc/mediatomb to your home folder, or you could just copy it across of course (with sudo, since /etc/ is owned by admin).

to create symlinks:
```
sudo ln -s /path/to/real/file /path/to/non-existant/file
```

---

### Post by MrWES on 2008-04-11
I have the daemon pointing to the config.xml file in ~/.mediatomb but now I'm getting the following error:

2008-04-11 13:00:43    INFO: Loading configuration from: /home/bill/.mediatomb/config.xml
2008-04-11 13:00:43    INFO: Checking configuration...
2008-04-11 13:00:43    INFO: Setting filesystem import charset to ANSI_X3.4-1968
2008-04-11 13:00:43    INFO: Setting metadata import charset to ANSI_X3.4-1968
2008-04-11 13:00:43    INFO: Setting playlist charset to ANSI_X3.4-1968
2008-04-11 13:00:43    INFO: Configuration check succeeded.
2008-04-11 13:00:43   ERROR: Error while accessing sqlite database file (/home/bill/.mediatomb/mediatomb.db): Permission denied

The files is owned by root.

---

