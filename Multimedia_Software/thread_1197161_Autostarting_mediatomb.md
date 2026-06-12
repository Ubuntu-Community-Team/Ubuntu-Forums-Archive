---
title: "Autostarting mediatomb"
date: 2009-06-25
forum: Multimedia Software
---

### Post by 98cwitr on 2009-06-25
cliffs:
mediatomb works great when run from terminal...everything loads exactly right
having problem with autostart
I just want to turn the computer on and off without any input devices and monitor and have it work
I don't want to leace my machine on 24-7
I am currently at my wits end

when you cant get your answers from Google, come here...right? :)

Few days ago I setup a media server using ubuntu 9.04 desktop. To make a long post short*er*, I was able to autostart mediatomb two days ago, but cannot now. Server is set for autologon underneath my profile [brett]. Here are my config.xml (both etc/mediatomb, etc/defaults/mediatomb, and etc/init.d/mediatomb files:

> 

<?xml version="1.0" encoding="UTF-8"?>
<config version="1" xmlns="http://mediatomb.cc/config/1" xmlnssi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://mediatomb.cc/config/1 http://mediatomb.cc/config/1.xsd">
<server>
<ui enabled="yes">
<accounts enabled="no" session-timeout="30">
<account user="mediatomb" password="mediatomb"/>
</accounts>
</ui>
<name>MediaTomb</name>
<udn>uuid:6556ae80-64c9-4054-99d2-cea1b84d6fc9</udn>
<home>/home/csk/.mediatomb</home>
<webroot>/usr/share/mediatomb/web</webroot>
<storage>
<sqlite3 enabled="yes">
<database-file>mediatomb.db</database-file>
</sqlite3>
<mysql enabled="no">
<host>localhost</host>
<username>mediatomb</username>
<database>mediatomb</database>
</mysql>
</storage>
<protocolInfo extend="yes"/><!-- For PS3 support change to "yes" -->
<!--
Uncomment the lines below to get rid of jerky avi playback on the
DSM320 or to enable subtitles support on the DSM units
-->

<custom-http-headers>
<add header="X-User-Agent: redsonic"/>
</custom-http-headers>

<manufacturerURL>redsonic.com</manufacturerURL>
<modelNumber>105</modelNumber>

<!-- Uncomment the line below if you have a Telegent TG100 -->
<!--
<upnp-string-limit>101</upnp-string-limit>
-->
</server>
<import hidden-files="no">
<scripting script-charset="UTF-8">
<common-script>/usr/share/mediatomb/js/common.js</common-script>
<playlist-script>/usr/share/mediatomb/js/playlists.js</playlist-script>
<virtual-layout type="builtin">
<import-script>/usr/share/mediatomb/js/import.js</import-script>
</virtual-layout>
</scripting>
<mappings>
<extension-mimetype ignore-unknown="no">
<map from="avi" to="video/x-divx"/>
<map from="divx" to="video/x-divx"/>

<map from="mp3" to="audio/mpeg"/>
<map from="ogg" to="application/ogg"/>
<map from="asf" to="video/x-ms-asf"/>
<map from="asx" to="video/x-ms-asf"/>
<map from="wma" to="audio/x-ms-wma"/>
<map from="wax" to="audio/x-ms-wax"/>
<map from="wmv" to="video/x-ms-wmv"/>
<map from="wvx" to="video/x-ms-wvx"/>
<map from="wm" to="video/x-ms-wm"/>
<map from="wmx" to="video/x-ms-wmx"/>
<map from="m3u" to="audio/x-mpegurl"/>
<map from="pls" to="audio/x-scpls"/>
<map from="flv" to="video/x-flv"/>
<!-- Uncomment the line below for PS3 divx support -->
<!--<map from="avi" to="video/divx"/> -->
<!-- Uncomment the line below for D-Link DSM / ZyXEL DMA-1000 -->
<!-- <map from="avi" to="video/avi"/> -->
</extension-mimetype>
<mimetype-upnpclass>
<map from="audio/*" to="object.item.audioItem.musicTrack"/>
<map from="video/*" to="object.item.videoItem"/>
<map from="image/*" to="object.item.imageItem"/>
</mimetype-upnpclass>
<mimetype-contenttype>
<treat mimetype="video/x-divx" as="avi"/>

<treat mimetype="audio/mpeg" as="mp3"/>
<treat mimetype="application/ogg" as="ogg"/>
<treat mimetype="audio/x-flac" as="flac"/>
<treat mimetype="image/jpeg" as="jpg"/>
<treat mimetype="audio/x-mpegurl" as="playlist"/>
<treat mimetype="audio/x-scpls" as="playlist"/>
<treat mimetype="audio/x-wav" as="pcm"/>
<treat mimetype="audio/L16" as="pcm"/>
<treat mimetype="video/x-msvideo" as="avi"/>
</mimetype-contenttype>
</mappings>
</import>
<transcoding enabled="yes">
<mimetype-profile-mappings>
<transcode mimetype="video/x-divx" using="video-thumbnail"/>
<transcode mimetype="application/ogg" using="audio-common"/>
<transcode mimetype="application/ogg" using="video-common"/>
<transcode mimetype="audio/x-flac" using="audio-common"/>
<transcode mimetype="video/x-flv" using="video-common"/>
</mimetype-profile-mappings>
<profiles>
<profile name="audio-common" enabled="yes" type="external">
<mimetype>audio/L16</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>no</accept-ogg-theora>
<agent command="mediatomb-transcode-audio" arguments="%in %out"/>
<buffer size="1048576" chunk-size="131072" fill-size="262144"/>
</profile>
<profile name="video-common" enabled="yes" type="external">



<mimetype>video/mpeg</mimetype>
<accept-url>yes</accept-url>
<first-resource>yes</first-resource>
<accept-ogg-theora>yes</accept-ogg-theora>
<agent command="mediatomb-transcode-video" arguments="%in %out"/>
<buffer size="10485760" chunk-size="262144" fill-size="524288"/>
</profile>

<profile name="video-thumbnail" enabled="yes" type="external">
<mimetype>image/jpeg</mimetype>
<accept-url>yes</accept-url>
<thumbnail>yes</thumbnail>
<resolution>128x128</resolution>
<agent command="ffmpegthumbnailer" arguments="-i %in -o %out -s 128"/>
<buffer size="524288" chunk-size="512" fill-size="1024"/>
</profile>

</profiles>
</transcoding>
</config>
Both the etc/mediatomb and ~/.mediatomb config files match...and I do not have any trouble running mediatomb once I issue the command to start it from terminal. 

> 
# Defaults for MediaTomb initscript
# sourced by /etc/init.d/mediatomb
# installed at /etc/default/mediatomb by the maintainer scripts

#
# This is a POSIX shell fragment
#

# Set whether the daemon should be started. Set this value to anything
# but 'yes' to enable the daemon
NO_START="no"

# Additional options that are passed to the daemon.
OPTIONS=""

# The network interface for MediaTomb to bind to and for which the multicast
# routing entry should be added; "" if the route shouldn't be added at all.
# For example: INTERFACE="eth0"
INTERFACE="Auto eth0"

# The route command and arguments to be used if INTERFACE is defined.
# These variables should normally be left unmodified.
ROUTE_ADD="/sbin/route add -net 239.0.0.0 netmask 255.0.0.0"
ROUTE_DEL="/sbin/route del -net 239.0.0.0 netmask 255.0.0.0"

# The user and group that MediaTomb should be run as.
USER="MEDIATOMB"
GROUP="MEDIATOMB"
and lastly...the script I got from a search and suggestion for the DARGS value

> 
#! /bin/sh
#
# MediaTomb initscript
#
# Original Author: Tor Krill <tor@excito.com>.
# Modified by: Leonhard Wimmer <leo@mediatomb.cc>
#
#

### BEGIN INIT INFO
# Provides: mediatomb
# Required-Start: $all
# Required-Stop: $all
# Should-Start: $all
# Should-Stop: $all
# Default-Start: 2 3 4 5
# Default-Stop: 0 1 6
# Short-Description: upnp media server
### END INIT INFO


set -e

PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
DESC="upnp media server"
NAME=mediatomb
DAEMON=/usr/bin/$NAME
PIDFILE=/var/run/$NAME.pid
SCRIPTNAME=/etc/init.d/$NAME
USER=mediatomb
GROUP=mediatomb
LOGFILE=/var/log/mediatomb
HOME=/home/brett/.mediatomb

# Read config file if it is present.
if [ -r /etc/default/$NAME ]
then
. /etc/default/$NAME
fi

# if NO_START is set, exit gracefully
[ "$NO_START" = "yes" ] && exit 0

D_ARGS="-c /etc/mediatomb/config.xml -d -u $USER -g $GROUP -P $PIDFILE -l $LOGFILE -m /etc"

if [ "$INTERFACE" != "" ] ; then
D_ARGS="$D_ARGS -e $INTERFACE"
fi



# Gracefully exit if the package has been removed.
test -x $DAEMON || exit 0

#
# Function that starts the daemon/service.
#
d_start() {
touch $PIDFILE
chown $USER:$GROUP $PIDFILE
touch $LOGFILE
chown $USER:$GROUP $LOGFILE
start-stop-daemon --start --quiet --pidfile $PIDFILE \
--exec $DAEMON -- $D_ARGS $DAEMON_OPTS
}

#
# Function that stops the daemon/service.
#
d_stop() {
start-stop-daemon --stop --signal 2 --retry 5 --quiet --pidfile $PIDFILE \
--name $NAME
rm $PIDFILE
}

#
# Function that sends a SIGHUP to the daemon/service.
#
d_reload() {
start-stop-daemon --stop --quiet --pidfile $PIDFILE \
--name $NAME --signal 1
}

case "$1" in
start)
echo -n "Starting $DESC: $NAME"
if [ "$INTERFACE" != "" ] ; then
# try to add the multicast route
/sbin/route add -net 239.0.0.0 netmask 255.0.0.0 $INTERFACE >/dev/null 2>&1 || true
fi
d_start
echo "."
;;
stop)
echo -n "Stopping $DESC: $NAME"
d_stop
echo "."
;;
reload|force-reload)
echo -n "Reloading $DESC configuration..."
d_reload
echo "done."
;;
restart)
#
# If the "reload" option is implemented, move the "force-reload"
# option to the "reload" entry above. If not, "force-reload" is
# just the same as "restart".
#
echo -n "Restarting $DESC: $NAME"
d_stop
sleep 1
d_start
echo "."
;;
*)
# echo "Usage: $SCRIPTNAME {start|stop|restart|reload|force-reload}" >&2
echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
exit 1
;;
esac

exit 0
Things I have tried include:

[LIST]
[*]System->Preferences->Startup Applications and using a variety of different paths and commands...nothing works
[*]creating a shell script with the contents "mediatomb" or "mediatomb -d" and loading it in via sudo update-rc.d *scriptname* defaults
[*]Checked the rc0.d dir to make sure all the links for mediatomb were there and had been created
[*]ensuring the mediatomb files listed above had the correct permissions
[LIST]
[*]chmod 0755
[*]chmod +rw
[*]chmod +x
[/LIST]
 
[/LIST]

What do I need to change? Thanks for the help boys and girls!

---

### Post by 98cwitr on 2009-06-26
anybody?

---

### Post by 98cwitr on 2009-06-27
:-k

---

### Post by 98cwitr on 2009-06-29
:-k :-k

---

### Post by Mugwug on 2009-06-30
I'm relatively new to this and have only recently been able to get MediaTomb to run properly on my system, however I had exactly the same problem. I needed to "sudo mediatomb" after each reboot.

I initially added mediatomb to the startup list (System->Preferences->Startup Applications) giving it the command "sudo mediatomb".

I then added my username to the sudoers file, for mediatomb,

USERNAME ALL=NOPASSWD: /usr/bin/mediatomb
(I'm not 100% if this was the precise format)

This allows mediatomb to be run as root at startup and seems to function fine on my machine.

YMMV, and there is probably a more elegant solution to this, but I'm still learning my way around Ubuntu.

---

### Post by 98cwitr on 2009-07-01
well i dont have to use sudo command to run mediatomb, so I essentially tried the same thing by adding a startup command of 'mediatomb' to the list...still didnt work. :/

---

### Post by 98cwitr on 2009-07-02
makes me think there is something wrong with the OS when the startup apps that I created dont seem to work :/

Ok, so check this one out...

last entry in my startup command textbox was /etc/init.d/mediatomb start when I ran this, i got something to the effect of invalid user 'MEDIATOMB:MEDIATOMB' so I changed it back like I had it to plain mediatomb

then added this 

> or a &#8220;headless&#8221; server where you can't log in, try this workaround: edit file /etc/network/interfaces adding these 2 lines:

auto eth0

iface eth0 inet dhcp

then did this

> Please note the following if using this method:

As soon as you save changes to /etc/network/interfaces, your ethernet port will become disabled. So make sure you are logged in via the physical console (not ssh or telnet) when editing!
After your edit is complete, you must run /etc/init.d/networking restart to re-enable your ethernet.
Network Manager will report that your network is manually configured. This shouldn't be a problem for most people.

Lastly, I changed the user:group from MEDIATOMB:MEDIATOMB to brett:brett (me) in the etc/default/mediatomb and the etc/init.d/mediatomb files

I don't know which step worked...but it's back running now. Now if I could only get it to load without having to have auto logon turned on I'd be set.

---

### Post by oxymoron on 2009-07-07
I had this problem, converting to debian lenny on my server fixed it though! I just think its a bug in ubuntu, maybe a new release will fix it.

---

### Post by reckik on 2010-01-08
I'm not sure if this is what u mean but what about just running mediatomb starting up in a terminal?

i added the following command in preferences>startup items

gnome-terminal -e mediatomb

and mediatomb starts up fine here.. although there is an the gnome terminal to close everytime

---

### Post by 98cwitr on 2010-02-07
didnt use the gnome-terminal command, that could have been the problem. Mediatomb was giving me lag problems though, switched to using a Windows machine against my better judgement and just using my Linux box for the downloads and transferring later. I should try it on 9.10 and see what happens, just dont have the time at the moment.

---

### Post by buntunoob on 2010-02-12
try this, its from [http://mediatomb.cc/dokuwiki/faq:faq](http://mediatomb.cc/dokuwiki/faq:faq)
it starts it later
 
sudo update-rc.d -f mediatomb remove 
sudo update-rc.d mediatomb defaults 99

---

### Post by hmuenz on 2010-08-19
I've had the same problem with Ubuntu 10.04 and mediatomb. The hint posted by buntunoob (from mediatomb's wiki) didn't work either. It's the result of Ubuntu's effords to speed up system start. The mediatomb daemon doesn't start if the network interface isn't already up and configured. So sometimes, if the network interface is configured fast enough, it will start at boottime - and sometimes it won't.  That's bad, if you don't want to login and start mediatomb manually before you can watch movies or listen to music.

To fix this problem, I have written a small script to be executed by /etc/rc.local. It first will check, if mediatomb is already running. If not, it will wait, until the network interface is up and then start the mediatomb daemon. Here is the code:
```

#!/bin/sh
# check-mediatomb.sh
# This script checks, if the mediatomb-daemon has started regularly while boot-up.
# If not, it will be started delayed after the network interface is up.
#
# IP-address to check if the network interface is already up
PING_IP="10.0.2.2"
# How many seconds do we want to wait before checking again?
SLEEP_TIME=3 
#
if test -f /var/run/mediatomb.pid ; then
    logger -s $(date)": mediatomb started regularly"
else
    while !(ping -c 1 $PING_IP); do
        sleep $SLEEP_TIME
    done
    /etc/init.d/mediatomb start
    logger -s $(date)": mediatomb started delayed"
fi
exit 0

```
[LIST]
[*]Copy this to a file (e.g. /usr/local/bin/check-mediatomb.sh) and set the executable flag.
[*]customize the PING_IP varable to any IP-address or url which should be reachable by your computer (e.g. your router's IP-address).
[*]edit /etc/rc.local and add the following line:
/usr/local/bin/check-mediatomb.sh &
[*]Have fun!
[/LIST]
Now you should be able to access your media server without having to start it manually. 

Maybe you will first have to delete (or rename) the ~/.mediatomb directory. On my computer, mediatomb cannot be started by the init system, if there is a .mediatomb folder in my $HOME directory.

Regards
Heiner

---

### Post by rebeltaz on 2010-09-30
I have tried EVERYTHING posted here and I still have to run 'sudo /etc/init.d/mediatomb start' in a terminal to get it to run... Any thing else I can try?

EDIT:
[COLOR="Red"]I found that if you add 'sleep 60' to the beginning of the "do_start" section of the /etc/init.d/mediatomb file, the script will wait for 60 seconds before starting, giving the network enough time to fully load. Mediatomb then loads automatically by itself...
[/COLOR]

---

### Post by 98cwitr on 2010-10-05
yeah I quit using mediatomb last year and went to Java Media Server

[https://help.ubuntu.com/community/Ps3MediaServer](https://help.ubuntu.com/community/Ps3MediaServer)

havent looked back.

---

### Post by bentkarma on 2010-10-22
Have you tried going into users and groups and adding yourself to the group for mediatomb?

---

### Post by 98cwitr on 2010-10-23
> **bentkarma said:**
> Have you tried going into users and groups and adding yourself to the group for mediatomb?

Yeah, that was done at the time. Again, PS3 Media Server is a lot better imho.

---

### Post by rebeltaz on 2010-10-23
I tried PMS before I used MediaTomb and IMHO MT is way better...

---

### Post by comthre3 on 2011-05-03
I've tried everything in this thread too,, with nothing can someone post a solution please? I used to use uShare and was happy with it, until i upgraded to Natty and everything stopped working again. 

any help would be greatly appreciated 

Thanks

---

### Post by tokyo-joe on 2012-05-26
I was having the same issue but resolved it!

See this article for network drive mounting on openSUSE.
[http://opensuse.swerdna.org/susesambacifs.html#slow](http://opensuse.swerdna.org/susesambacifs.html#slow)

When you want to start something that requires a superuser privilege after some delay at boot, try this

```
sudo crontab -e

```
Add the following line in crontab.
```
@reboot sleep 20;service mediatomb start
```

"@reboot" means this is done at every boot. "sleep XX" means it waits for 20 seconds before performing the following command.

This worked for my Ubuntu 11.04 system.

---

