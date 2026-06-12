---
title: "Mythshutdown problem after upgrading to 10.04"
date: 2010-05-15
forum: Mythbuntu
---

### Post by ozsliver on 2010-05-15
Hi.

I upgraded today from Mythbuntu 9.10 to 10.04.

It went quite smoothly, but I now have a problem with mythshutdown.

I originally configured ACPI wakeup following instructions here:

[http://ubuntuforums.org/showthread.php?t=1176528](http://ubuntuforums.org/showthread.php?t=1176528)

It was working beautifully in 9.10.

After the upgrade, mythwelcome is now cycling on the shutdown counter when idle (i.e. the counter goes to zero and starts again).

I had a look at the myth backend log and that's what I found:

2010-05-15 19:48:15.225 I'm idle now... shutdown will occur in 120 seconds.
2010-05-15 19:50:14.414 MainServer::ANN Monitor
2010-05-15 19:50:14.450 adding: cezanne as a client (events: 0)
2010-05-15 19:50:14.499 MainServer::ANN Monitor
2010-05-15 19:50:14.510 adding: cezanne as a client (events: 1)
2010-05-15 19:50:14.550 CheckShutdownServer returned - OK to shutdown
2010-05-15 19:50:14.558 Running the command to set the next scheduled wakeup time :-
                        [COLOR=RoyalBlue]sudo -H mythshutdown --setwakeup "2010-05-15 20:26:40"[/COLOR]
................................................................................

[COLOR=Red]No UPnP backends found[/COLOR]

Would you like to configure the database connection now? [no]  
[console is not interactive, using default 'no']
[COLOR=Red]mythshutdown: Could not initialize myth context. Exiting.[/COLOR]
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
2010-05-15 19:50:17.936 SetWakeuptimeCommand failed, shutdown aborted

If I run the sudo -H command in blue above from a terminal, I get the same error.

I've checked all the settings and my sudo visudo file and everything looks in order.
I tried to google a bit but could not find an answer.

Any help would be appreciated! Thanks heaps.

---

### Post by kja999 on 2010-05-15
Only suggestion I can think of it to increase the verbose level and see if it sheds any light:
-v/--verbose debug-level (Use '-v help' for level info)

---

### Post by Neon Dusk on 2010-05-15
Think it's because you're using 'sudo -H' and mythshutdown is unable to find the DB connection info, just 'sudo mythshutdown --setwakeup "2010-05-15 20:26:40"' should work.

However there's no need for the sudo at all on 'mythshutdown --setwakeup'. See settings in the Mythwelcome section of the [ACPI Wiki](http://www.mythtv.org/wiki/ACPI_Wakeup)

---

### Post by ozsliver on 2010-05-15
Thanks for your suggestions. I'll change the settings to the ones in the Wiki tonight and will report back.

---

### Post by ozsliver on 2010-05-16
Using the settings in the Wiki works, thanks again!

---

