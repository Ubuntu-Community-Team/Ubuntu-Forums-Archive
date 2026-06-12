---
title: "How to I get my network to start at boot time."
date: 2009-05-02
forum: Networking &amp; Wireless
---

### Post by irv on 2009-05-02
Since I upgraded to 9.04 I have an issue with my network. I am using wicd for my network. First I get connect to my network and Internet at startup, but I don't have client. I can get it to work by doing:
[COLOR="Red"]sudo wicd and entering my password[/COLOR] at the terminal. Then I hit [Alt] F2 and enter [COLOR="Red"]wicd-client[/COLOR]. What I would like to do is start the process wicd at boot up and I can run the client in startup Applications. I am not sure how to do this? Any help would be great.
Thanks

---

### Post by irv on 2009-05-04
I posted this problem yesterday. Is there any one who could help or any ideas would be great.
Thanks.

---

### Post by imdano on 2009-05-04
How did you install wicd?  Are you getting automatically connected to your network at startup?  If that's the case, than the wicd daemon is already running at start up, and all you need to do is add wicd-client to the list of start-up applications (there's a menu entry for adding start-up apps under System I think...I'm not at my Ubuntu machine right now so I'm not sure of the exact name).  You can say for certain if the wicd daemon is starting when you boot using by running ```
ps -ef | grep wicd
``` after you boot and seeing if you get any results.

---

### Post by papangul on 2009-05-04
Check System --> Preferences --> Sessions -->  WICD tray 

..or you may try to reinstall wicd.

---

### Post by irv on 2009-05-04
When I run the command I get:
> irv@irv-old-laptop:~$ ps -ef | grep wicd
irv       9246  9227  0 13:31 pts/0    00:00:00 grep wicd
irv@irv-old-laptop:~$ 

and I have wicd-client set to auto run.
See my screen shot.

The client does not run until I run wicd again in a terminal and then run the client. then it works. This has been driving me nuts.
Thanks for all the advice and if there is anything else I can try let me know.

---

### Post by imdano on 2009-05-04
How did you install wicd?  Does running```
sudo /etc/init.d/wicd start
```work instead of running ```
sudo wicd
```?

---

### Post by irv on 2009-05-05
> **imdano said:**
> How did you install wicd?  Does running```
sudo /etc/init.d/wicd start
```work instead of running ```
sudo wicd
```?

I installed via the packager manager about a year ago. It work find until I upgrade to 9.01. I have tried to uninstall it, and reinstall it and to see what i got for errors goto this tread.
[http://ubuntuforums.org/showthread.php?t=1146286]("http://ubuntuforums.org/showthread.php?t=1146286")

I tried the code ```
sudo /etc/init.d/wicd start
```
and all it does is stop and start the wicd deamon.

---

### Post by irv on 2009-05-05
I thought I would post the exact out-put when I try to remove the wicd:
> irv@irv-old-laptop:~$ sudo apt-get remove wicd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fakeroot dkms fglrx-kernel-source
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  wicd
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 1905kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 284697 files and directories currently installed.)
Removing wicd ...
Stopping wicd daemon...
invoke-rc.d: initscript wicd, action "stop" failed.
dpkg: error processing wicd (--remove):
 subprocess pre-removal script returned error exit status 1
update-rc.d: warning: /etc/init.d/wicd missing LSB information
update-rc.d: see <http://wiki.debian.org/LSBInitScripts>
Stopping any running daemons...
Starting wicd daemon...
Errors were encountered while processing:
 wicd
E: Sub-process /usr/bin/dpkg returned an error code (1)
irv@irv-old-laptop:~$ 

When I went to the website [http://wiki.debian.org/LSBInitScripts]("http://wiki.debian.org/LSBInitScripts")that was in the returned error code, I couldn't make heads or tails of what they were saying.

---

### Post by zika on 2009-05-05
try stopping wicd daemon before trying to remove it ...
```
sudo /etc/init.d/wicd stop
sudo apt-get remove wicd
```

---

### Post by irv on 2009-05-05
> **zika said:**
> try stopping wicd daemon before trying to remove it ...
```
sudo /etc/init.d/wicd stop
sudo apt-get remove wicd
```

Same error.

---

### Post by imdano on 2009-05-05
What version of wicd are you using?  Can you paste the contents /etc/init.d/wicd?  It sounds like you're using an old version with a messed up init script.

---

### Post by irv on 2009-05-06
The version is 1.5.9
and the output is:
> #!/bin/bash

if [[ $1 = "start" ]]
then
	echo "Stopping any running daemons..."
	killall daemon.py 2> /dev/null
	echo "Starting wicd daemon..."
	/opt/wicd/daemon.py 2> /dev/null
fi

if [[ $1 = "stop" ]]
then
	echo "Stopping wicd daemon..."
	killall daemon.py 2> /dev/null
fi

---

### Post by imdano on 2009-05-06
Yep, that's the old, broken init script. Replace that with this and you should be good:
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          wicd
# Required-Start:    dbus
# Required-Stop:     
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts and stops Wicd
# Description:       Starts and stops Wicd, a network manager
### END INIT INFO

# Author: Adam Blackburn <compwiz18@users.sourceforge.net>
#

# Do NOT "set -e"

# PATH should only include /usr/* if it runs after the mountnfs.sh script
PATH=/usr/sbin:/usr/bin:/sbin:/bin
DESC="Network connection manager"
NAME=wicd
RUNDIR=/var/run/$NAME
DAEMON=/usr/sbin/$NAME
DAEMON_ARGS=""
PIDFILE=$RUNDIR/wicd.pid
SCRIPTNAME=/etc/init.d/wicd

# Exit if the package is not installed
[ -x "$DAEMON" ] || exit 0

# Create RUNDIR if it doesn't exist
[ -d "$RUNDIR" ] || mkdir -p "$RUNDIR"

# Read configuration variable file if it is present
[ -r /etc/default/$NAME ] && . /etc/default/$NAME

# Load the VERBOSE setting and other rcS variables
[ -f /etc/default/rcS ] && . /etc/default/rcS

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

# Perhaps not the best idea
# but a confirmation is nice
# when starting/stopping the daemon
VERBOSE=yes

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	#   vvvv -- don't do this -- vvvv
	#   [ -e $PIDFILE ] && return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --pidfile $PIDFILE --startas $DAEMON -- \
		$DAEMON_ARGS > /dev/null 2> /dev/null\
		|| return 2
	# Add code here, if necessary, that waits for the process to be ready
	# to handle requests from services started subsequently which depend
	# on this one.  As a last resort, sleep for some time.
}

#
# Function that stops the daemon/service
#
do_stop()
{
	# Return
	#   0 if daemon has been stopped
	#   1 if daemon was already stopped
	#   2 if daemon could not be stopped
	#   other if a failure occurred
	start-stop-daemon --stop --quiet --retry=TERM/30/KILL/5 --pidfile $PIDFILE --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	# Wait for children to finish too if this is a daemon that forks
	# and if the daemon is only ever run from this initscript.
	# If the above conditions are not satisfied then add some other code
	# that waits for the process to drop all resources that could be
	# needed by services started subsequently.  A last resort is to
	# sleep for some time.
	start-stop-daemon --stop --quiet --oknodo --retry=0/30/KILL/5 --exec $DAEMON
	[ "$?" = 2 ] && return 2
	# Many daemons don't delete their pidfiles when they exit.
	rm -f $PIDFILE
	return "$RETVAL"
}

#
# Function that sends a SIGHUP to the daemon/service
#
do_reload() {
	#
	# If the daemon can reload its configuration without
	# restarting (for example, when it is sent a SIGHUP),
	# then implement that here.
	#
	start-stop-daemon --stop --signal 1 --quiet --pidfile $PIDFILE --name $NAME
	return 0
}

case "$1" in
  start)
	if [ "$START_DAEMON" != no ]; then
	    [ "$VERBOSE" != no ] && log_daemon_msg "Starting $DESC" "$NAME"
	    do_start
        case "$?" in
            0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
            2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
        esac
	else
	    log_warning_msg "Not starting wicd daemon. Please edit /etc/default/wicd first."
	fi
	;;
  stop)
	[ "$VERBOSE" != no ] && log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) [ "$VERBOSE" != no ] && log_end_msg 0 ;;
		2) [ "$VERBOSE" != no ] && log_end_msg 1 ;;
	esac
	;;
  #reload|force-reload)
	#
	# If do_reload() is not implemented then leave this commented out
	# and leave 'force-reload' as an alias for 'restart'.
	#
	#log_daemon_msg "Reloading $DESC" "$NAME"
	#do_reload
	#log_end_msg $?
	#;;
  restart|force-reload)
	#
	# If the "reload" option is implemented then remove the
	# 'force-reload' alias
	#
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
	    if [ "$START_DAEMON" != no ]; then
	        do_start
            case "$?" in
                0) log_end_msg 0 ;;
                1) log_end_msg 1 ;; # Old process is still running
                *) log_end_msg 1 ;; # Failed to start
            esac
        else
            log_warning_msg "Not starting wicd daemon. Please edit /etc/default/wicd first."
        fi
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	#echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:

```

---

### Post by irv on 2009-05-06
Thanks imdano, that did the trick. After rebooting the wicd manager loads at boot time. Thanks again.
Irv
):P

---

### Post by silentmonkey on 2009-06-13
Thanks, imdano!  This helped me too.

My problem was slightly different, though.  For some reason my installation of wicd about a month ago didn't create the /etc/init.d/wicd file, so the rc.# scripts never worked.  I created the file and copied your script into it.  Simple!

I was similarly frustrated with having to type 'sudo wicd' each time I started up my laptop.

Now, to make sure I have the system tray icon running on startup . . .

---

