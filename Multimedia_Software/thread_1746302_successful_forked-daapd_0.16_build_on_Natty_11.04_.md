---
title: "successful forked-daapd 0.16 build on Natty 11.04 Server"
date: 2011-05-01
forum: Multimedia Software
---

### Post by rsjaffe on 2011-05-01
This is the result of reading lots of advice on this forum and elsewhere--thought I'd put it into one post for people's convenience.

Picked up the latest tarball at [http://alioth.debian.org/~jblache/forked-daapd/]("http://alioth.debian.org/~jblache/forked-daapd/"). Unpacked the tarball with [FONT="Lucida Console"]**tar -zxvf nameofball.tar.gz**[/FONT].

Loaded the following packages that it depended on: [FONT="Lucida Console"]**sudo apt-get install build-essential libtagc0-dev gperf libunistring-dev pkg-config zlib1g-dev  libconfuse-dev libavahi-client-dev libsqlite3-dev libavcodec-dev libavformat-dev libswscale-dev libmxml-dev libevent-dev libavl-dev libantlr3c-dev libgcrypt11-dev libflac-dev libogg-dev libtagc0-dev libasound2-dev**[/FONT] .

Ran [FONT="Lucida Console"]**./configure --prefix=/usr --sysconfdir=/etc --localstatedir=/var --enable-flac --enable-musepack**[/FONT]. Fix any errors that show up by tracking down a dependency that I hadn't listed above. Keep on running until it has no errors.

Then [FONT="Lucida Console"]**make; sudo make install**[/FONT]. I had installed checkinstall, so I ran [FONT="Lucida Console"]**make; sudo checkinstall -D**[/FONT] instead.

Then to set up the system:
```

#make an init.d script (the script I used is at the end of this post)
sudo -e /etc/init.d/forked-daapd 
sudo chmod +x /etc/init.d/forked-daapd
sudo update-rc.d forked-daapd defaults
#edit forked-daapd.conf as needed. All I had to do was change the directory to index
sudo -e /etc/forked-daapd.conf
#make sure all music has 755 privilege
#chmod the music as necessary
sudo adduser daapd
sudo mkdir /var/cache/forked-daapd
sudo chown daapd /var/cache/forked-daapd
sudo /etc/init.d/forked-daapd start
#and you're done! hopefully

```

Below is the init.d script I used.

```

#! /bin/sh

### BEGIN INIT INFO
# Provides:          forked-daapd
# Required-Start:    $local_fs $remote_fs $network $time avahi
# Required-Stop:     $local_fs $remote_fs $network $time
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: media server with support for RSP, DAAP, DACP and AirTunes
# Description:       forked-daapd is an iTunes-compatible media server for
#                    sharing your music library over the local network with RSP
#                    clients like the SoundBridge from Roku and DAAP clients like
#                    iTunes. It can also stream music to AirTunes devices.
### END INIT INFO

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DAEMON=/usr/sbin/forked-daapd
NAME=forked-daapd
DESC="RSP and DAAP media server"

test -x $DAEMON || exit 0

PIDFILE=/var/run/$NAME.pid

set -e

running_pid()
{
    # Check if a given process pid's cmdline matches a given name
    pid=$1
    name=$2
    [ -z "$pid" ] && return 1
    [ ! -d /proc/$pid ] &&  return 1
    cmd=`cat /proc/$pid/cmdline | tr "\000" "\n"|head -n 1 |cut -d : -f 1`
    # Is this the expected child?
    [ "$cmd" != "$name" ] &&  return 1
    return 0
}

running()
{
# Check if the process is running looking at /proc
# (works for all users)

    # No pidfile, probably no daemon present
    [ ! -f "$PIDFILE" ] && return 1
    # Obtain the pid and check it against the binary name
    pid=`cat $PIDFILE`
    running_pid $pid $DAEMON || return 1
    return 0
}

force_stop() {
# Forcefully kill the process
    [ ! -f "$PIDFILE" ] && return
    if running ; then
        kill -15 $pid
        # Is it really dead?
        if running ; then
            kill -9 $pid
            if running ; then
                echo "Cannot kill $NAME (pid=$pid)!"
                exit 1
            fi
        fi
    fi
    rm -f $PIDFILE
    return 0
}

case "$1" in
  start)
        echo -n "Starting $DESC: "
        start-stop-daemon --start --quiet --pidfile $PIDFILE \
            --exec $DAEMON -- $DAEMON_OPTS
        if running ; then
            echo "$NAME."
        else
            echo " ERROR."
        fi
        ;;
  stop)
        echo -n "Stopping $DESC: "
        start-stop-daemon --oknodo --stop --quiet --pidfile $PIDFILE \
            --exec $DAEMON
        echo "$NAME."
        ;;
  force-reload)
        start-stop-daemon --stop --test --quiet --pidfile \
            /var/run/$NAME.pid --exec $DAEMON \
            && $0 restart \
            || exit 0
        ;;
  restart)
    echo -n "Restarting $DESC: "
        start-stop-daemon --stop --quiet --pidfile \
            /var/run/$NAME.pid --exec $DAEMON
        start-stop-daemon --start --quiet --pidfile \
            /var/run/$NAME.pid --exec $DAEMON -- $DAEMON_OPTS
        echo "$NAME."
        ;;
  status)
    echo -n "$NAME is "
    if running ;  then
        echo "running"
    else
        echo " not running."
        exit 1
    fi
    ;;
  *)
    N=/etc/init.d/$NAME
    echo "Usage: $N {start|stop|restart|force-reload|status}" >&2
    exit 1
    ;;
esac

exit 0

```

---

### Post by rsjaffe on 2011-05-13
Just replaced the init.d script with an upstart script. The following is the upstart script I used (placed in /etc/init/forked-daapd.conf):
 
```

# forked-daapd daemon
 
description "forked-daapd service"
author "rsjaffe"
 
start on (filesystem and runlevel [2345])
stop on runlevel [!2345]
 
exec /usr/sbin/forked-daapd -f

```

---

### Post by Neonightmare on 2011-05-16
Hi, thx for the Tutorial.. I will try this on my own and report the result..


Is it possible to make a *.deb or to integrate daapd-forked into the packaging-system for natty?

[https://launchpad.net/ubuntu/+source/forked-daapd]("https://launchpad.net/ubuntu/+source/forked-daapd")

I posted a question there, but no result till now.

THX Neo

---

### Post by rsjaffe on 2011-05-17
> **Neonightmare said:**
> Hi, thx for the Tutorial.. I will try this on my own and report the result..


Is it possible to make a *.deb or to integrate daapd-forked into the packaging-system for natty?

[https://launchpad.net/ubuntu/+source/forked-daapd]("https://launchpad.net/ubuntu/+source/forked-daapd")

I posted a question there, but no result till now.

THX Neo
I used [FONT="Fixedsys"]checkinstall [/FONT]rather than [FONT="Fixedsys"]make install[/FONT], so did produce a deb (at least for 64 bit systems). 

UPDATE: I checked into this a bit more and fixed the dependencies list in the deb file. This file may be sufficient to install forked-daapd on 11.04 amd64 systems. YMMV. Files downloaded before 18-5-2011 18:10 PDT (GMT-7) will not have the proper dependencies list.

---

### Post by Neonightmare on 2011-05-20
i don't have an AMD64, so I can't try your package, but thank you for the help.

Here some news abaout packaging..

[https://bugs.launchpad.net/ubuntu/+source/forked-daapd/+bugs?field.status:list=NEW](https://bugs.launchpad.net/ubuntu/+source/forked-daapd/+bugs?field.status:list=NEW)

mayby you can help there...

THX Neo

---

### Post by rsjaffe on 2011-05-23
Update: changed upstart init file to account for the dependencies noted in the forked-daapd readme. forked-daapd also depends on NTP, but since that still uses the old SysV init style, couldn't check on it unless I changed the way NTP starts.

```


# forked-daapd daemon
description "forked-daapd service"
author "Rory Jaffe <rjaffe@gmail.com>"

start on (filesystem and (runlevel [2345] and (net-device-up IFACE!=lo and started avahi-daemon)))
stop on runlevel [!2345]

exec /usr/sbin/forked-daapd -f

```

---

### Post by sashxp on 2011-09-13
i can't compile forked v0.19 - i think  that i stuck tith the antl3r things.
Is it possible to get a working v19 .deb from someone who hast compiled it?

thanks!

sash

---

### Post by Rezista on 2012-05-22
Hi all,
I use forked-daapd a lot (I have an airport express and numerous iOS devices as remotes around the house) and lately have taken a liking to internet radio.

I made some changes to forked-daapd so it now supports some internet radio stations and even sends the song name + artist to the remote iOS devices.

Note that this change only works with sending internet radio to the airport express + local sound card. 

Let me know if you would like a copy. I have emailed the author (Julien Blache) and hopefully the changes will make their way in :)

---

