---
title: "FYI, using xine instead of internal dvd player"
date: 2009-08-09
forum: Mythbuntu
---

### Post by mathog on 2009-08-09
I prefer the internal player to xine, but occasionally there are disks it cannot handle.  Here is how I set up my remote control only (no keyboard) system to get around this, additionally, it lets us restart the front end.   The way this works normally is that when the system starts mymythtv.sh starts up mythwelcome.  If the frontend locks up or crashes hit "digitalanalog" on the remote and it kills everything below mymythtv.sh, which then restarts mythwelcome.  To run xine press "sleep" on the remote, and it shuts down all of mythtv (preventing it from turning off the computer as idle) and starts xine.  On exiting xine mythtv is started back up.  Seems to work pretty well so far.  One of the scripts uses my "extract" program (search for drm_tools) to pull out a process ID from a ps -ef line, but it could also be done with cut or even the right bash syntax.  The display :0.1 business is because this system runs on a TV-OUT which is the second display.  Some of this was based on ideas mentioned by "Lost Dog" in the Mythtv VDPAU thread on the nv linux forum.



Starting from my home directory, hare are:

./.lirc/irexec
```
begin
    remote = RM-VL600_8201
    prog = irexec
    button = digitalanalog
    config = /usr/local/bin/mythtv_failsafe.sh
    repeat = 0
    delay = 0
end
begin
    remote = RM-VL600_8201
    prog = irexec
    button = sleep
    config = /usr/local/bin/use_xine.sh
    repeat = 0
    delay = 0
end

```

Also added this to .lircrc

```
include ~/.lirc/irexec
```

In ./.config/autostart/irexec_startup.desktop

```
[Desktop Entry]
Name=irexec startup
Comment=my hack to start irexec
Version=0.0.1
Exec=/usr/bin/irexec -d
Type=Application
Encoding=UTF-8
StartupNotify=false
Terminal=false
Hidden=true
```

In ./.config/autostart/mythtv_startup.desktop
```
[Desktop Entry]
Name=mythtv startup
Comment=my hack to start mythtv on screen 1
Version=0.9.4
Exec=/usr/local/bin/mymythtv.sh
Type=Application
Encoding=UTF-8
Icon=/usr/share/mythtv/themes/blue/myth_tv_logo.png
StartupNotify=false
Terminal=false
Hidden=false
```

In /usr/local/bin/mythtv_failsafe.sh
```
#!/bin/sh
#
# this is run with the "digital/analog" button on the remote.
# It blows up the front end so that mymythtv.sh can restart it.
# Also blows up firefox, in case that got started.
# MATHOG JUL-11-2009
#
killall firefox
killall xine
killall mythfrontend.real
killall mythfrontend
killall mythwelcome

```

In /usr/local/bin/use_xine.sh
```
#!/bin/sh
# play a DVD using xine instead of the built in player
export DISPLAY=:0.1
/etc/init.d/mythtv-backend stop
kill -9 `ps -ef | grep mymythtv.sh | grep david | extract -mt -sc 2 -nc 1`
killall mythwelcome
killall mythfrontend.real
xine -B -G 604x456+18+12 --no-splash dvd:/
#
# start it back up again after xine exits
#
/etc/init.d/mythtv-backend start
/usr/local/bin/mymythtv.sh >/home/david/mm.log 2>&1 </dev/null
```

and finally, in /usr/local/bin/mymythtv.sh

```
#!/bin/sh
#
#  This script sets the display and then starts mythfrontend
#  The while script is to restart mythwelcome if it should crash or exit
#  for some reason.
#
#  if the TV idles at the main screen too long it will blank if the
#  screensaver is on.  No mouse to shake to get it back
#
killall gnome-screensaver
#
#  This works so long as mythfrontend is NOT set to start automatically.
#  It cannot be set that way anyway, because if it is programmed recording
#  will start the frontend, and then the backend cannot shut down the system.
#
export DISPLAY=:0.1
while [ 1 ]; do
  logger "starting mythwelcome at `date`"
  mythwelcome --logfile /var/log/mythtv/mythwelcome.log
  logger "mythwelcome exited at `date`"
done

```

---

### Post by superm1 on 2009-08-10
This seems a bit overzealous to insist upon stopping mythbackend just to watch a DVD doesn't it?

---

### Post by mathog on 2009-08-10
> **superm1 said:**
> This seems a bit overzealous to insist upon stopping mythbackend just to watch a DVD doesn't it?

Once the frontend and mythwelcome are turned off the backend will classify the system as idle if no recording is going on, and trigger a shutdown.  Not compatible with watching a DVD. 

But yes, you are right, it shouldn't be necessary to kill the backend, since that will preclude automatic recording at the same time a DVD is being played.  To avoid that the script which checks to see if it is ok to shutdown must also check to see if xine is running.  The supplied mythshutdown doesn't do this right, but I already had a wrapper around that, and it is easy enough to add another exception for xine.

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
#  busy.(Or more generally, the system is busy and should not turn off.)
#
mythshutdown --check
MYTHSTATUS=$?
if [ $MYTHSTATUS -eq 0  ]
then
#    Backend thinks it is OK to shut down.
  RUNNING_XINE=`ps -ef | grep xine | grep -v use_xine | wc -l`
  if [ $RUNNING_XINE -ne 0 ]
  then
#    Xine is running, block shutdown
#    ignore use_xine since the restart of mymythtv.sh in the last line
#      may leave that script hanging around
      MYTHSTATUS=1
  else
    FRONTSTATUS=`ps -ef | grep mythfrontend.real | grep /usr/bin | wc -l`
    if [ $FRONTSTATUS -ne 0 ]
    then
#    Frontend is running, block shutdown
      MYTHSTATUS=1
    fi
  fi
else
  MYTHSTATUS=1
fi
exit $MYTHSTATUS

```

and

/usr/local/bin/use_xine.sh
```
#!/bin/sh
# play a DVD using xine instead of the built in player
## version 2, leave backend running because shutdown check has been modified
export DISPLAY=:0.1
##/etc/init.d/mythtv-backend stop
kill -9 `ps -ef | grep mymythtv.sh | grep david | extract -mt -sc 2 -nc 1`
killall mythwelcome
killall mythfrontend.real
xine -B -G 604x456+18+12 --no-splash dvd:/
#
# start it back up again after xine exits
#
##/etc/init.d/mythtv-backend start
# here output is logged, alternatively, send it to /dev/null
/usr/local/bin/mymythtv.sh >/home/david/mm.log 2>&1 </dev/null

```

---

### Post by mathog on 2009-08-10
This is better, the previous one was missing one grep, and this one is easier to understand:

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
#  busy.(Or more generally, the system is busy and should not turn off.)
#
mythshutdown --check
MYTHSTATUS=$?
if [ $MYTHSTATUS -ne 0  ]
then
  exit 1
fi
#    Backend thinks it is OK to shut down.
RUNNING_XINE=`ps -ef | grep xine | grep -v use_xine | grep -v grep | wc -l`
if [ $RUNNING_XINE -ne 0 ]
then
  exit 1
fi
#    Xine is not running (ignore use_xine, it could be left after xine exits)
FRONTSTATUS=`ps -ef | grep mythfrontend.real | grep /usr/bin | wc -l`
if [ $FRONTSTATUS -ne 0 ]
then
#    Frontend is running, block shutdown
  exit 1
fi
#all conditions for shutdown have been met
exit 0


```

---

### Post by mathog on 2009-08-23
Discovered that irexec was having issues delivering events once xine had run one time.  This broke the failsafe shutdown, since it could not be triggered from the remote.  This modified version is better, but still not perfect.  The problem is that if one presses the "exit" key immediately after Xine starts, Xine disappears from the screen, but "ps -ef" shows that it is still running, so the use_xine.sh script never releases the lock file and the system hangs - again.  Sigh.  The main problem here seems to be that the the delivery of lirc signals to the appropriate target is a bit of a black art.

mythtv_failsafe.sh
```

#!/bin/sh
#
# this is run with the "digital/analog" button on the remote.
# It blows up the front end so that mymythtv.sh can restart it.
# Also blows up firefox, and xine with its lock file in case
# one of those was started.
# MATHOG AUG-23-2009
#
killall firefox
killall xine
rm -f /home/david/usingxine
killall mythfrontend.real
killall mythfrontend
killall mythwelcome
```

mymythtv.sh
```
#!/bin/sh
#
#  This script sets the display and then starts mythfrontend
#  The while loop is to restart mythwelcome if it should crash or exit
#  for some reason.
#
#  if the TV idles at the main screen too long it will blank if the
#  screensaver is on.  No mouse to shake to get it back
#
killall gnome-screensaver
rm -f /home/david/usingxine
#
#  This works so long as mythfrontend is NOT set to start automatically.
#  It cannot be set that way anyway, because if it is programmed recording
#  will start the frontend, and then the backend cannot shut down the system.
#
export DISPLAY=:0.1
while [ 1 ]; do
  if [ -e /home/david/usingxine ]
  then
    sleep 1
  else
    logger "starting mythwelcome at `date`"
    mythwelcome --logfile /var/log/mythtv/mythwelcome.log
    logger "mythwelcome exited at `date`"
  fi
done
```

use_xine.sh
```
#!/bin/sh
# play a DVD using xine instead of the built in player
## version 3, leave backend running because shutdown check has been
## modified, AND use a lock file to control mythwelcome restart by 
## mymythtv.sh, which is allowed to keep running.
export DISPLAY=:0.1
##/etc/init.d/mythtv-backend stop
##kill -9 `ps -ef | grep mymythtv.sh | grep david | extract -mt -sc 2 -nc 1`
logger "xine lock applied"
touch /home/david/usingxine
killall mythwelcome
killall mythfrontend.real
xine -B -G 604x456+18+12 --no-splash dvd:/
logger "xine exited"
#
# start it back up again after xine exits by removing the lock file.
# This lets mymythtv.sh restart the frontend.
#
rm -f /home/david/usingxine
logger "xine lock removed"

```

---

