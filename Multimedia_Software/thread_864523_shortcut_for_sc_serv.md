---
title: "shortcut for sc_serv"
date: 2008-07-19
forum: Multimedia Software
---

### Post by Sevy on 2008-07-19
Im setting up a shoutcast server for when I switch to Ubuntu:) and everything seems to be fine with shoutcast and idjc software.
All I need now is to create a shortcut to sc_serv that opens in a terminal and stays open.
Ive found the following solution [http://www.unix-tutorials.com/go.php?id=921](http://www.unix-tutorials.com/go.php?id=921)
but when I click on the shortcut the terminal doesnt stay open.
How can I keep it open?

---

### Post by Sevy on 2008-07-20
Has any fellow shoutcaster found a way of doing this?

---

### Post by spsuaiken on 2008-12-14
Probably the "easiest" (or best) way is to create startup scripts in /etc/init.d/ and add them to rc runlevels with update-rc.d

I did these after I put all the shoutcast binaries and configurations in /var/sc_serv

FIRST CREATE /etc/init.d/sc_serv FOR THE SERVER
#!/bin/sh
# /etc/init.d/sc_serv: start the shoutcast sc_serv server

### BEGIN INIT INFO
# Provides sc_serv
# Required-Start: $bootmisc $net $localmount
# Required-Stop:  $bootmisc $localmount
# Default-Start:  2 3 4 5
# Default-Stop:   0 1 6
# Short-Description:  Start sc_serv
# Description:
### END INIT INFO

PATH=/bin:/usr/bin:/sbin:/usr/sbin

SERVPATH=/var/sc_serv/sc_serv
SERVCONF=/var/sc_serv/sc_serv.conf
SERVPID=/var/sc_serv/run/sc_serv.pid

sc_serv_start() {
  echo "Starting Shoutcast Server"
  start-stop-daemon --start --exec $SERVPATH $SERVCONF --background \
                    --make-pidfile --pidfile $SERVPID --name sc_serv
}

sc_serv_stop() {
  echo "Shutting Down Shoutcast Server"
  start-stop-daemon --stop --exec $SERVPATH --pidfile $SERVPID
}


sc_serv_restart() {
  sc_serv_stop
  sc_serv_start
}

case "$1" in
'start')
sc_serv_start
;;
'stop')
sc_serv_stop
;;
'restart')
sc_serv_restart
;;
*)
sc_serv_start
esac

NOW ONTO /etc/init.d/sc_trans FOR THE TRANSCODER
#!/bin/sh

### BEGIN INIT INFO
# Required-Start:   $net $localmount $sc_serv
# Required-Stop:    $localmount
# Default-Start:    2 3 4 5
# Default-Stop:     0 1 6
# Short Description: Start / Stop sc_trans
# Description:  The transcoder to send mp3 data into the sc_serv server
### END INIT INFO

PATH=/bin:/usr/bin:/sbin:/usr/sbin

NOHUP=/usr/bin/nohup
SERVPATH=/var/sc_serv/sc_trans_linux
SERVCONF=/var/sc_serv/sc_trans.conf
SERVPID=/var/sc_serv/run/sc_trans.pid

sc_trans_start() {
  echo "Starting Shoutcast Transcoder"
  start-stop-daemon --start --exec $NOHUP $SERVPATH $SERVCONF >> /dev/null \
                    --make-pidfile --pidfile $SERVPID --name sc_trans &
}

sc_trans_stop() {
  echo "Shutting Down Shoutcast Transcoder"
  start-stop-daemon --stop --exec $SERVPATH --pidfile $SERVPID
}


sc_trans_restart() {
  sc_trans_stop
  sc_trans_start
}

case "$1" in
'start')
sc_trans_start
;;
'stop')
sc_trans_stop
;;
'restart')
;;
*)
sc_trans_start
esac

NOW UPDATE YOUR RUN LEVELS
update-rc.d -f sc_serv start 90 2 3 4 5 .
update-rc.d -f sc_trans start 91 2 3 4 5 .

sc_serv should start before sc_trans (90<91)

Hope this helps! Wouldn't mind anyone else telling me if I did dependencies AKA Required-Start stuff correct either. But for now these are working at boot.

---

