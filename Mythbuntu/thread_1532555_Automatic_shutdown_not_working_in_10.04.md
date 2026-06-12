---
title: "Automatic shutdown not working in 10.04?"
date: 2010-07-16
forum: Mythbuntu
---

### Post by JasonEde on 2010-07-16
I've set up the shutdown procedure as per [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

However, when I leave mythwelcome then it doesn't shutdown... The countdown geos to 10 and then back to 300.

This is what I see in the backend log file.

2010-07-16 20:28:45.991 CheckShutdownServer returned - OK to shutdown
2010-07-16 20:28:46.037 Running the command to set the next scheduled wakeup time :-
                                                sudo -H mythshutdown --setwakeup 2010-07-18T17:54:00
................................................................................

No UPnP backends found

Would you like to configure the database connection now? [no]
[console is not interactive, using default 'no']
mythshutdown: Could not initialize myth context. Exiting.
QSqlDatabasePrivate::removeDatabase: connection 'DBManager0' is still in use, all queries will cease to work.
2010-07-16 20:28:49.794 SetWakeuptimeCommand failed, shutdown aborted
2010-07-16 20:28:51.835 I'm idle now... shutdown will occur in 300 seconds.

Suggestions of where to look would be great... I've checked all the config files for typos and found nothing.

Jason

---

### Post by jMon54 on 2010-07-16
I had this problem and solved it by removing "-H" from the shutdown command

---

### Post by Neon Dusk on 2010-07-16
> **JasonEde said:**
> I've set up the shutdown procedure as per [http://www.mythtv.org/wiki/ACPI_Wakeup](http://www.mythtv.org/wiki/ACPI_Wakeup)

...

                                                **sudo -H mythshutdown --setwakeup 2010-07-18T17:54:00**


The wiki has the command 
```

mythshutdown --setwakeup $time

```

where did you get the command
```

sudo -H mythshutdown --setwakeup $time

```
?

---

### Post by JasonEde on 2010-07-17
Ooops. That was me trying stuff when it wasn't working... I've removed the sudo -H now.

---

