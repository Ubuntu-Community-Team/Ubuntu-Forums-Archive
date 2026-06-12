---
title: "Logitech Media Server on Ubuntu 20.04"
date: 2020-05-11
forum: Multimedia Software
---

### Post by a-hartmann on 2020-05-11
I posted this [thread already to askubuntu.com]("https://askubuntu.com/questions/1188506/how-to-install-logitech-media-server-squeezebox-server") but maybe it is of interest here too.

I upgraded to Ubuntu 20.04 and that broke my installation but I figured out how to make it work again:

  After some tempering around, I considered to do a fresh install. So I deleted the old stuff in /var/lib/squeezeboxserver/

  Then I got me a fresh deb-packet from: [http://downloads.slimdevices.com/nightly/?ver=8.0](http://downloads.slimdevices.com/nightly/?ver=8.0)

  Personally I used the version for the most plattforms but depending on plattform just select a fitting deb:

  ```
wget [http://downloads.slimdevices.com/nightly/8.0/lms/cf7bcdb87b4f8bf6f71f5b5444c923afae4c300d/logitechmediaserver_8.0.0~1589180193_all.deb](http://downloads.slimdevices.com/nightly/8.0/lms/cf7bcdb87b4f8bf6f71f5b5444c923afae4c300d/logitechmediaserver_8.0.0~1589180193_all.deb)
```
  
I Installed it with: 

```
dpkg -i logitechmediaserver_8.0.0_1588799628_all.deb
```

  As I tried older versions too and even tried a git checkout I hope I  lack no detail another script has already done for me without noticing  it.

  If the dpkg installation not already added a user and group please do so:
  ```
adduser squeezeboxserver
usermod -a -G squeezeboxserver squeezeboxserver
```
  Create a directory for the pid file:
  ```
mkdir /var/run/logitechmediaserver
```
  And give it to that user and group:
  ```
chown squeezeboxserver:squeezeboxserver /var/run/logitechmediaserver
```
  Same goes for the stuff in /var/lib/squeezeboxserver/
  ```
chown squeezeboxserver:squeezeboxserver /var/lib/squeezeboxserver
chown -R squeezeboxserver:squeezeboxserver /var/lib/squeezeboxserver/*
```
  The problem comes with the startup script in /etc/init.d. It simply  does not work, as Ubuntu 20.04 does not have the start-stop-daemon any  more. It is simply linked to /bin/true which might work for some scripts  but does not work for the logitechmediaserver. I tried a C  implementation for this program, but it had it hinges so I dropped the  start-stop-daemon and modified the startup program arcordingly.
  Just store the old startup script away (just to be save) and copy this content into an editor of your choice:
  ```
#!/bin/sh
#
# $Id$
#
# logitechmediaserver   initscript for slimserver.pl
#           This file should be placed in /etc/init.d.
#
# Original Author: Mattias Holmlund
#
# Updated By: Dan Sully, Michael Herger, Alexander Hartmann

#
### BEGIN INIT INFO
# Provides:             logitechmediaserver
# Required-Start:       $all
# Required-Stop:        $all
# Should-Start:         $all
# Should-Stop:          $all
# Default-Start:        2 3 4 5
# Default-Stop:         0 1 6
# Short-Description:    Startup script for the Logitech Media Server
# Description:      Logitech Media Server powers the Squeezebox, Transporter and SLIMP3 network music \
#           players and is the best software to stream your music to any software MP3 \
#           player. It supports MP3, AAC, WMA, FLAC, Ogg Vorbis, WAV and more! \
#           As of version 7.7 it also supports UPnP clients, serving pictures and movies too!"
### END INIT INFO
#
# -e  Exit immediately if a command exits with a non-zero status.
set -e

# Load the VERBOSE setting and other rcS variables
. /lib/init/vars.sh

# Define LSB log_* functions.
# Depend on lsb-base (>= 3.2-14) to ensure that this file is present
# and status_of_proc is working.
. /lib/lsb/init-functions


### About logitechmediaserver
# The logitechmediaserver is kind of special. It uses the
# squeezeboxserver_safe script, to restart any died squeezeboxserver. This
# can easily happen, for example if you use a MySQL server. Depending on unix
# flavour you are running they sometimes do a regular restart. That would
# cause the squeezeboxserver to terminate. Because of that the 
# squeezeboxserver_safe starts a logitechmediaserver every few seconds, which
# gets shut down again if any other logitechmediaserver is still running.
#
# Sadly this procedure messes up, the process id file. You would get a new id
# file, every time a new server process gets started. That process will
# terminate but the process id of the first server process is lost. So the
# killing the squeezeboxserver have to be done with analysing the process
# table.
#
# As I upgraded to Ubuntu 20.04 my logitechmediaserver stopped working.
# Installing the lastest 8.0 version was no problem downloading the deb-packet
# and installing with dpkg. But the server did not start. I could start it
# manually but the startup script was not able to start it. After some looking
# around I found this:
#
#           /sbin/start-stop-daemon -> /bin/true
#
# This explains why the start up script is not working. There is no package
# in the ubuntu package repository for the start-stop-daemon.
#
# First I tried the C implementation of start-stop-daemon from Dale O'Brien on
# github ([https://github.com/daleobrien/start-stop-daemon](https://github.com/daleobrien/start-stop-daemon)). It does not
# implement the --remove-pidfile option the original script. But more 
# problematic it threw the error not able to terminate the server while
# doing it without a problem.
#
# I had to compile the C implementation from Dale O'Brien myself, which
# worked without a hitch. Considering the limiations of the implementation
# I came to the conclusion to ditch the start-stop-daemon completly and 
# doing it the old school way.


PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="Logitech Media Server"
NAME=squeezeboxserver
NEWNAME=logitechmediaserver
DAEMON=/usr/sbin/$NAME
DAEMON_RESTARTER=/usr/sbin/${NAME}_safe
PIDFILE=/var/run/$NEWNAME/${NEWNAME}.pid
SCRIPTNAME=/etc/init.d/$NEWNAME
SLIMUSER=$NAME
SLIGROUP=$NAME
PREFSDIR=/var/lib/$NAME/prefs
LOGDIR=/var/log/$NAME/
CACHEDIR=/var/lib/$NAME/cache
CHARSET=utf8
SLEEPTIMER=1

## if you want to add additional options
## use /usr/sbin/squeezeboxserver --help 
## for the supported options and place them
## into the configfile  /etc/default/logitechmediaserver


# Read config file if it is present.
if [ -r /etc/default/$NEWNAME ]; then
    . /etc/default/$NEWNAME
elif [ -r /etc/default/$NAME ]; then
    . /etc/default/$NAME
fi

#
#   Function that starts the daemon/service.
#
d_start() {
        # Where is your su installed?
        SU_BIN=$(command -v su)

        # Use squeezeboxserver_safe to restart the daemon when
        # it dies. This must be done to handle mysql restarts.

        $SU_BIN - $SLIMUSER \
          -s /bin/sh \
          -c "$DAEMON_RESTARTER \
                $DAEMON \
                  --user $SLIMUSER \
                  --group $SLIGROUP \
                  --prefsdir $PREFSDIR \
                  --logdir $LOGDIR \
                  --cachedir $CACHEDIR \
                  --charset=$CHARSET \
                  --daemon \
                  $SLIMOPTIONS \
              > /dev/null 2>&1 &"


        # Writing the pid for the restarter          
        PID=$(ps ax | \
          grep "$DAEMON_RESTARTER $DAEMON" | \
          grep -v grep | \
          head -1 | \
          awk '{print $1}' )

        if [ $PID ]
        then
          if [ $PID -gt 0 ]
          then
            echo -n "  Started the restarter with the process id: "
            echo $PID

            if [ -e $PIDFILE ]
            then
              rm $PIDFILE
            fi

            echo -n $PID > $PIDFILE
          fi
        else
            echo "  ERROR: No process id for the restarter could be found!"
        fi


        # Check if the server is successfully started        
        PERL_BIN=$(command -v perl)

        PID_SERVER=$(ps ax | \
          grep "$PERL_BIN $DAEMON" | \
          grep -v grep | \
          head -1 | \
          awk '{print $1}' )

        if [ $PID_SERVER ]
        then
          if [ $PID_SERVER -gt 0 ]
          then
            echo "  Started the server successfully."
          else
            echo "  ERROR: No process id for the server could be found!"        
          fi
        fi
}


#   Function that stops the daemon/service.
#
d_stop() {
    echo -n "  Checking if the restarter is still running: "

    ## This will kill the squeezeboxserver_safe script. So we don't have
    ## to bother about it, starting new processes.

    PID1=$(ps ax | \
      grep "$DAEMON_RESTARTER $DAEMON" | \
      grep -v grep | \
      head -1 | \
      awk '{print $1}' )


    if [ $PID1 ]
    then
      echo positive
      if [ $PID1 -gt 0 ]
      then
        echo -n "  Stopping now restarter: "

        kill $PID1

            if [ -e $PIDFILE ]
            then
              rm $PIDFILE
        fi

        echo done.
      fi
    else
            echo negative
        fi

    ## We have to kill at least one server process. Possible two processes
    ## and in weird cases  under real high load even three processess.
    ## So a loop it is.
    ## We have to wait for at least one second for closing the process
    ## and analyzing the process list again.

        echo -n "  Checking if any server instances are running: "

    PERL_BIN=$(command -v perl)

        PID2=$(ps ax | \
          grep "$PERL_BIN $DAEMON" | \
          grep -v grep | \
          head -1 | \
          awk '{print $1}' )

        if [ $PID2 ]
        then
          echo positive
          echo -n "  Stopping now all server instances: "
          if [ $PID2 -gt 0 ]
          then
            while [ $(ps ax | \
              grep "$PERL_BIN $DAEMON" | \
              grep -v grep | \
              head -1 | \
              awk '{print $1}') ]
            do
          kill $(ps ax | \
                grep "$PERL_BIN $DAEMON" | \
                grep -v grep | \
                head -1 | \
                awk '{print $1}')
              sleep $SLEEPTIMER
            done
            echo done
          fi
        else
          echo negative
        fi
}

#
#   Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
    start-stop-daemon --stop --quiet --pidfile $PIDFILE --signal 1
}

case "$1" in
  start)
    echo "Making sure that $DESC is not running: "
    d_stop
    echo "Starting $DESC:"
    d_start
    ;;
  stop)
    echo "Stopping $DESC:"
    d_stop
    ;;
  restart|force-reload)
    #
    #   If the "reload" option is implemented, move the "force-reload"
    #   option to the "reload" entry above. If not, "force-reload" is
    #   just the same as "restart".
    #
    echo "Restarting $NAME."
    d_stop
    d_start
    ;;
  status)  
    status_of_proc /usr/bin/$NEWNAME $NEWNAME
    ;;
  *)
    echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload|status}" >&2
    exit 1
    ;;
esac

exit 0
```
  Yeah, it's not pretty, but it does the job for me and will hopefully  help you too. You have to place it in /etc/init.d under the name  logitechmediaserver
  After that you have to run the following command to make systemctl happy:
  ```
systemctl daemon-reload
```
  Just give it a test run with starting it:
  ```
/etc/init.d/logitechmediaserver start
```
  You should be able to log in with your webbrowser to [http://YourServerIP:9000/](http://YourServerIP:9000/) and configure it.
  And test if it does shut down again:
  ```
/etc/init.d/logitechmediaserver stop
```
  When everything has worked out, enable the service:
  ```
systemctl enable logitechmediaserver.service
```

---

