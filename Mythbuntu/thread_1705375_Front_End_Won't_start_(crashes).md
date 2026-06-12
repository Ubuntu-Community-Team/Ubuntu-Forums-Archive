---
title: "Front End Won't start (crashes)"
date: 2011-03-12
forum: Mythbuntu
---

### Post by MusicMonkey5555 on 2011-03-12
I had an issue where the computer running mythbuntu on it froze so I force shut down waited a long while (for the hard drive to stop spinning) and then started it back up again. Now my frontend won't start. I tried grabbing a long using the log tool but not sure exactly where it shows up cause the url is down now.

I then tried the command:
```
mythfrontend -v all 2>&1 /tmp/mythfrontend.log
```

It seems to start up stay for a long while. I then click in the console and it closes the frontend. Most of the time not outputting the log like it should, but their is a bunch of text in the console. I finally got it to output a file and it is attached (had to zip it cause it is big).

I am hoping someone can help me figure this out. My first guess is a corrupted db, but not sure and I tried the repair command:
```
mysqlcheck -r umythtv -u root -p mythconverge
```
and it said that umythtv is not found or something like that.

Anyway any help is greatly appreciated!

---

### Post by kja999 on 2011-03-12
Hi,

It also looks like a db error to me too.

If you run mysqlcheck without the -r does it show any tables with issues?

---

### Post by MusicMonkey5555 on 2011-03-12
Yeah I get a bunch of:
error: incorrect file format '____'
error: corrupt

this is for a bunch of them like: 'recordedrating', recordedprogram', 'recordedmarkup', 'recordedfile', 'recordedcredits', 'record_tmp', 'record','program...

This is no good, hope I can at least recover some of it or something. The issue was I couldn't even see the screen it was so frozen. It was just all black.

PS: I can run the output to a file if you want, but I think you get the idea (have enough info).

---

### Post by newlinux on 2011-03-12
In case you hadn't figured this out yet, the syntax of your mysql command above is wrong. You want:

```

mysqlcheck -r -umythtv -p mythconverg

```
then enter your mythtv mysql password that you enter in the mythtv setup screens and should be in ~/.mythtv/mysql.txt

---

### Post by MusicMonkey5555 on 2011-03-12
I get essentially the same output. Thanks for that though. I just didn't know my password so I figured I would try root cause I knew the password to that.

Am I hosed? I think Mythtv autopacks up the db how would I go about restoring a backup or fixing the errors?

---

### Post by nickrout on 2011-03-12
[http://www.mythtv.org/wiki/Database_Backup_and_Restore](http://www.mythtv.org/wiki/Database_Backup_and_Restore)

---

### Post by MusicMonkey5555 on 2011-03-12
Ok so restored from an old backup and everything works now.  Thanks for all the great help. Just a couple more general questions that are related:
How often does it backup and where do I set that (keep in mind I am using the defaults)?
What should I do next time I have a completely black screen when I turn on my tv?

I am sure it was frozen and this has happened before, but never had an issue where the database got corrupted after hard rebooting. My guess is that it was recording a show or doing something with a recording that just happened (writing to the database) and then that is when it happened. Just want general suggestions for this issue or what to do when it happens again (if there is anything beyond what I did that I can do).

---

### Post by newlinux on 2011-03-12
```

mythconverg_backup.pl --help --help | more

```

---

### Post by nickrout on 2011-03-13
> **MusicMonkey5555 said:**
> Ok so restored from an old backup and everything works now.  Thanks for all the great help. Just a couple more general questions that are related:
How often does it backup and where do I set that (keep in mind I am using the defaults)?

By default mythbuntu runs the backup script from /etc/cron.weekly, therefore it runs once a week.

I moved the script to /etc/cron.daily and made it keep 21 (3 weeks) of backups by creating a backuprc file - I am not at home right now so I can't tell you exactly where that file is or what it contains - will try and remember to post that tonight.

> What should I do next time I have a completely black screen when I turn on my tv?


click a key (one that does nothing like <control> a few times.

If that doesn't work, try to ssh in from another computer and run ```
sudo service gdm restart
``` or if that doesn't bring the screen back to life try ```
sudo reboot
```

> I am sure it was frozen and this has happened before, but never had an issue where the database got corrupted after hard rebooting. My guess is that it was recording a show or doing something with a recording that just happened (writing to the database) and then that is when it happened. Just want general suggestions for this issue or what to do when it happens again (if there is anything beyond what I did that I can do).

---

### Post by MusicMonkey5555 on 2011-03-13
Thanks a ton!
You guys have been great help and love the black screen answers you just gave nickrout.

---

