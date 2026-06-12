---
title: "vnstat  ?"
date: 2010-01-29
forum: Networking &amp; Wireless
---

### Post by Tourdog on 2010-01-29
Doing some reading on this excellent forum:

"vnstat" seems to be just what I have been looking for!   (thanks paddy!)

But, this is what I get:

> tourdog@PJK3:~$ vnstat -u -i wlan0
Error:
Unable to read database "/var/lib/vnstat/wlan0".
Error:
Unable to write database "/var/lib/vnstat/wlan0".
Make sure it's write enabled for this user.
Database not updated.
tourdog@PJK3:~$ 
How do I approve my read/write to this subdirectory and plugin?!
TIA !!!

---

### Post by chewearn on 2010-01-29
For first time creating a database, you need to run the command with sudo.
```
sudo vnstat -u -i wlan0
```

---

### Post by Tourdog on 2010-01-29
thanks chewearn for getting back!

Here is what I get:  

tourdog@PJK3:~$ sudo vnstat -u -i wlan0
tourdog@PJK3:~$ vnstat -u -i wlan0
Error:
Unable to write database "/var/lib/vnstat/wlan0".
Make sure it's write enabled for this user.
Database not updated.
tourdog@PJK3:~$ 

I suspect it was too late and I need to delete the "vnstat -u -i wlan0"?  Then use the sudo vnstat -u -i wlan0?

---

### Post by ajgreeny on 2010-01-29
No, you seem to have already used ```
sudo vnstat -u -i wlan0
```which did not give any output.  No output normally means that there are no errors and all is well, though vnstat usually says a new database has been produced.  The second command you show in your last post is a repeat of the first without sudo, so will again show the errors seen.

Try running ```
vnstat -d
``` and see if any output appears with downloads for the day.  This command normally shows the last months usage tabulated, but as you have only just installed it will only have a small output, of course.  If there is no database available you will be told.

---

### Post by Tourdog on 2010-01-29
ajgreeny,
thanks very much for the reply.  I tried the "vnstat -d" and no output just as you said.  I'll get busy and get some bits & bytes for it to crunch and tabulate.

vnstat is exactly the plugin I have been looking for.   
Thank you again.   :) !

---

