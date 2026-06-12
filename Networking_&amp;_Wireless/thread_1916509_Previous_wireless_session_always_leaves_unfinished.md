---
title: "Previous wireless session always leaves unfinished process"
date: 2012-01-28
forum: Networking &amp; Wireless
---

### Post by yngens on 2012-01-28
I have managed to configure my Ubuntu Server 10.4 LTS to wirelessly connect to Internet following the instructions on:  [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic) The only problem it doesn't restart when booting the system or running

```
sudo /etc/init.d/networking restart
```

because always there is some process using wpa_supplicant.log. So I have to manually find its pid with:

```
sudo fuser /var/log/wpa_supplicant.log
```
 
and then 

```
sudo rm -rf /var/run/wpa_supplicant/eth2
 sudo kill [pid] 
```

Only after that running ```
sudo /etc/init.d/networking restart
``` brings up wireless connection.

The content of wpa.sh file from [https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic](https://help.ubuntu.com/community/NetworkConfigurationCommandLine/Automatic) is:


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
INTERFACE=eth2
DRIVER=wext
DAEMONMODE="-B"
LOGFILE=/var/log/$WPA.log

function start() {

    # TODO: Support multiple interfaces and drivers
    OPTIONS="-c $CONF -i $INTERFACE -D $DRIVER $DAEMONMODE"

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

How can I solve this annoying issue to avoid additional manual work after each reboot?

---

