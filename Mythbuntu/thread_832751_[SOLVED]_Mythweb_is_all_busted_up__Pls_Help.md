---
title: "[SOLVED] Mythweb is all busted up?  Pls Help"
date: 2008-06-18
forum: Mythbuntu
---

### Post by ShiftyPowers on 2008-06-18
Hey all, does anyone know what is going on with my mythweb? I've attached a screenshot of what happens when I click on "Listings".  Get a bunch of errors that say "divide by zero"

I get a bunch of these errors:

```
Error at /usr/share/mythtv/mythweb/modules/tv/tmpl/default/list_data.php, line 65:
Division by zero
```

I'm running the latest 0.21-fixes version of Mythbuntu

Thanks!
Shifty

---

### Post by Lindsay.Mathieson on 2008-06-18
I think I saw that happen when my ```
/etc/mythtv
``` directory got emptied.

You should have the following in that dir:
```
mysql.txt
mythweb-config.php
mythweb-canned_searches.conf.php
session-settings
```

---

### Post by laga on 2008-06-18
Do you have channels defined in MythTV?

---

### Post by ShiftyPowers on 2008-06-18
> **Lindsay.Mathieson said:**
> I think I saw that happen when my ```
/etc/mythtv
``` directory got emptied.

You should have the following in that dir:
```
mysql.txt
mythweb-config.php
mythweb-canned_searches.conf.php
session-settings
```
Yep, my directory has the following in it:

```
htpc@HTPC:/etc/mythtv$ ls -l
total 24
-rw-rw---- 1 mythtv mythtv   1127 2008-06-14 12:59 mysql.txt
-rw-r--r-- 1 root   root     1989 2008-06-10 16:49 mythweb-canned_searches.conf.php.dpkg-dist
-rwxrwxrwx 1 root   root        0 2008-06-14 13:01 mythweb-config.php
-rw-r--r-- 1 root   root     4730 2008-06-10 16:49 mythweb-config.php.dpkg-dist
-rw-r----- 1 mythtv www-data   45 2008-06-14 12:59 mythweb-digest
-rw-r--r-- 1 root   root     1190 2008-04-14 11:35 session-settings

```

---

### Post by ShiftyPowers on 2008-06-18
> **laga said:**
> Do you have channels defined in MythTV?

Laga, I am able to watch LiveTV and have the channels working if that is what you mean.  Not sure if that is what you meant by defined

---

### Post by Lindsay.Mathieson on 2008-06-18
Shifty, your mythweb-config.php is zero length, that will be the cause of your problem.

I'd suggest copying the mythweb-config.php.dpkg-dist over it, but you'll have to edit the contents to match your settings (dbserver, mysql password etc).

---

### Post by ShiftyPowers on 2008-06-18
Lindsay, thank for the reply.  I did indeed create a zero lenght mythweb-config.php in /etc/mythtv in order to solve another problem.  I don't have mythweb-config.php.dpkg-dist anywhere in my system.  Where is it usually located?

---

### Post by Lindsay.Mathieson on 2008-06-18
From the directory list you posted earlier, in /etc/mythtv :)

It is odd you got this, how did you install mythbuntu - was it on top of kubuntu via mythbuntu-control-center?

---

### Post by ShiftyPowers on 2008-06-18
well crap....i deleted that file last time because i was trying to reinstall mythweb.  i deleted it and hten reinstalled mythweb through the MCC but the file did not show up again.

---

### Post by Lindsay.Mathieson on 2008-06-18
Bummer. 

If you haven't already done so I suggest actually uninstalling mythweb via mcc, going into /etc/mythtv and manually deleting any mythweb related file.

Also check /var/www/mythweb is gone - delete if its not.

Then reinstall mythweb via mcc.

Useful related tip - use 'locate' to find files, its *really* quick. However you need to establish a search db first.

# get root prompt
sudo -i

# launch updatedb
nohup updatedb&

# exit
exit

Takes a while to run, but then you can do things like:

locate mythweb-config.php

---

### Post by ShiftyPowers on 2008-06-18
that's exactly what I did :)  I actually had already done your process exactly.  But upon reinstalling mythweb thru the MCC the file does not show up again.  hmm....

---

### Post by ShiftyPowers on 2008-06-18
Bizarre, got it to work now...what i had to do was delete the cached dpkg archives and any refrence to mythweb anywhere in the system. Reinstalled via MCC and now it works fine, no more erros and the mythweb-config.php is properly located in the directory and already filled out.

Thanks for your help Lindsay.

---

### Post by Lindsay.Mathieson on 2008-06-18
There's actually no sensitive info in it so I've attached mine, hope this helps.

Edit : Cross-post and you've solved your problem - excellent! deleted my attachment :)

Cheers

---

