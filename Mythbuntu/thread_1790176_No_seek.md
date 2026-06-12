---
title: "No seek"
date: 2011-06-24
forum: Mythbuntu
---

### Post by Colonelguf on 2011-06-24
Today the power went out for a minute. When I restarted, I couldn't seek on some channels, or in recordings. I get this in the terminal:

```

Error preparing query: SELECT mark, offset FROM recordedseek WHERE chanid = :CHANID AND starttime = :STARTTIME AND type = :TYPE ;
Driver error was [2/144]:
QMYSWL3: Unable to prepare statement
Database error was:
Table './mythconverg/recordseek' is marked as crashed and last (automatic?) repair failed

```

Anybody know what I should do?
thanks for the help

---

### Post by nickrout on 2011-06-24
try running ```
sudo /etc/cron.weekly/mythtv-database
``` which will try to repair the database. If that doesn't fix it report back, there is another route to repair the recordedseek table, but I need to look it up.

---

### Post by klc5555 on 2011-06-24
Running mysqlcheck from a prompt along the lines of

mysqlcheck --databases mythconverg --auto-repair

ought to take care of it.

---

### Post by nickrout on 2011-06-25
only if the table is capable of repair, otherwise you basically have to drop the table and recreate it.

read the whole thread:

[http://www.gossamer-threads.com/lists/mythtv/users/441453#441453](http://www.gossamer-threads.com/lists/mythtv/users/441453#441453)

---

### Post by Colonelguf on 2011-06-25
> **nickrout said:**
> try running ```
sudo /etc/cron.weekly/mythtv-database
``` which will try to repair the database. If that doesn't fix it report back, there is another route to repair the recordedseek table, but I need to look it up.

Ran that command and got

```

mythconverg.recorded
warning  : Found 30904 deleted space in delete link chain. Should be 31448
error    : Found 176 deleted rows in delete link chain. Should be 177
error    : record delete-link-chain corrupted
error    : Corrupt
mythconverg.recordedseek
warning  : Table is marked as crashed and last repair failed
warning  : 1 client is using or hasn't closed the table properly
warning  : Size of indexfile is: 137113600      Should be: 1024
error    : Record-count is not ok; is 4463744   Should be: 0
warning  : Found 6514700 deleted space.   Should be 0
warning  : Found 260588 deleted blocks       Should be: 0
warning  : Found 4724332 key parts. Should be: 0
error    : Corrupt

ERROR: DBBackupDirectory not specified, stopped at /usr/share/mythtv/mythconverg_backup.pl line 855.

```I'm trying to digest the info in the other thread you referred to, will report back. I have daily backups of my database.
Thanks for the help.

---

### Post by Colonelguf on 2011-06-27
> **nickrout said:**
> only if the table is capable of repair, otherwise you basically have to drop the table and recreate it.

read the whole thread:

[http://www.gossamer-threads.com/lists/mythtv/users/441453#441453](http://www.gossamer-threads.com/lists/mythtv/users/441453#441453)

I ran the command in the linked thread 
```
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]for I in *.mpg *.nuv ; do mythcommflag --rebuild --file $I ; done[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]
and when it finished about 9 hours later everything worked great again. 
Thanks again for the help.
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

---

### Post by klc5555 on 2011-06-27
> **Colonelguf said:**
> I ran the command in the linked thread 
```
[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]for I in *.mpg *.nuv ; do mythcommflag --rebuild --file $I ; done[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]
```[FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black][FONT=Verdana,Arial,Helvetica][SIZE=2][COLOR=black]
and when it finished about 9 hours later everything worked great again. 
Thanks again for the help.
[/COLOR][/SIZE][/FONT][/COLOR][/SIZE][/FONT]

9 hours? Yikes.

Next time you may want to try mysqlcheck first. If the table is repairable (as it usually is with this common problem) it should save you about 8 hours and 56 minutes.

---

### Post by nickrout on 2011-06-27
If you read this thread the suggestion WAS to try and repair first. And it was not repairable!

---

### Post by klc5555 on 2011-06-27
> **nickrout said:**
> If you read this thread the suggestion WAS to try and repair first. And it was not repairable!

I read the thread. You recommended a manual run of /etc/cron.weekly/mythtv-database. Unless the behavior of the script has been rewritten in 0.24, it attempts to back up mythconverg (if uncorrupted) and checks mythconverg with mysqlcheck. But it doesn't invoke mysqlcheck with an explicit  repair option. So by just running /etc/cron.weekly/mythtv-database, no actual repair was attempted. (Unless this behavior has been specifically altered in the current version, in which case I stand corrected.) That's why I recommended and still recommend explicitly running mysqlcheck --databases mythconverg --auto-repair  from a prompt. Total time invested about four minutes.

If that doesn't work, then there's always time to spend 9 hours and mythcommflag the entire database.

---

### Post by nickrout on 2011-06-27
> **klc5555 said:**
> I read the thread. You recommended a manual run of /etc/cron.weekly/mythtv-database. Unless the behavior of the script has been rewritten in 0.24, it attempts to back up mythconverg (if uncorrupted) and checks mythconverg with mysqlcheck. But it doesn't invoke mysqlcheck with an explicit  repair option. So by just running /etc/cron.weekly/mythtv-database, no actual repair was attempted. (Unless this behavior has been specifically altered in the current version, in which case I stand corrected.) That's why I recommended and still recommend explicitly running mysqlcheck --databases mythconverg --auto-repair  from a prompt. Total time invested about four minutes.

If that doesn't work, then there's always time to spend 9 hours and mythcommflag the entire database.

No I think I stand corrected, I thought the cron script DID try and repair, but I am wrong. Sorry bout that.

We'll never know in this case whether the repair option would have worked. I know when I did it (and started the thread I have pointed to) that the repair option in mythweb didn't work. Whether I tried it from the commandline with mysqlcheck I cannot recall.

---

### Post by klc5555 on 2011-06-28
No problem. :)

I do know, however, that on the (unfortunately frequent) occasions when I have collapsed the seektable (or other tables) the mythweb repair option has failed every time, while the database has always been subsequently fixable from the command prompt. So I suspect that mythweb also invokes mysqlcheck either at its default or at best with an "optimize" parameter.

Cheers!

---

### Post by Colonelguf on 2011-06-28
> **klc5555 said:**
> 9 hours? Yikes.

Next time you may want to try mysqlcheck first. If the table is repairable (as it usually is with this common problem) it should save you about 8 hours and 56 minutes.

Yes, I did try the mysqlcheck that you recommended but it didn't work. I might not have been doing it right, I kept getting an error, something like permission denied, even with sudo. I also tried the repair table link in Mythweb.

Anyway, it's fixed, and I really appreciate the help.

---

