---
title: "Darkice Startup"
date: 2007-01-04
forum: Multimedia &amp; Video
---

### Post by ezsra.mcdonald on 2007-01-04
I have spent the better part of this morning trying to get a startup script for Darkice working. It works on the command line but never loads up on boot. Any assistance is appreciated. If you have a working script please share it.


I have tried the following:

1. update-rc.d darkice defaults 99 20

2. Added to the rc.local file

3. Linked into the rcS.d dir

I see the script get executed but the daemon is not running after boot.

Here is my startup script modeled off of the cron startup script.

```
#!/bin/sh
# Start/stop the darkice daemon
#
### BEGIN INIT INFO
# Provides:          darkice
# Required-Start:    $syslog $time
# Required-Stop:     $syslog $time
# Default-Start:     2 3 4 5 6
# Default-Stop:      S 0 1 6
# Short-Description: Darkice Audio streamer
# Description:       Darkice Audio streamer

### END INIT INFO


test -f /usr/local/bin/darkice || exit 0

. /lib/lsb/init-functions

case "$1" in
start)  log_begin_msg "Starting Darkice audio streamer..."
        start-stop-daemon --start -b -m -p /var/run/darkice.pid -n darkice -x /usr/local/bin/darkice -- -c /usr/local/etc/darkice.cfg
        log_end_msg $?
        ;;
stop)   log_begin_msg "Stopping Darkice audio streamer..."
        start-stop-daemon --stop --quiet --pidfile /var/run/darkice.pid --name darkice
        log_end_msg $?
        ;;
restart) log_begin_msg "Restarting Darkice audio streamer..."
        start-stop-daemon --stop --retry 5 --quiet --pidfile /var/run/darkice.pid --name darkice
        start-stop-daemon --start -b -m -p /var/run/darkice.pid -n darkice -x /usr/local/bin/darkice -- -c /usr/local/etc/darkice.cfg
        log_end_msg $?
        ;;
*)      log_success_msg "Usage: /etc/init.d/darkice start|stop|restart"
        exit 1
        ;;
esac
exit 0
```

---

