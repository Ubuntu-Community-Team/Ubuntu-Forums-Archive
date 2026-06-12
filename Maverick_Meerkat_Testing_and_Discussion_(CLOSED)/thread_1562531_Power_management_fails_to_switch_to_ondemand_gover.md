---
title: "Power management fails to switch to ondemand governor"
date: 2010-08-27
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by Devport on 2010-08-27
Since I switched to maverick weeks ago ( update from lucid ) when booting the power management switches to the ondemand governor randomly only ( e.g. at most every second time on average ) - at the other times the cpu stays in performance mode wasting lots of power and forcing me to manually switch the governor all the time.

Anybody else experiencing it ? How can I find the cause / where is the governor switch done when the boot sequence is done ?

---

### Post by mc4man on 2010-08-28
The only install I have pre A1 is a desktop which doesn't use scaling, my laptop install (A2) is fine in that regard.
the switch from performance to ondemand is thru a script in /etc
(/etc/init.d/ondemand
where the default is to wait 60 secs before switching.

Have seen posts where ondemand is never set, not like you've described
- are you waiting 60 secs to see if ondemand kicks in?
You could try lowering the sleep time a bit, 60 secs is more than most newer setups need, though if the command is truly never run on some boots can't see why that would help.

This is the script as seen here though ignore the blue section (i edited that in to set the up_theshold to a lower value which suits my use better than the default of 95
```

#! /bin/sh
### BEGIN INIT INFO
# Provides:          ondemand
# Required-Start:    $remote_fs $all
# Required-Stop:
# Default-Start:     2 3 4 5
# Default-Stop:
# Short-Description: Set the CPU Frequency Scaling governor to "ondemand"
### END INIT INFO


PATH=/sbin:/usr/sbin:/bin:/usr/bin

. /lib/init/vars.sh
. /lib/lsb/init-functions

case "$1" in
    start)
    	start-stop-daemon --start --background --exec /etc/init.d/ondemand -- background
        ;;
    background)
	sleep 60 # probably enough time for desktop login

	for CPUFREQ in /sys/devices/system/cpu/cpu*/cpufreq/scaling_governor
	do
		[ -f $CPUFREQ ] || continue
		echo -n ondemand > $CPUFREQ
	done

	[COLOR="Blue"]for CPU_THRESHOLD in /sys/devices/system/cpu/cpufreq/ondemand/up_threshold
	do
		[ -f $CPU_THRESHOLD ] || continue
		echo -n 70 > $CPU_THRESHOLD
	done[/COLOR]
	;;
    restart|reload|force-reload)
        echo "Error: argument '$1' not supported" >&2
        exit 3
        ;;
    stop)
        ;;
    *)
        echo "Usage: $0 start|stop" >&2
        exit 3
        ;;
esac
```

otherwise I guess you could look thru your various logs in /var/log, though I've never seen anything specific to this

---

### Post by Devport on 2010-08-28
**Thanks for your help. This is all I need to know to fix it. Marking as SOLVED.**

Side notes :

I waited minutes for it to switch to ondemand which it didn't. On an other occasion I already wondered why I do have a running bash and a sleep command which wont terminate after a clean start to the desktop. For some reason the script seems to hang every now and then on my system... Strange since the script is pretty simple - but I actually had 3 services being run incorrectly / occasionally after my update to Maverick - 2 of them are working fine now and I will fix ondemand.

---

