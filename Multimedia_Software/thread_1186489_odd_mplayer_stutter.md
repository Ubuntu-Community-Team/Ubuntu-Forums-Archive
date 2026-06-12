---
title: "odd mplayer stutter"
date: 2009-06-13
forum: Multimedia Software
---

### Post by fedoraboy on 2009-06-13
Background:
I have a mp3 jukebox streaming on my local LAN.  The streaming server also has a tie into my stereo and plays a constant 24/7 stream using mplayer.  The odd issue will come up after about 8 or more hours of playing.  After that, I start getting a little bit of stutter on mplayer.

I am not sure if this is an mplayer issue or ... maybe the process is occasionally getting swapped out.  Mplayer gets started with a pretty decent size cache... and is run with a negative nice value.

Any ideas?

Here's the startup script for the local mplayer:
> 
#! /bin/sh
#
# local_audio init.d file
#
#       Based on the skeleton init.d file 
#

### BEGIN INIT INFO
# Provides:          local_audio_player
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Should-Start:      $local_fs $network
# Should-Stop:       $local_fs $network
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: plays music locally
# Description:       Starts, stops and reloads configuration of
#                    the local audio player 
#                    
### END INIT INFO
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC=jukebox-local-player
USERID=jukebox
DAEMON="/usr/bin/mplayer"
OPTIONS="-slave -really-quiet -autosync 10 -cache 1024 -nolirc http://localhost:8000/"
if [ "x$OPTIONS" != "x" ]; then
  OPTIONS="-- $OPTIONS"
fi

test -x $DAEMON || exit 0


set -e

case "$1" in
  start)
        echo -n "Starting $DESC: "
        echo -n "give away device perms. "
        echo "Giving away audio device perms"
        # ignoring /dev/dsp /dev/adsp /dev/audio /dev/mixer
        for dev in /dev/sr0  /dev/snd/* ; do
                chgrp $USERID $dev
                chmod g+rw $dev
                #setfacl -m g:$USERID:rw $dev
        done
        echo -n "set master volume up. "
        /usr/bin/amixer set 'Master',0 30
        /usr/bin/amixer set 'PCM',0 30
        start-stop-daemon --start --quiet --nicelevel -4 \
        --chuid $USERID:$USERID         \
        --exec $DAEMON $OPTIONS 2>/dev/null >/dev/null &
        echo "mplayer."
        ;;
  stop)
        echo -n "Stopping $DESC: "
        start-stop-daemon --stop --oknodo --quiet --name mplayer
        echo "mplayer"
        ;;
  reload|force-reload)
        echo "No reload function for local player."
        ;;
  restart)
        echo -n "Restarting $DESC: "
        start-stop-daemon --stop --oknodo --signal KILL --name `basename $DAEMON`
        echo "stop mplayer."

        sleep 5
        echo "mplayer."
        start-stop-daemon --start --quiet --nicelevel -4 \
        --chuid $USERID:$USERID         \
        --exec $DAEMON $OPTIONS 2>/dev/null >/dev/null &
        ;;
  *)
        N=/etc/init.d/$NAME
        # echo "Usage: $N {start|stop|restart|reload|force-reload}" >&2
        echo "Usage: $N {start|stop|restart|force-reload}" >&2
        exit 1
        ;;
esac

exit 0



---

