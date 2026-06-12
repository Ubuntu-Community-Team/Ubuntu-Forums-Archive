---
title: "mythbackend shutting down during frontend setup"
date: 2009-04-02
forum: Mythbuntu
---

### Post by mathog on 2009-04-02
Sometimes in mythfrontend this happens:

```
select utilities/setup
select setup
select one of the options
take more than one minute
system shuts down

```

The mythtv-setup shutdown/wakeup options are:

```
startup command: blank)
[x] Block shutdown before client connected
Idle shutdown timeout (secs): 60
Max. wait for recording (min): 5
Startup before rec. (secs): 180
Wakeup time format: time_t
Command to set Wakeup Time:  /usr/local/bin/MythWakeSet $time
Server halt command:  /usr/local/bin/MythPowerOff
Pre Shutdown check-command:  mythshutdown --check

```
mythwelcome itself doesn't do anything except start the frontend, all the other commands are set to /bin/true.  This is MythPowerOff
```

#!/bin/bash
MYTIME=`date '+%s'`
logger "MythPowerOff called at $MYTIME"
poweroff
```

It looks like some of the setup options do not show up as "busy" for "mythshutdown --check" and it shuts down.  In theory this should return 255, but maybe that is for setting up the backend and not the front end?  The mythtv version is 
  
  0.21.0+fixes20277-openglvdpau-0ubuntu3

Anybody else seen this?

---

### Post by mathog on 2009-04-04
Last night it shut down while it was playing a NUV file.  VERY annoying.

```
top menu
media library
watch recording
select recording
watch it

```

A minute or maybe two later, system shut down. The logs showed it was a shutdown initiated by mythbackend. 

So far it has not shut down while watching TV or recording.

---

### Post by mathog on 2009-04-05
I think I see what the problem is.   Both of these

mythshutdown -c 1 
mythshutdown -s 1

return 0 when the frontend is running, whether or not TV is being watched, recordings are being watched, or whatever.  It does return 
8 for recording, etc. but just using the frontend does not, apparently qualify as a condition precluding shutdown.  So I put this in
/usr/local/bin/MythCheckShutdown

```
#!/bin/bash
#
#  safer check for mythbackend initiated system shutdown.  
#  This may be used in the "Pre Shutdown check-command" in mythtv-setup
#  "general", under "Shutdown/Wakeup Options"
#
#    Returns 0 if shutdown is allowed
#    Returns 1 if shutdown is not allowed
#
#  mythshutdown status must be 0, anything else means the backend is
#  busy.
#
mythshutdown --check
MYTHSTATUS=$?
if [ $MYTHSTATUS -eq 0  ]
then
#
#  the frontend must also have exited, or not started in the first place
#  If that is the case the next.
#
  FRONTSTATUS=`ps -ef | grep mythfrontend.real | grep /usr/bin | wc -l`
  if [ $FRONTSTATUS -ne 0 ]
  then
    MYTHSTATUS=1
  fi
else
  MYTHSTATUS=1
fi
exit $MYTHSTATUS

```

And changed

```
Pre Shutdown check-command:  mythshutdown --check
```

to
```

Pre Shutdown check-command:  MythCheckShutdown
```

So far it has blocked further unwanted shutdowns.

---

