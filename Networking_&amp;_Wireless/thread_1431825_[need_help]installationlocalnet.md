---
title: "[need help]installation/localnet"
date: 2010-03-17
forum: Networking &amp; Wireless
---

### Post by fourteenth on 2010-03-17
hi all

I'm trying to simulate install a few kind of OS to other computer in my network by boot from network method..

I'm planning to use my computer ubuntu 9.10 as boot server.

I found this article from
[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet)

but i stuck in this step
3. Start bootp: Here is a wrapper to start and stop bootpd from the command line.```

vDaemon=bootpd
vCd=/var/lib/tftpboot

Start () {
    echo -n "Starting $vDaemon: default current directory is at $vCd ... :"
    /usr/sbin/$vDaemon -d 4 -c $vCd >/tmp/$vDaemon.log 2>/tmp/$vDaemon.err &
    sleep 1
    Status
}

Stop () {
        echo "Stopping $vDaemon ..."
    kill `pidof $vDaemon`
}

Reload () {
    if [ "`pidof $vDaemon`" ] ; then
        echo "Reloading config file for $vDaemon ..."
        kill -HUP "`pidof $vDaemon`"
    fi
    Status
}

Status () {
    vPid="`pidof $vDaemon`"
    if [ "$vPid" ] ; then
        echo "$vDaemon running, pid=$vPid"
    else
        echo "$vDaemon not running"
    fi
}

case "$1" in
    start)      Start ;;
    stop)       Stop ;;
    reload) Reload ;;
    restart) Stop ; sleep 2; Start ;;
    status) Status ;;
    ""|*) echo `basename $0` parameter: start stop status reload or restart ;;esac
```


how to use this script?
is there anyone have another successful method??
thanks..

---

### Post by fourteenth on 2010-03-17
help please...:(

---

