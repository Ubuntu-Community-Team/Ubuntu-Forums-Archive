---
title: "Serial blaster with MCEUSB remote on Hardy Mythbuntu?"
date: 2009-06-06
forum: Multimedia Software
---

### Post by sgtrock on 2009-06-06
OK, this is strange.  I can either use my remote and not change channels on my Dish receiver through my serial IR blaster, or change channels on my Dish and not use my remote.  (I have an OTA antenna and the Dish receiver for inputs, btw.)

By default, when my Mythbuntu box boots, the remote works.  "ps -ef | grep lir" shows:

> root     10087     1  0 18:16 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0 --pidfile=/home/mythbuntu/lirc.pid

If I then start another copy of lircd like this:

```
sudo /usr/sbin/lircd --device=/dev/lirc1 --pidfile=/home/mythbuntu/lirc1.pid
```

The remote quits working.  However, I can then use the keyboard to change channels for both Dish and OTA.

"ps -ef | grep lir" shows this:

> root     10087     1  0 18:16 ?        00:00:00 /usr/sbin/lircd --device=/dev/lirc0 --pidfile=/home/mythbuntu/lirc.pid
root     10204     1  0 18:18 ?        00:00:11 /usr/sbin/lircd --device=/dev/lirc1 --pidfile=/home/mythbuntu/lirc1.pid

From looking through my configuration and the startup script, it looks to me as if I should have both working without having to do anything.  Anyone have any thoughts on what I'm missing?  

(See below)

/etc/lirc/hardware.conf:
```

# /etc/lirc/hardware.conf
#
#Chosen Remote Control
REMOTE="Windows Media Center Remotes (new version Philips et al.)"
REMOTE_MODULES="lirc_dev lirc_mceusb2"
REMOTE_DRIVER=""
REMOTE_DEVICE=""
REMOTE_LIRCD_CONF="mceusb/lircd.conf.mceusb"
REMOTE_LIRCD_ARGS=""

#Chosen IR Transmitter
TRANSMITTER="Serial Port (UART) : Dish Receiver"
TRANSMITTER_MODULES="lirc_dev lirc_serial"
TRANSMITTER_DRIVER=""
TRANSMITTER_DEVICE=""
TRANSMITTER_LIRCD_CONF="dish/general.conf"
TRANSMITTER_LIRCD_ARGS=""

#Enable lircd
START_LIRCD="true"

#Don't start lircmd even if there seems to be a good config file
#START_LIRCMD="false"

#Try to load appropriate kernel modules
LOAD_MODULES="true"

# Default configuration files for your hardware if any
LIRCMD_CONF=""

#Forcing noninteractive reconfiguration
#If lirc is to be reconfigured by an external application
#that doesn't have a debconf frontend available, the noninteractive
#frontend can be invoked and set to parse REMOTE and TRANSMITTER
#It will then populate all other variables without any user input
#If you would like to configure lirc via standard methods, be sure
#to leave this set to "false"
FORCE_NONINTERACTIVE_RECONFIGURATION="false"
START_LIRCMD=""

```

/etc/lirc/lircd.conf:
```
#This configuration has been automatically generated via
#the Ubuntu LIRC package maintainer scripts.
#
#It includes the default configuration for the remote and/or
#transmitter that you have selected during package installation.
#
#Feel free to add any custom remotes to the configuration
#via additional include directives or below the existing
#Ubuntu include directives from your selected remote and/or
#transmitter.

#Configuration for the Windows Media Center Remotes (new version Philips et al.) remote:
include /usr/share/lirc/remotes/mceusb/lircd.conf.mceusb

#Configuration for the Serial Port (UART) : Dish Receiver transmitter:
include /usr/share/lirc/transmitters/dish/general.conf
```

/etc/init.d/lirc
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          lirc
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Should-Start:      $local_fs
# Should-Stop:       $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts LIRC daemon.
# Description:       LIRC is used to control different
#                    infrared receivers and transceivers.
### END INIT INFO

load_modules ()
{
    local MODULES_MISSING=false

    log_daemon_msg "Loading LIRC modules"
    for mod in $*
    do
        if [ $mod = "udev" ]; then
            log_end_msg 0
            log_success_msg "Restarted via udev, don't reload modules"
            break
        else
            modprobe -k $mod 2> /dev/null || MODULES_MISSING=true
        fi
    done
    log_end_msg $?

    if $MODULES_MISSING; then
        log_failure_msg "Unable to load LIRC kernel modules. Verify your"
        log_failure_msg "selected kernel modules in /etc/lirc/hardware.conf"
        START_LIRCMD=false
        START_LIRCD=false
    fi
}

build_remote_args ()
{
    local REMOTE_ARGS="$*"

    #For remote only detection support, we need
    #both REMOTE_DEVICE and TRANSMITTER_DEVICE undefined
    if [ -z "$REMOTE_DEVICE" ] && [ -z "$TRANSMITTER_DEVICE" ]; then
        for dev in /dev/lirc0; do
            if [ -c $dev ]; then
                REMOTE_DEVICE="$dev"
                break
            fi
        done
    fi

    #If we have a REMOTE_DEVICE or REMOTE_DRIVER defined (either because no devices
    #were defined, OR if we explicitly did), then populate REMOTE_ARGS
    if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
        if [ -n "$REMOTE_DEVICE" ] && [ "$REMOTE_DEVICE" != "none" ]; then
            REMOTE_ARGS="--device=$REMOTE_DEVICE $REMOTE_ARGS"
        fi
        if [ -n "$REMOTE_DRIVER" ] && [ "$REMOTE_DRIVER" != "none" ]; then
            REMOTE_ARGS="--driver=$REMOTE_DRIVER $REMOTE_ARGS"
        fi

        #Now, if we ALSO have a transmitter defined, add some args
        #To make the first lircd listen up
        if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
            REMOTE_ARGS="$REMOTE_ARGS --output=/dev/lircd --listen"
        fi
    fi
    REMOTE_ARGS="$REMOTE_ARGS --pidfile=/home/mythbuntu/lirc.pid"
    echo $REMOTE_ARGS
}

build_transmitter_args ()
{
    local TRANSMITTER_ARGS="$*"

    #Transmitters must be explicitly be defined
    if [ ! -z "$TRANSMITTER_DEVICE" ] || [ ! -z "$TRANSMITTER_DRIVER" ]; then
        if [ -n "$TRANSMITTER_DEVICE" ] && [ "$TRANSMITTER_DEVICE" != "none" ]; then
            TRANSMITTER_ARGS="--device=$TRANSMITTER_DEVICE $TRANSMITTER_ARGS"
        fi
        if [ -n "$TRANSMITTER_DRIVER" ] && [ "$TRANSMITTER_DRIVER" != "none" ]; then
            TRANSMITTER_ARGS="--driver=$TRANSMITTER_DRIVER $TRANSMITTER_ARGS"
        fi

        #Now, if we ALSO have a remote defined, add some args
        #To make the second lircd connect
        if [ ! -z "$REMOTE_DEVICE" ] || [ ! -z "$REMOTE_DRIVER" ]; then
            TRANSMITTER_ARGS="$TRANSMITTER_ARGS --output=/dev/lircd1 --connect=localhost:8765 --pidfile=/var/run/lircd1.pid"
        fi
    fi
    echo $TRANSMITTER_ARGS
}

. /lib/lsb/init-functions

test -f /usr/sbin/lircd || exit 0
test -f /usr/sbin/lircmd || exit 0

START_LIRCMD=true
START_LIRCD=true

if [ -f /etc/lirc/hardware.conf ];then
    . /etc/lirc/hardware.conf
fi

if [ ! -f /etc/lirc/lircd.conf ] \
    || grep -q "^#UNCONFIGURED"  /etc/lirc/lircd.conf;then
    if [ "$1" = "start" ]; then
        log_success_msg "No valid /etc/lirc/lircd.conf has been found."
        log_success_msg "Remote control support has been disabled."
        log_success_msg "Reconfigure LIRC or manually replace /etc/lirc/lircd.conf to enable."
    fi
    START_LIRCD=false
    START_LIRCMD=false
fi
if [ ! -f /etc/lirc/lircmd.conf ] \
    || grep -q "^#UNCONFIGURED" /etc/lirc/lircmd.conf;then
    START_LIRCMD=false
fi

case "$1" in
    start)
        if [ "$LOAD_MODULES" = "true" ] && [ "$START_LIRCD" = "true" ]; then
            load_modules $2 $REMOTE_MODULES $TRANSMITTER_MODULES $MODULES
        fi
        if $START_LIRCD; then
            log_daemon_msg "Starting remote control daemon(s) : LIRC "
            REMOTE_LIRCD_ARGS=`build_remote_args $REMOTE_LIRCD_ARGS`
            TRANSMITTER_LIRCD_ARGS=`build_transmitter_args $TRANSMITTER_LIRCD_ARGS`

            #if we have a remote defined, it is primary process
            if [ ! -z "$REMOTE_LIRCD_ARGS" ]; then
                start-stop-daemon --start --quiet \
                        --exec /usr/sbin/lircd -- $REMOTE_LIRCD_ARGS < /dev/null
                log_end_msg $?

                #now if we additionally have a transmitter defined, it is secondary process
                if [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
                    /usr/sbin/lircd $TRANSMITTER_LIRCD_ARGS < /dev/null
                fi
            elif [ ! -z "$TRANSMITTER_LIRCD_ARGS" ]; then
                start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $TRANSMITTER_LIRCD_ARGS < /dev/null
            else
                log_end_msg 1
            fi
        fi
        if $START_LIRCMD; then
            log_daemon_msg "Starting remote control mouse daemon : LIRCMD "
            start-stop-daemon --start --quiet --exec /usr/sbin/lircmd < /dev/null
            log_end_msg $?
        fi
        ;;
    stop)
        if $START_LIRCMD; then
            log_daemon_msg "Stopping remote control mouse daemon: LIRCMD"
            start-stop-daemon --stop --quiet --exec /usr/sbin/lircmd
            log_end_msg $?
        fi
        if $START_LIRCD; then
            log_daemon_msg "Stopping remote control daemon(s): LIRC"
            start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
            log_end_msg $?
        fi
        ;;
    reload|force-reload)
        if $START_LIRCD; then
            start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircd
        fi
        if $START_LIRCMD; then
            start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircmd
        fi
        ;;
    restart)
        $0 stop
        #passes parameter $2 which is possibly our udev paramater
        $0 start $2
        ;;
    *)
        echo "Usage: /etc/init.d/lircd {start|stop|reload|restart|force-reload}"
        exit 1
esac

exit 0
```

---

