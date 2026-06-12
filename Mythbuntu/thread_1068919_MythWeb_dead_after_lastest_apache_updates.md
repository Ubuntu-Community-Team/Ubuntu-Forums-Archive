---
title: "MythWeb dead after lastest apache updates"
date: 2009-02-13
forum: Mythbuntu
---

### Post by fatmonk on 2009-02-13
Today Synaptic recommended a couple of important security updates for apache, so I let it apply them.

Now I get a message from MythWeb when I try to browse it, that it cannot connect to the database.

```
Database Access Denied

You are most likely receiving this message because you
have failed to configure mythweb's database login info.

Please see INSTALL for instructions.

```

Looking at the INSTALL file as advised, I can see the file that I need to edit and move to rest the password correctly, but there are quite a few other bits to edit in this file and I don't really want to hack around too much in case I just make the situation worse.

Any ideas?

-FM

---

### Post by buntunub on 2009-02-13
There is another post about this [here]("http://ubuntuforums.org/showthread.php?t=1067968&highlight=mythweb"). There are no answers to this problem right now, and the only real solution offered is to roll back to a previous release of php5, mysql, etc. As at least 75 - 95% of Ubuntu users are unfamiliar with php and/or mysql programming inner dynamics, it looks like we will most likely be at the mercy of those few who can decipher that gobly gook.

---

### Post by fatmonk on 2009-02-13
Actually just figured it out.. will check the other post and see if my fix is relevant to that as well...(edit: the other post appears to be about a different, more serious problem)

All I did was add the database password to the mythweb config file in the apache2 available sites directory:

```
/etc/apache2/sites-available/mythweb.conf
```

That's sorted it, no more database access error!

-FM

---

### Post by buntunub on 2009-02-13
> **fatmonk said:**
> Actually just figured it out.. will check the other post and see if my fix is relevant to that as well...(edit: the other post appears to be about a different, more serious problem)

All I did was add the database password to the mythweb config file in the apache2 available sites directory:

```
/etc/apache2/sites-available/mythweb.conf
```

That's sorted it, no more database access error!

-FM

Ok Ill bite. What and where within that file did you change? I looked within mine and it shows all the correct information on the setenv db_login, and setenv db_password. Is there some other variable that needs to be uncommented or added?

---

### Post by buntunub on 2009-02-14
The real solution to this problem can be found [here]("http://ubuntuforums.org/showthread.php?t=1067968").

---

### Post by fatmonk on 2009-02-15
buntunub,

The thread that you keep referring to is about another, different problem.

The post that you refer to involves a blank screen - to quote the first post in that thread:

"I cant use mythweb anymore.
The page is blank..white.. nothing."

As per my original post in this thread, I get output from MythWeb that tells me that I have a database access error - I DO NOT have a "blank..white" screen.

The solution to my problem was to edit /etc/apache2/sites-available/mythweb.conf as I said in post 3. I edited the db_password environment variable settings (setenv db_password, as you rightly identify). For some reason, the latest php upgrade reset this to 'mythtv' on my system, whereas Mythbuntu changes this from a default to a nice random string.

When I replaced 'mythtv' with my particular random string as found in /home/mythtv/.mythtv/mysql.txt and tried again MythWeb worked perfectly again.

This is the REAL solution to the problem I had.

The REAL problem to the problem you are referring to can obviously be found in the thread that you are referring to.

-FM

---

