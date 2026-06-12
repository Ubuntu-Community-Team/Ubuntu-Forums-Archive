---
title: "pulseaudio script not working"
date: 2009-02-22
forum: Multimedia Software
---

### Post by mathfeel on 2009-02-22
I was investigating why I don't have sound and found that pulseaudio did not start at boot. So I checked:
```
~$ sudo /etc/init.d/pulseaudio start
~$ pgrep pulse
~$ aplay /usr/share/sounds/question.wav
ALSA lib pulse.c:272:(pulse_connect) PulseAudio: Unable to connect: Connection refused

aplay: main:583: audio open error: Connection refused
~$ pulseaudio -D
W: ltdl-bind-now.c: Failed to find original dlopen loader.
~$ aplay /usr/share/sounds/question.wav
Playing WAVE '/usr/share/sounds/question.wav' : Signed 16 bit Little Endian, Rate 44100 Hz, Mono
```

so pulseaudio is configured fine but some how /etc/init.d/pulseaudio cannot start pulseaudio for some reason and running pulseaudio -D from CLI would have activated pulseaudio correctly. I haven't touch that file at all:
```
$ cat /etc/init.d/pulseaudio 
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          pulseaudio esound
# Required-Start:    $remote_fs $syslog dbus
# Required-Stop:     $remote_fs $syslog dbus
# Should-Start:      dbus
# Should-Stop:       dbus
# Default-Start:     2 3 4 5
# Default-Stop:      1
# Short-Description: Start the PulseAudio sound server
# Description:       System mode startup script for
#                    the PulseAudio sound server.
### END INIT INFO

DAEMON=/usr/bin/pulseaudio
PIDFILE=/var/run/pulse/pid 
PATH=/sbin:/bin:/usr/sbin:/usr/bin

test -x $DAEMON || exit 0

. /lib/lsb/init-functions

PULSEAUDIO_SYSTEM_START=0
DISALLOW_MODULE_LOADING=1
test -f /etc/default/pulseaudio && . /etc/default/pulseaudio
test "$PULSEAUDIO_SYSTEM_START" != "1" && exit 0

pulseaudio_start () {
	log_begin_msg "Starting PulseAudio Daemon"
	start-stop-daemon -x $DAEMON -p $PIDFILE --start -- --system --daemonize --high-priority --log-target=syslog --disallow-module-loading=$DISALLOW_MODULE_LOADING
	if [ -e /var/run/pulse/.esd_auth ]; then
		chown pulse:pulse-access /var/run/pulse/.esd_auth
		chmod 640 /var/run/pulse/.esd_auth
	fi
	if [ -e /var/run/pulse/.pulse-cookie ]; then
		chown pulse:pulse-access /var/run/pulse/.pulse-cookie
		chmod 640 /var/run/pulse/.pulse-cookie
	fi
	log_end_msg $?
}

pulseaudio_stop () {
	log_begin_msg "Stopping PulseAudio Daemon"
	start-stop-daemon -p $PIDFILE --stop || echo -n "... pulseaudio is not running"
	log_end_msg $?
}

case "$1" in
	start|stop)
		pulseaudio_${1}
		;;
	restart|reload|force-reload)
		pulseaudio_stop
		pulseaudio_start
		;;
	force-stop)
		pulseaudio_stop
		killall pulseaudio || true
		sleep 2
		killall -9 pulseaudio || true
		;;
	*)
		echo "Usage: /etc/init.d/pulseaudio {start|stop|force-stop|restart|reload|force-reload}"
		exit 1
		;;
esac

exit 0
```

Anyone?

SOLVED: I guess I missed the memo on this one. PULSEAUDIO_SYSTEM_START is set to 0 in /etc/default/pulseaudio. Since I am not using GNOME, I have to start the daemon by myself.

---

