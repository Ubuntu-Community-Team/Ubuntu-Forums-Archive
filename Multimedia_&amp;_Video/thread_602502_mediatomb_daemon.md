---
title: "mediatomb daemon"
date: 2007-11-04
forum: Multimedia &amp; Video
---

### Post by takeawaydave on 2007-11-04
Installed and configured mediatomb 0.1 on to Ubuntu 7.04 and trying to run as a daemon.

Getting the following single line in /var/log/mediatomb:
2007-11-04 13:56:57   ERROR: Could not determine users home directory
I am not using user mediatomb instead have tried user david and user root.
Still the same error occurs.
This error only occurs when starting the daemon from boot not otherwise.
in other words I can start as expected by:
sudo /etc/init.d/mediatomb start
then all is ok.
Its just when I run the daemon from boot startup.
Since I can run the daemon manually ok I can't see there being a config file error. 
pulling my hair out on this.....been going round in circles for hours....please some one save me from madness....

---

### Post by takeawaydave on 2007-11-04
ok following works

add

-m option to start up in options in init script. use -m value of home/user/mediatomb

---

### Post by pedalwrench on 2007-11-11
OK

That worked great for me.

Using Gutsy with the Feisty pkgs.  Mediatomb 0.10.0

Using a PS3 to access it.

This works like a champ! :guitar:

Here is my init script:

```
#! /bin/sh 
#
# MediaTomb initscript
#
# Original Author: Tor Krill <tor@excito.com>.
# Modified by:     Leonhard Wimmer <leo@mediatomb.cc>
#
#

### BEGIN INIT INFO
# Provides:          mediatomb
# Required-Start:    $all
# Required-Stop:     $all
# Should-Start:      $all
# Should-Stop:       $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: upnp media server
### END INIT INFO


set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="upnp media server"
NAME=mediatomb
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
USER=mediatomb
GROUP=mediatomb
LOGFILE=/var/log/mediatomb
HOME=/home/mediatomb

# Read config file if it is present.
if [ -r /etc/default/$NAME ]
then
	. /etc/default/$NAME
fi

# if NO_START is set, exit gracefully
[ "$NO_START" = "yes" ] && exit 0

D_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -m $HOME -P $PIDFILE -l $LOGFILE"

if [ "$INTERFACE" != "" ] ; then
    D_ARGS="$D_ARGS -e $INTERFACE"
fi



# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

#
#       Function that starts the daemon/service.
#
d_start() {
	touch $PIDFILE
	chown $USER:$GROUP $PIDFILE
	touch $LOGFILE
	chown $USER:$GROUP $LOGFILE
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
                --exec $DAEMON -- $D_ARGS $DAEMON_OPTS
}

#
#       Function that stops the daemon/service.
#
d_stop() {
        start-stop-daemon --stop --signal 2 --retry 5 --quiet --pidfile $PIDFILE \
                --name $NAME
        rm $PIDFILE
}

#
#       Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME --signal 1
}

case "$1" in
  start)
        echo -n "Starting $DESC: $NAME"
        if [ "$INTERFACE" != "" ] ; then
            # try to add the multicast route
            /sbin/route add -net 239.0.0.0 netmask 255.0.0.0 $INTERFACE >/dev/null 2>&1 || true
        fi
        d_start
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        d_stop
        echo "."
        ;;
  reload|force-reload)
        echo -n "Reloading $DESC configuration..."
        d_reload
        echo "done."
  	;;
  restart)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        echo -n "Restarting $DESC: $NAME"
        d_stop
        sleep 1
        d_start
        echo "."
        ;;
  *)
        # echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0

```

---

### Post by dema on 2008-01-17
How do I let Ubuntu 7.10 starts mediatomb on startup?

---

### Post by JSVH on 2008-01-27
Ok, I am struggling with this issue too. I want mediatomb to start automatically so I can access it from my PS3 without having to SSH into my server to start it.

I am hoping this would be the solution. I edited my /etc/init.d/mediatomb file to look like:

```
#! /bin/sh
#
# MediaTomb initscript
#
# Original Author: Tor Krill <tor@excito.com>.
# Modified by:     Leonhard Wimmer <leo@mediatomb.cc>
# 
#

### BEGIN INIT INFO
# Provides:          mediatomb
# Required-Start:    $all
# Required-Stop:     $all
# Should-Start:      $all
# Should-Stop:       $all
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: upnp media server
### END INIT INFO


set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="upnp media server"
NAME=mediatomb
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
USER=mediatomb
GROUP=mediatomb
LOGFILE=/var/log/mediatomb
HOME=/home/jsvh

# Read config file if it is present.
if [ -r /etc/default/$NAME ]
then
        . /etc/default/$NAME
fi

# if NO_START is set, exit gracefully
[ "$NO_START" = "yes" ] && exit 0

D_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -m $HOME -P $PIDFILE -l $LOGFILE"

if [ "$INTERFACE" != "" ] ; then
    D_ARGS="$D_ARGS -e $INTERFACE"
fi



# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

#
#       Function that starts the daemon/service.
#
d_start() {
        touch $PIDFILE
        chown $USER:$GROUP $PIDFILE
        touch $LOGFILE
        chown $USER:$GROUP $LOGFILE
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
                --exec $DAEMON -- $D_ARGS $DAEMON_OPTS
}

#
#       Function that stops the daemon/service.
# 
d_stop() {
        start-stop-daemon --stop --signal 2 --retry 5 --quiet --pidfile $PIDFILE \
                --name $NAME
        rm $PIDFILE
}

#
#       Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
        start-stop-daemon --stop --quiet --pidfile $PIDFILE \
                --name $NAME --signal 1
}

case "$1" in
  start)
        echo -n "Starting $DESC: $NAME"
        if [ "$INTERFACE" != "" ] ; then
            # try to add the multicast route
            /sbin/route add -net 239.0.0.0 netmask 255.0.0.0 $INTERFACE >/dev/null 2>&1 || true
        fi
        d_start
        echo "."
        ;;
  stop)
        echo -n "Stopping $DESC: $NAME"
        d_stop
        echo "."
        ;;
  reload|force-reload)
        echo -n "Reloading $DESC configuration..."
        d_reload
        echo "done."
        ;;
  restart)
        #
        #       If the "reload" option is implemented, move the "force-reload"
        #       option to the "reload" entry above. If not, "force-reload" is
        #       just the same as "restart".
        #
        echo -n "Restarting $DESC: $NAME"
        d_stop
        sleep 1
        d_start
        echo "."
        ;;
  *)
        # echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0
```

I have also tried HOME=/home/mediatomb, and HOME=/home/jsvh/.mediatomb where the config file resides. Still no luck, Any advice?

---

### Post by MisaMisa on 2008-02-01
Check the /etc/default/mediatomb file.  The NO_START option should be set to anything other than 'yes'.

---

