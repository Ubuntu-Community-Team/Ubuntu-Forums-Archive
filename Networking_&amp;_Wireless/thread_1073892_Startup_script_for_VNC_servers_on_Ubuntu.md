---
title: "Startup script for VNC servers on Ubuntu"
date: 2009-02-18
forum: Networking &amp; Wireless
---

### Post by hzFVOW00pw on 2009-02-18
Just worked on an initscript for VNC servers.

Put this one in /etc/init.d, name it vncservers and do a chmod +x /etc/init.d/vncservers


```
#!/bin/bash

# Scripted by <snip>

# chkconfig: 2345 91 35
# description: Starts and stops vncserver. \
# Used to provide remote X administration services.

### BEGIN INIT INFO
# Provides: vncservers
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Required-Start: networking
# Required-Stop: networking
# Short-Description: Starts and stops vncserver
# Description: Used to provide remote X administration services.
### END INIT INFO

# Source function library.

. /lib/lsb/init-functions

VNCSERVERS=""

[ -f /etc/default/vncservers ] && . /etc/default/vncservers || exit 0

start() {

    ulimit -S -c 0 >/dev/null 2>&1

    RETVAL=0

    for display in ${VNCSERVERS}; do

    eval cd ~${display##*:}

    if [ -e ".vnc/passwd" ]; then

        log_begin_msg "Starting VNC Server for user ${display##*:}:"

        unset BASH_ENV ENV

        su ${display##*:} -c "cd ~${display##*:} && vncserver :${display%%:*}"

        RETVAL="$?"

        if [ "$RETVAL" -ne 0 ]; then

        log_end_msg 1
    
        break

        else

        log_end_msg 0

        fi

    else

        log_begin_msg "Not starting VNC Server for user ${display##*:}.\n   File \"~${display##*:}/.vnc/passwd\" not found.\n   Create a password file for the VNC server with vncpasswd"

        log_end_msg 1

    fi

    done

    [ "$RETVAL" -eq 0 ] && touch "/var/lock/vncserver"

}

stop() {

    unset BASH_ENV ENV

    for display in ${VNCSERVERS}; do

    log_begin_msg "Shutting down VNC Server for user ${display##*:}: "

    su ${display##*:} -c "vncserver -kill :${display%%:*}" >/dev/null 2>&1

    RETVAL="$?"

    [ "$RETVAL" -eq 0 ] && log_end_msg 0 || log_end_msg 1

    done

    [ -f "/var/lock/vncserver" ] && rm -f "/var/lock/vncserver"

}

case "$1" in

    start)        start
            ;;

    stop)        stop
            ;;

    restart|reload)    stop
            start
            ;;

    *)            echo $"Usage: $0 {start|stop|restart}"
            exit 1
            ;;

esac

exit 0

```

Put this next one in /etc/default and name it vncservers. Edit to your likings.

```

# The VNCSERVERS variable is a list of display:user pairs.
#
# Uncomment the line below to start a VNC server on display :1
# as my 'myusername' (adjust this to your own). You will also
# need to set a VNC password; run 'man vncpasswd' to see how
# to do that.
#
# DO NOT RUN THIS SERVICE if your local area network is
# untrusted! For a secure way of using VNC, see
# <URL:http://www.uk.research.att.com/vnc/sshvnc.html>.

VNCSERVERS="1:ubuntu 2:joe"

# ubuntu's VNC options
VNCSERVERARGS[1]="-geometry 1024x768"

# joe's VNC options
VNCSERVERARGS[2]="-geometry 1280x1024"

```

Have fun.

= = = = =
Comment from **alexander-stohr** 2013-12-05, changes needed:

```
su ${display##*:} -c "cd ~${display##*:} && vncserver :${display%%:*} ${VNCSERVERARGS[${display%%:*}]}"
```
post configuration:
```
update-rc.d vncservers defaults
```

---

