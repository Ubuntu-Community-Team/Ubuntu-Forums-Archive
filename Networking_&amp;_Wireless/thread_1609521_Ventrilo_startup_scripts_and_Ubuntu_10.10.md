---
title: "Ventrilo startup scripts and Ubuntu 10.10"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by Ben_neB on 2010-10-30
Okay, I have been trying to get Ventrilo to start on boot up for days now, and I'm getting annoyed. All of the instructions and tutorials I've found online seem to be designed for versions of Ubuntu earlier than 10.10. Most notably, they reference folders such as /etc/rc.d and  and the file /etc/rc.d/rc.local, neither of which exist any longer in 10.10. 

I've tried the simple way of just using System->Preferences->Startup Applications, and that doesn't work either. It creates a ventrilo log file that claims that it can't open the .ini file necessary to create the server, even though I can just execute the same file I'm pointing to and the server starts up just fine. (This is my preferred method, because it is so simple to replicate and teach to people, and it annoys me greatly that it doesn't work like it should.) 

The longer method of creating startup scripts and placing them in the /etc/init.d folder and sym-linking them in the /etc/rc2.d folder doesn't seem to work either, as I have tried several variations of this method, and none of them start the freaking server on boot up. (I'm probably not creating the sym link correctly, but when I read the properties of the sym link, it says that it is linking to the correct file, so I don't know what I could be doing wrong.) 

Is there anyone that has a vent server that starts on bootup of 10.10 that can just tell me exactly how they accomplished that? 

I'm always telling everyone how much easier Ubuntu and Linux are than Windows, but in this case, it was a two-click deal to get vent to start on bootup of Windows, and a three-day project so far for Ubuntu, and it's really getting annoying... (So forgive me if I didn't provide enough info, I'm just tired of it not working.)

---

### Post by sir2u on 2010-11-10
I wrote this today.  It's put together with my rudimentary understanding and the skeleton init file.  It works though.

I've created a user called 'ventrilo' for the daemon to run as and the working directory is /usr/local/ventrilo/.  Change the script to suit your setup.

1)  Copy the below into /etc/init.d/ventrilo
```

#!/bin/sh
#
### BEGIN INIT INFO
# Provides:          ventrilo_srv
# Required-Start:    $network $remote_fs $syslog
# Required-Stop:     $network $remote_fs $syslog
# Should-Start:      $named
# Should-Stop:       $named
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Ventrilo version 3.0
### END INIT INFO

NAME=ventrilo_srv
DESC="Ventrilo 3.0"
DAEMON=/usr/local/ventrilo/ventrilo_srv
PIDFILE=/usr/local/ventrilo/$NAME.pid
DAEMON_ARGS="-f/usr/local/ventrilo/ventrilo_srv -d"
VENT_USER=ventrilo

do_start() {

        start-stop-daemon --quiet --start \
                --user $VENT_USER \
                --chuid $VENT_USER \
                --pidfile $PIDFILE \
                --exec $DAEMON -- $DAEMON_ARGS < /dev/null
        return $?

}

do_stop() {
        start-stop-daemon --stop --quiet \
                --retry=TERM/30/KILL/5 \
                --pidfile $PIDFILE \
                --name $NAME
        rm -f $PIDFILE
        return "$?"
}

case "$1" in
start)
        do_start
        ;;

stop)
        do_stop
        ;;

restart|reload|force-reload)
        do_stop
        sleep 10
        do_start
        ;;

*)
        echo "Usage: $0 start|stop|restart|reload|force-reload"
        exit 1
        ;;

```2)  sudo chmod 755 /etc/init.d/ventrilo
3)  sudo update-rc.d ventrilo defaults

Hope this helps.

---

### Post by ddnut on 2010-12-06
Ah I found the source to this bum script. it wont work as said!

I had to mod it some to get it up and running

First off make a user ventrilo(I made mine with null password)

Next I have my vent at /ventrilo/ventsrv/ so change in script to meet yours.


next cut and paste your new working script

```
#!/bin/sh
#
### BEGIN INIT INFO
# Provides:          ventrilo_srv
# Required-Start:    $network $remote_fs $syslog
# Required-Stop:     $network $remote_fs $syslog
# Should-Start:      $named
# Should-Stop:       $named
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Ventrilo version 3.0.3
### END INIT INFO

NAME=ventrilo_srv
DESC="Ventrilo 3.0.3"
DAEMON=/ventrilo/ventsrv/ventrilo_srv
PIDFILE=/ventrilo/ventsrv/$NAME.pid
DAEMON_ARGS="-f/ventrilo/ventsrv/ventrilo_srv -d"
VENT_USER=ventrilo

do_start() {

        start-stop-daemon --start \
                --user $VENT_USER \
                --chuid $VENT_USER \
                --pidfile $PIDFILE \
                --exec $DAEMON -- $DAEMON_ARGS < /dev/null
        return $?

}

do_stop() {
        start-stop-daemon --stop \
                --retry=TERM/30/KILL/5 \
                --pidfile $PIDFILE \
                --name $NAME
        rm -f $PIDFILE
        return "$?"
}

case "$1" in
start)
        echo "Starting Ventrilo Server."
        do_start
        echo "Ventrilo Server Started"
        ;;

stop)
        echo "Shutting Down Ventrilo Server."
        do_stop
        echo "Ventrilo Server Is Now Down"
        ;;

restart)
        echo "Restarting Ventrilo Server..."
        do_stop
        sleep 10
        do_start
        echo "Ventrilo Server Restarted"
        ;;

*)
        echo "Usage: $0 start|stop|restart"
        exit 1
        esac
        exit 0

        ;;
```

---

### Post by sir2u on 2010-12-17
Can you explain to me what exactly is broken about the original script?  It doesn't give output on a stop, start, etc and I can see you added that, but it still did the intended action.  

Are the instructions not clear enough?  I stated that I created a ventrilo user and where my working directory is, implying you should make note of those and modify the script accordingly.  Should I have explicitly stated to create a user called "ventrilo" and change the DAEMON=path to point to where the ventrilo binary is currently installed?

I'm trying to understand if 1) the script is really broken 2) my instructions were not clear enough and/or 3) you didn't read the post in its entirety and just copy/pasted the code.

---

