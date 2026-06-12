---
title: "It works, but is this the correct way???"
date: 2010-10-11
forum: Networking &amp; Wireless
---

### Post by RichardUK on 2010-10-11
I have wireless working ok but i'm not sure if i've don't it correctly? 

I use wpa_supplicant to handle the connection and run it at boot from an rc script. This scripts also runs dhclient so that I get an ip address.

But is this really nessery? Should'nt it be in the interfaces file? I got a bit confused with the documentation as there seems to be more that one way to skin this cat. 

I want to do this the 'correct' way. Doing it an 'odd' way will make it hard for anyone to maintain my stuff. This is for work on a system that will be based on a customers site.


many thanks,
Richard e Collins.

---

### Post by slakkie on 2010-10-11
You can start wpa_supplicant in the interfaces file as well. Look at pre-up:

```

pre-up  /sbin/wpa_supplicant -c /etc/wpa_supplicant.conf -D wext -i eth1 -w -B

```

Personally, I start wpa_supplicant as a daemon and then configure the interface via the interfaces file.

the init.d script:

```

#!/bin/bash
### BEGIN INIT INFO
# Provides:          wpa
# Required-Start:    $network $syslog $local_fs
# Required-Stop:     $network $syslog $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Start/stop script for wpa supplicant
# Description:       Custom start/stop script for wpa_supplicant.
### END INIT INFO

SELF=`basename $0`
WPA=wpa_supplicant
PROGRAM=/sbin/${WPA}
CONF=/etc/${WPA}.conf
INTERFACE=wlan0
DRIVER=wext
DAEMONMODE="-B"
LOGFILE=/var/log/$WPA.log

function start() {

    # TODO: Support multiple interfaces and drivers
    OPTIONS="-c $CONF -i $INTERFACE -D $DRIVER $DAEMONMODE"

    ## You can remove this if you are running 8.10 and up.
    # Ubuntu 8.10 and up doesn't need the -w anymore..
    # And the logfile option is not valid on 8.04 and lower
    local ver=$(lsb_release -sr | sed -e 's/\.//g');
    [ $ver -lt 810 ] && OPTIONS="$OPTIONS -w" && LOGFILE=""
    ##

    # Log to a file
    [ -n "$LOGFILE" ] && OPTIONS="$OPTIONS -f $LOGFILE"

    echo " * Starting wpa supplicant"
    eval $PROGRAM $OPTIONS
}

function stop() {
    echo " * Stopping wpa supplicant"
    pkill $PROGRAM
}

function debug() {
    stop
    DAEMONMODE="-ddd"
    start
}

function restart() {
    stop
    start
}

function status() {
    pgrep -lf $PROGRAM
}

function usage() {
    echo "Usage: $SELF <start|stop|status|debug>"
    return 2
}

case $1 in
    start|stop|debug|status) $1 ;;
    *) usage ;;
esac

```

Make it executable and start/stop-able on startup/shutdown.
```

chmod +x /etc/init.d/wpa.sh
sudo update-rc.d wpa.sh defaults

```

And then just configure your interface as normal in /etc/network/interfaces

---

### Post by Elaztic on 2010-10-11
Hi....yeah sounds like a lot of work for something simple.

If what you are trying to achive is networking your pc through a wireless usb/internal card/pci card then it should work out of the box via the Network Manager (see your system tray - little radio waves icon).

Alternatively you can start the network manager from the terminal

```
nm-applet
```

From here you can se a list of networks and connect to them.
No need for weird scripts or anything.

---

### Post by RichardUK on 2010-10-11
Sorry, forgot to say, i'm running server edition so no UI. I'll go do some more read, thanks for the leg up 'slakkie'. :)

---

