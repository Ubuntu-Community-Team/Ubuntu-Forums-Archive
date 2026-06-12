---
title: "Starting Darkice automatically on boot"
date: 2013-10-24
forum: Multimedia Software
---

### Post by Lufa on 2013-10-24
Hi! Recently I had to install darkice on Ubuntu 12.04 (and 13.10) and faced a problem many other users has: Darkice won't start on boot, Darkice won't start using "service darkice start/stop" method.

There was a [few]("http://ubuntuforums.org/showthread.php?t=1780884") [suggestions]("http://ubuntuforums.org/showthread.php?t=1642334") using cron and custom scripts.

I figured out how to do it natively, in Ubuntu-way and want to share my experience with community.

-------------------------------

So. There are few problems with Darkice startup script (/init.d/darkice) provided by package system.

1) It does not create Darkice PID-file on start.
2) It Does not delete Darkice PID-file on stop. ;)
3) It fail to check whether process is running or not.
4) Darkice can not start on boot properly (even if startup script was properly modified).

-------------------------------

Simple To-Do list:

(changed files published at the end of this post)

[SIZE=4]1[/SIZE]

In **/etc/init.d/darkice** find:
```
start-stop-daemon --start --quiet --pidfile $PIDFILE \
```
and replace it with:
```
start-stop-daemon --start --quiet -m --pidfile $PIDFILE \
```

[SIZE=4]2[/SIZE]

In **/etc/init.d/darkice** find:
```

stop_server() {
# Stop the process using the wrapper
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
            --exec $DAEMON
        errcode=$?

```
add after (with the new line):
```
    rm $PIDFILE
```

[SIZE=4]3[/SIZE]

In **/etc/init.d/darkice** find:
```

running() {
# Check if the process is running looking at /proc
# (works for all users)

```
add after (with the new line):
```
    sleep 1
```

[SIZE=4]4[/SIZE]

In **/etc/default/darkice ** check that you have
```
RUN=yes
```

[SIZE=4]5[/SIZE]

Add default user nobody to the audio group (in my case, to work with ALSA):
```
adduser nobody audio
```
or change user to whoever you need in /etc/default/darkice.

[SIZE=4]6[/SIZE]

Fix upstart problem (it seems Darkice is trying to start on boot too early):
```

update-rc.d -f darkice remove
update-rc.d darkice defaults 99 

```

That's it! I have Darkice, controlled by upstart scripts (service darkice start/stop) running on boot.

[SIZE=4]Appendix[/SIZE]

**/etc/init.d/darkice** diff:
```
 
86c86
< 
---
>     sleep 1
96c96
<         start-stop-daemon --start --quiet --pidfile $PIDFILE \
---
>         start-stop-daemon --start --quiet -m --pidfile $PIDFILE \
106a107
> 	rm $PIDFILE
184d184
<

```

**/etc/init.d/darkice** full code:
```

#!/bin/sh 
#
# Copyright (c) 2007 Javier Fernandez-Sanguino <jfs@debian.org>
# Copyright (c) 2009 Jochen Friedrich <jochen@scram.de>
#
# This is free software; you may redistribute it and/or modify
# it under the terms of the GNU General Public License as
# published by the Free Software Foundation; either version 2,
# or (at your option) any later version.
#
# This is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License with
# the Debian operating system, in /usr/share/common-licenses/GPL;  if
# not, write to the Free Software Foundation, Inc., 59 Temple Place,
# Suite 330, Boston, MA 02111-1307 USA
#
### BEGIN INIT INFO
# Provides:          darkice
# Required-Start:    $network $local_fs $remote_fs
# Required-Stop:     $network $local_fs $remote_fs
# Should-Start:      
# Should-Stop:       
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Live audio streamer
# Description:       DarkIce is an IceCast, IceCast2 and ShoutCast
#                    live audio streamer.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

NAME=darkice
DAEMON=/usr/bin/$NAME
DESC="Live audio streamer"
LOGDIR=/var/log
USER=nobody
GROUP=nogroup

PIDFILE=/var/run/$NAME.pid 

test -x $DAEMON || exit 0

. /lib/lsb/init-functions

# Default options, these can be overriden by the information
# at /etc/default/$NAME
DAEMON_OPTS=""          # Additional options given to the server 

DIETIME=2               # Time to wait for the server to die, in seconds
                        # If this value is set too low you might not
                        # let some servers to die gracefully and
                        # 'restart' will not work

# Include defaults if available
if [ -f /etc/default/$NAME ] ; then
	. /etc/default/$NAME
fi

# Use this if you want the user to explicitly set 'RUN' in 
# /etc/default/
if [ "x$RUN" != "xyes" ] ; then
    exit 0
fi

set -e

running_pid() {
# Check if a given process pid's cmdline matches a given name
    pid=$1
    name=$2
    [ -z "$pid" ] && return 1 
    [ ! -d /proc/$pid ] &&  return 1
    cmd=`cat /proc/$pid/cmdline | tr "\000" "\n"|head -n 1 |cut -d : -f 1`
    # Is this the expected server
    [ "$cmd" != "$name" ] &&  return 1
    return 0
}

running() {
# Check if the process is running looking at /proc
# (works for all users)
    sleep 1
    # No pidfile, probably no daemon present
    [ ! -f "$PIDFILE" ] && return 1
    pid=`cat $PIDFILE`
    running_pid $pid $DAEMON || return 1
    return 0
}

start_server() {
# Start the process using the wrapper
        start-stop-daemon --start --quiet -m --pidfile $PIDFILE \
            --background --chuid $USER:$GROUP --exec $DAEMON -- $DAEMON_OPTS
        errcode=$?
	return $errcode
}

stop_server() {
# Stop the process using the wrapper
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
            --exec $DAEMON
        errcode=$?
	rm $PIDFILE
	return $errcode
}

force_stop() {
# Force the process to die killing it manually
	[ ! -e "$PIDFILE" ] && return
	if running ; then
		kill -15 $pid
	# Is it really dead?
		sleep "$DIETIME"s
		if running ; then
			kill -9 $pid
			sleep "$DIETIME"s
			if running ; then
				echo "Cannot kill $NAME (pid=$pid)!"
				exit 1
			fi
		fi
	fi
	rm -f $PIDFILE
}


case "$1" in
  start)
	log_daemon_msg "Starting $DESC " "$NAME"
        # Check if it's running first
        if running ;  then
            log_progress_msg "apparently already running"
            log_end_msg 0
            exit 0
        fi
        if start_server && running ;  then
            # It's ok, the server started and is running
            log_end_msg 0
        else
            # Either we could not start it or it is not running
            # after we did
            # NOTE: Some servers might die some time after they start,
            # this code does not try to detect this and might give
            # a false positive (use 'status' for that)
            log_end_msg 1
        fi
	;;
  stop)
        log_daemon_msg "Stopping $DESC" "$NAME"
        if running ; then
            # Only stop the server if we see it running
            stop_server
            log_end_msg $?
        else
            # If it's not running don't do anything
            log_progress_msg "apparently not running"
            log_end_msg 0
            exit 0
        fi
        ;;
  force-stop)
        # First try to stop gracefully the program
        $0 stop
        if running; then
            # If it's still running try to kill it more forcefully
            log_daemon_msg "Stopping (force) $DESC" "$NAME"
            force_stop
            log_end_msg $?
        fi
	;;
  restart|force-reload)
        log_daemon_msg "Restarting $DESC" "$NAME"
        stop_server
        # Wait some sensible amount, some server need this
        [ -n "$DIETIME" ] && sleep $DIETIME
        start_server
        running
        log_end_msg $?
	;;
  status)
        log_daemon_msg "Checking status of $DESC" "$NAME"
        if running ;  then
            log_progress_msg "running"
            log_end_msg 0
        else
            log_progress_msg "apparently not running"
            log_end_msg 1
            exit 1
        fi
        ;;
  reload)
        log_warning_msg "Reloading $NAME daemon: not implemented, as the daemon"
        log_warning_msg "cannot re-read the config file (use restart)."
        ;;

  *)
	N=/etc/init.d/$NAME
	echo "Usage: $N {start|stop|force-stop|restart|force-reload|status}" >&2
	exit 1
	;;
esac

exit 0

```

Hope this will help someone. Cheers! ;)

P.S. I am wondering how to propose this changes to the package maintainer. Tnx.

---

### Post by ian-weisser on 2013-10-24
> **Lufa said:**
> I am wondering how to propose this changes to the package maintainer. Tnx.

That's what the bug tracker is for at [http://launchpad.net](http://launchpad.net)
Please file a bug report for the issue. Bug reports are always better when the solution is included, too!
The bug report should include the complete description of the issue. Repost your text there; don't just link.

---

### Post by andrew_wilson2 on 2013-11-01
thanks for the guide however after following carefully i still could not get darkice to start at boot or by invoking the service with the changes above. i can launch darkice manually however. any suggestions?
i'm using ubuntu 12.04 as i believe you are

thanks

---

### Post by Lufa on 2013-11-02
> **andrew_wilson2 said:**
> thanks for the guide however after following carefully i still could not get darkice to start at boot or by invoking the service with the changes above. i can launch darkice manually however. any suggestions?
i'm using ubuntu 12.04 as i believe you are

thanks
Hi! I am using 12.04 as well.

Try to grab all &#1089;ode of the /etc/init.d/darkice above and replace local one.

You need to be able to start/stop it manually via "service darkice ..." and then go further.

What output do you get?

P.S.
Is user you are running darkice a member of audio group? Check the username in /etc/default/darkice. Than check /etc/groups .

---

### Post by andrew_wilson2 on 2013-11-02
yep ive checked and done the above but with no luck! something must be weird. 

the only output i get is:

* Starting Live audio streamer  darkice                                 [fail]

nothing is logged
i'll have to poke around some more
thanks

---

### Post by andrew_wilson2 on 2013-11-02
update: ok if i change the init script to use the user as root and the group as root it works, must be a permissions issue. any suggestions on how i should be running it obv root isnt the best idea?

thanks

---

### Post by Lufa on 2013-11-02
It is probably OK. But preferably to use "nobody".

Do not forget to
> adduser nobody audio

I use "audio" group  for ALSA input device. May be your input device need other group.

---

### Post by Lufa on 2013-11-20
> **ian-weisser said:**
> That's what the bug tracker is for at [http://launchpad.net](http://launchpad.net)
Please file a bug report for the issue. Bug reports are always better when the solution is included, too!
The bug report should include the complete description of the issue. Repost your text there; don't just link.

Can't find the project there. The one I have found seems abandoned ([https://launchpad.net/darkice](https://launchpad.net/darkice)).

---

### Post by ian-weisser on 2013-11-20
Darkice is most recently located at [http://code.google.com/p/darkice/](http://code.google.com/p/darkice/)

---

### Post by Lufa on 2013-11-20
> **ian-weisser said:**
> Darkice is most recently located at [http://code.google.com/p/darkice/](http://code.google.com/p/darkice/)

Sure, tnx. But authors of Darkice  does not provide startup script for Ubuntu. So it is not they business to fix it.

I am looking for Ubuntu's package maintainer.

---

### Post by ian-weisser on 2013-11-20
Darkice does not have a specific maintainer in Ubuntu like it does in Debian. Instead, it's maintained by committee: [email]ubuntu-devel-discuss@lists.ubuntu.com[/email]
See [https://code.launchpad.net/~ubuntu-branches/ubuntu/trusty/darkice/trusty](https://code.launchpad.net/~ubuntu-branches/ubuntu/trusty/darkice/trusty) for an example of how darkice gets merged from Debian each cycle.

Since much of what you are discussing seems to be a bug, I suggest you elevate the specific bug-issues to the debian bug tracker at [http://bugs.debian.org/cgi-bin/pkgreport.cgi?package=darkice](http://bugs.debian.org/cgi-bin/pkgreport.cgi?package=darkice) .

If you merely want to contact the debian maintainer, you already know who that is: <jochen@scram.de>
Of course, he might just tell you to file a bug so it's in his queue. If you do that, remember to upstream the Launchpad bug.

---

