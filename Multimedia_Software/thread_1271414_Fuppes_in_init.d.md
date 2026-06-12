---
title: "Fuppes in init.d"
date: 2009-09-20
forum: Multimedia Software
---

### Post by xshad0wfx on 2009-09-20
High i recently followed a tutorial [http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d](http://fuppes.ulrich-voelkel.de/wiki/index.php?title=Startup_with_Init.d)  to try and get fuppes to autostart when booted but it didnt work.  The service does not run when my computer is booted. and when i type in /etc/init.d/fuppesd start  i get an error saying start-stop-daemon: Unable to set gid to 123 (Operation not permitted)
it works in sudo /etc/init.d/fuppesd start and fuppes runs, but i want it to autostart when i boot in init.d that way i dont need to actually login and i can just wake on lan my comp via my laptop and have the ubuntu media server plugged in somwhere.

---

### Post by waxxey on 2009-09-21
i have the exact same problem, running fuppes 0.646 on jaunty

---

### Post by xshad0wfx on 2009-09-21
im running the same version of fuppes in jaunty as well, has anyone have any thoughts as to how to solve this issue?

---

### Post by waxxey on 2009-09-21
i thought it might be problems with the group or the user fuppes, but when i changed the user and group to my username in /etc/init.d/fuppesd the problem persisted. i tried to manually add my user to the group fuppes but that did nothing. as far as i can see (not far) the script won't load during boot.

---

### Post by waxxey on 2009-09-21
found a work around, quite simple, so probably not the ideal solution for most cases, but for me it's ok. i went back in /etc/init.d/fuppesd changed the user and group to my login name, saved. then i went to the system tab -> preferences -> startup applications and added the script "/etc/init.d/fuppesd start" to the command line. next boot up it worked. i haven't tried using root.

---

### Post by nickwalnut on 2009-10-29
Hi I've been having the same problem since Jaunty came out. I tried what you did waxxey and still nothing. I've had to resort since then to use a script on my windows machine, connecting to the Ubuntu machine through Plink, logging in under my username using an ID and then commencing the fuppes process from there.
 
It works ok, it''s just that my windows machine now has to be on for us to use fuppes, and it's rather annoying.
 
Anybody solve this problem yet?
 
Thx in advance

---

### Post by Shhnap on 2009-11-03
This error disappeared for me after i ran sudo make install and my working /etc/init.d/fuppesd file is:

```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          fuppesd
# Required-Start:    $local_fs $remote_fs
# Required-Stop:     $local_fs $remote_fs
# Default-Start:     2 3 4 5
# Default-Stop:      S 0 1 6
# Short-Description: UPnP Media Server
# Description:       Fuppes UPnP media server.
### END INIT INFO
echo "Currently does not run, please edit /etc/init.d/fuppesd to get to init properly."
exit 0

PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin
DESC="UPnP Media Server"
NAME=fuppesd
DAEMON=`which $NAME`
DAEMON_ARGS="--config-dir /etc/fuppes/ --database-file /var/lib/fuppes/fuppes.db --log-level 1"
SCRIPTNAME=/etc/init.d/$NAME
FUPPES_USER=fuppes
FUPPES_GROUP=fuppes

# Exit if the package is not installed
if [ ! -x "$DAEMON" ]; then
{
        echo "Couldn't find $DAEMON"
        exit 99
}
fi

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.0-6) to ensure that this file is present.
. /lib/lsb/init-functions

#
# Function that starts the daemon/service
#
do_start()
{
	# Return
	#   0 if daemon has been started
	#   1 if daemon was already running
	#   2 if daemon could not be started
	start-stop-daemon --start --quiet --chuid $FUPPES_USER:$FUPPES_GROUP --exec $DAEMON --test > /dev/null \
		|| return 1
	start-stop-daemon --start --quiet --chuid $FUPPES_USER:$FUPPES_GROUP --exec $DAEMON -- $DAEMON_ARGS \
		|| return 2
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
	start-stop-daemon --stop --signal 2 --retry 5 --quiet --name $NAME
	RETVAL="$?"
	[ "$RETVAL" = 2 ] && return 2
	return "$RETVAL"
}

case "$1" in
  start)
	log_daemon_msg "Starting $DESC" "$NAME"
	do_start
	case "$?" in
		0|1) log_end_msg 0 ;;
		2) log_end_msg 1 ;;
	esac
	;;
  stop)
	log_daemon_msg "Stopping $DESC" "$NAME"
	do_stop
	case "$?" in
		0|1) log_end_msg 0 ;;
		2) log_end_msg 1 ;;
	esac
	;;
  restart|force-reload)
	log_daemon_msg "Restarting $DESC" "$NAME"
	do_stop
	case "$?" in
	  0|1)
		do_start
		case "$?" in
			0) log_end_msg 0 ;;
			1) log_end_msg 1 ;; # Old process is still running
			*) log_end_msg 1 ;; # Failed to start
		esac
		;;
	  *)
	  	# Failed to stop
		log_end_msg 1
		;;
	esac
	;;
  *)
	echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
	exit 3
	;;
esac

:
```

Also make sure that your fuppes.cfg and vfolder.cfg files are inside a folder called /etc/fuppes (which the fuppes user should own) and make sure that the fuppes.db file is in /var/lib/fuppes
[Which is explained here: [http://ubuntuforums.org/showthread.php?t=1021890]](http://ubuntuforums.org/showthread.php?t=1021890])

---

