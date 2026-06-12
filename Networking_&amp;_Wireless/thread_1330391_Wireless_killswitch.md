---
title: "Wireless killswitch"
date: 2009-11-18
forum: Networking &amp; Wireless
---

### Post by slakkie on 2009-11-18
Hello,

I make use of my killswitch for wireless. There is one little annoyance, wpa_supplicant doesn't start when the switch is disabled (wifi disabled) and I want to start wpa_supplicant when the switch is enabled. 

I want to start wpa_supplicant when I enable wireless again without having to start wpa_supplicant manually. Which file is responsible keeping the killswitch state?

---

### Post by slakkie on 2009-11-20
Never mind, I fixed it with a bit of a hack:

```

!/usr/bin/env bash                                                       
#set -x                                                                   

_pid=/var/run/kswifi.pid

SLEEP=5
WPA="/etc/init.d/wpa.sh"


check_user() {
    if [ "$UID" -ne 0 ] ; then
        echo "This program needs to be run as root"
        exit 1                                     
    fi                                             
}                                                  


get_pid() {
    pid=$(cat $_pid);
    pidname=$(ps -p $pid -o comm=)
}                                 

stop() {
    check_user
    get_pid   
    if [ -n "$pidname" ] ; then
        kill $pid  &>/dev/null 
        return $?              
    fi                         
    return 0                   
}                              

restart() {
    stop   
    start  
}          


status() {
    get_pid
    if [ -n "$pidname" ] ; then
        echo Running: $pid     
        exit 0                 
    fi                         
    exit 1                     
}                              

start() {
    check_user
    get_pid   
    if [ -n "$pidname" ] ; then
        echo Already running
        return 0
    fi
    _start
    return 0
}


start_wpa() {
    $WPA status &>/dev/null
    local wpa=$?

    lsusb | grep -q "Dell Computer Corp. Wireless 360 Bluetooth"
    local usb=$?

    if [ $usb -eq 0 ] && [ $wpa -ne 0 ] ; then
        $WPA start
    elif [ $usb -ne 0 ] && [ $wpa -eq 0 ] ; then
        $WPA stop
    fi
    return 0
}

_start() {
    (while : ; do
        start_wpa
        [ $? -ne 0 ] && sleep $SLEEP
    done)&
    RC=$!
    echo $RC > $_pid
    #echo "$$ -> $RC"
}

case $1 in
    start|restart|stop|status) $1;;
    *) echo "Usage: $(basename $0) <start|restart|stop|status>" ;;
esac

```

---

