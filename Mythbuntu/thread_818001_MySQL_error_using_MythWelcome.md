---
title: "MySQL error using MythWelcome"
date: 2008-06-04
forum: Mythbuntu
---

### Post by parvaman on 2008-06-04
I'm hoping someone can give me some pointers. I'm running Mythbuntu 8.04 backend/frontend on same machine with a Nova T-500 DVB-T dual tuner and am trying to set up MythWelcome using APCI, so my machine will wake-up/shut down for scheduled recordings. When I schedule a TV program to record in frontend and then quit frontend, Mythwelcome dutifully shuts down the machine and correctly sets the Wake up time but unfortunately it never wakes up to record. 
When I log back in what I see in my Mythbackendlog is this ...

2008-06-03 14:07:30.029 CheckShutdownServer returned - OK to shutdown
2008-06-03 14:07:30.033 Running the command to set the next scheduled wakeup time :- mythshutdown --setwakeup 2008-06-03T14:46:40
2008-06-03 14:07:30.356 Running the command to shutdown this computer :- sudo mythshutdown --shutdown
2008-06-03 14:07:32.372 DB Error (Looking up chanID):
Query was:
SELECT chanid, useonairguide FROM channel, dtv_multiplex WHERE serviceid        = 15552   AND       networkid        = 9018   AND       transportid      = 12290 AND       channel.mplexid  = dtv_multiplex.mplexid AND channel.sourceid =1
Driver error was [2/2006]:
QMYSQL3: Unable to execute query
Database error was:MySQL server has gone away

It then goes on to display other SQL errors trying to grab TV schedule info.

I've run command "sudo mysqlcheck --auto-repair -A -u mythtv -p" and all databases are marked as OK but the problem just re-occurs. Any pointers anyone? Is this something do to with backend shutting down too soon as it seems I'm losing connectivity to SQL database.

When I schedule a recording without using Mythwelcome it works fine and starts up OK and records. The problem is though that this being a frontend/backend machine, it'll never shut down once recordimg has finished as the frontend remains on. I'd like to get it recording using Mythwelcome so that it shuts down automatically afterwards.
I have been following instructions from this document - [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake)

Many thanks in anticipation of any help

---

### Post by parvaman on 2008-06-09
Having looked at this further, I suspect this issue has nothing to do with MySQL because its probably giving those errors as it shuts down the backend.
To recap, I have combined frontend/backend machine and I have used the latest setup instructions from here - [https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake](https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake) and it shuts down OK, appears to write the wakeup time OK but never wakes up for the recording. Could this be BIOS setting related? I have tried it with both RTC Wakeup as enabled and disabled. When I set this up without MythWelcome it wakes up fine but the document says that RTC works slightly differently when Mtyhwelcome is involved.
I am using an Abit AN-M2HD mobo. Anybody had experience of setting up MythWelcome with this mobo? Its currently on Bios revision 14 so is not the latest one (which is revision 19 but there doesn't seem to be anything in Bios upgrade notes that suggests it would help with an upgrade). Any pointers appreciated or any checks I can do?

---

### Post by tohc1 on 2008-06-09
I had a similiar issue when first setting up mythwelcome. Looking at the log:

2008-06-03 14:07:30.356 Running the command to shutdown this computer :- sudo mythshutdown --shutdown

My guess would be that it's not actually runing the command because it's waiting for a password. You probably need to add the mythshutdown command to the sudoers file so that it runs with needing a password.

---

### Post by parvaman on 2008-06-10
Thanks for reply. My sudoers file currently contains this 
%mythtv ALL = NOPASSWD: /sbin/shutdown, /usr/bin/MythWakeSet, /proc/acpi/alarm, /usr/bin/MythShutdownCheck, /etc/init.d/mythtv-backend, /usr/bin/mythshutdown
... so I think it looks OK. As its shutting down is there anything I can check to see what actual wake up time is written?

---

### Post by parvaman on 2008-06-10
More info ...
What I see in backend log is the time being set correctly i.e.

2008-06-10 16:51:18.099 Running the command to set the next scheduled wakeup time :-	sudo mythshutdown --setwakeup 2008-06-10T17:56:40
2008-06-10 16:51:18.422 Running the command to shutdown this computer :-sudo -H mythshutdown --shutdown

but what MythWakeSet has put in the /proc/acpi/alarm is this ...

2008-06-10 00:00:00

so I can see why its never waking up now as that will always be in the past. So it looks like its setting the date OK, but not the time part of the wake up.
Any more ideas anyone?

Could this be that this motherboard (Abit AN-M2HD) just doesn't support this?

---

### Post by tohc1 on 2008-06-10
Sorry I miss read your post, though it was a problem with not shutting down.

Having looked at the instruction page you link too, I notice in the Modify MythWakeSet section that the new version of mythwelcome has a wakeup time format setting - I'm still using mythbuntu 7.10 so this is new before mythwelcome passed the time as seconds since 1970. 

I would check to see if it's actually passing the time the way you think it is by having a look at the temp_stamp (=/home/mythtv/timestamp) file

The good news is if you can make wakeup work manually its not the motherboard or bios settings.

---

