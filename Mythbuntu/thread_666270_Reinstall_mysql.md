---
title: "Reinstall mysql"
date: 2008-01-13
forum: Mythbuntu
---

### Post by lingenfr on 2008-01-13
In the process of running commands to allow xbmcmythtv clients to connect, I think I sudoed where I shouldn't have and now I can't get mysql to start. I have been dealing with this off and on for a few weeks and now I have to solve it. I would like to do it in the least destructive manner possible, but I am about ready to throw in another harddrive and do a fresh install of mythbuntu just to get going again. I tried to reinstall mythtv-database, that failed with the same type of mysql I have been getting. I suppose that the next step is to reinstall (purge) mysql and mythtv-database. Can anyone help me with the process? Should I do anything else to insure that I am not left with file/directory permission problems? Thanks.

Update: I logged in and tried to reinstall all mysql packages using synaptic. No joy. After reinstall when it tried to configure mysql, it failed with the same error I had been getting about unable to connect to mysqld.sock. I looked at the complete removal option, but I did not want to go that far without some feedback.

---

### Post by racmar on 2008-01-18
to uninstall completely:
```
sudo apt-get remove --purge mysql
```
I'm pretty sure your databases will be fine, but I'm not 100% sure.  If you want to be 100% sure, make a backup copy of the following folder:
/var/lib/mysql/mythconverg



then:
```
sudo apt-get install mysql
```

---

### Post by lingenfr on 2008-01-18
Thanks. Unfortunately, mythtv depends on mysql and that would have wiped nearly everything. I grabbed my files off that system, wiped it and installed a fresh mythbuntu. I am nearly back to 100%. With what I know now about phpmyadmin, I might have been able to sort it out. I think I got myself into trouble with sudo and screwing up some folder/file permissions.

---

### Post by racmar on 2008-01-18
well, glad you've go it mostly sorted.  You are right about the dependencies, but you could have just copied what was removed and then reinstalled those packages also.

---

### Post by lingenfr on 2008-01-18
agreed. once i get everything restored, i am going to image the system in case this happens again.

---

### Post by Zack McCool on 2008-01-18
You could have just imagined the system was working, if imagination is what you are after...   ;)

Good luck on the reinstall...

---

