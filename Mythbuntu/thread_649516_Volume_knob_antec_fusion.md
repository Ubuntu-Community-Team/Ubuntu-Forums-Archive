---
title: "Volume knob antec fusion"
date: 2007-12-25
forum: Mythbuntu
---

### Post by axelsvag on 2007-12-25
Now when I got a few days free during the holiday (don´t tell my wife) I wnat to get my volume knob to work. I looked in this tutorial [http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion]("http://www.mythtv.org/wiki/index.php/Volume_Knob_on_Antec_Fusion").

There is a few this I have questions about in that tutorial.

At first everythin is crystal clear and I can recognize the steps in my installation.  I can find the idVendor by lsusb
1. But then In the text it says ```
Following this thread, I added these lines into /etc/lircd.conf 
``` In my mythbuntu the folder is /etc/lirc/lircd.conf or am I in the wrong folder messing around?

2. Then it says ```
Edit /etc/init.d/lircd

``` but in my folder ther is just a /etc/init.d/lirc not a lircd

3. Now to the really odd thing In the text it says that I should edit the lircd ```
Replace the line 

daemon lircd $LIRCD_OPTIONS
with these two lines 

lircd $LIRCD1_OPTIONS
lircd $LIRCD_OPTIONS
And add after the line 

killproc lircd
another line that reads 

killproc lircd1

```

But I can´t find any text that looks like that at all in my file. That makes me suspicious that I am in the completely wrong folder. 

Can anyone help me to get me on the right track again? And save me from more cleaning in the house (my wifes order).

---

### Post by foxbuntu on 2007-12-26
1) /etc/lirc/lircd.conf is correct
2) /etc/init.d/lirc is also correct

use those and the rest of the Wiki seems correct

---

### Post by axelsvag on 2007-12-27
Thank you for your support but I can´t seem to find the line ```
daemon lircd $LIRCD_OPTIONS
``` in the /etc/init.d/lirc  so what should I delete and what should I insert?

---

### Post by axelsvag on 2007-12-29
> **axelsvag said:**
> Thank you for your support but I can´t seem to find the line ```
daemon lircd $LIRCD_OPTIONS
``` in the /etc/init.d/lirc  so what should I delete and what should I insert?

I search and search but my /etc/init.d/lirc looks like this no sign of any killproc or LIRCD_OPTIONS or am I blind?
```
#! /bin/sh
### BEGIN INIT INFO
# Provides:          lirc
# Required-Start:    $syslog
# Required-Stop:     $syslog
# Should-Start:      $local_fs
# Should-Stop:       $local_fs
# Default-Start:     2 3 4 5
# Default-Stop:      0 1 6
# Short-Description: Starts LIRC daemon.
# Description:       LIRC is used to control different
#                    infrared receivers and transceivers.
### END INIT INFO


load_modules ()
{
	local MODULES_MISSING=false

	for mod in $*
	do
		modprobe -k $mod 2> /dev/null || MODULES_MISSING=true
	done

	if $MODULES_MISSING; then
		echo "#####################################################"
		echo "## I couldn't load the required kernel modules     ##"
		echo "## You should install lirc-modules-source to build ##"
		echo "## kernel support for your hardware.               ##"
		echo "#####################################################"
		echo "## If this message is not appropriate you may set  ##"
		echo "## LOAD_MODULES=false in /etc/lirc/hardware.conf   ##"
		echo "#####################################################"
		START_LIRCMD=false
		START_LIRCD=false
	fi

	if test -x /sbin/udevsettle && [ ! -z $3 ] && [ $3 != "udev" ];
	then
		if ! /sbin/udevsettle; then
		  echo "timeout waiting for devices to be ready"
		fi
	fi
}

build_args ()
{
	local ARGS="$*"
	
    ## Try to find an lirc device.
    ## udev uses /dev/lirc0
    ## static dev uses /dev/lirc
    ## devfs uses /dev/lirc/0
    if [ -z "$DEVICE" ]; then
    	for dev in /dev/lirc0 /dev/lirc /dev/lirc/0; do
	    	if [ -c $dev ]; then
				DEVICE="$dev"
				break
			fi
		done
	fi
	
	if [ -n "$DEVICE" ] && [ "$DEVICE" != "none" ]; then
		ARGS="--device=$DEVICE $ARGS"
	fi
	if [ -n "$DRIVER" ] && [ "$DRIVER" != "none" ]; then
		ARGS="--driver=$DRIVER $ARGS"
	fi
	echo $ARGS
}

test -f /usr/sbin/lircd || exit 0
test -f /usr/sbin/lircmd || exit 0
#test -f /etc/lirc/lircd.conf || exit 0
#test -f /etc/lirc/lircmd.conf || exit 0

START_LIRCMD=true
START_LIRCD=true

if [ ! -f /etc/lirc/lircd.conf ] \
	|| grep -q "^#UNCONFIGURED"  /etc/lirc/lircd.conf;then
	if [ "$1" = "start" ]; then
          echo "##################################################"
          echo "## LIRC IS NOT CONFIGURED                       ##"
          echo "##                                              ##"
          echo "## read /usr/share/doc/lirc/html/configure.html ##"
          echo "##################################################"
	fi
	START_LIRCD=false
	START_LIRCMD=false
fi
if [ ! -f /etc/lirc/lircmd.conf ] \
	|| grep -q "^#UNCONFIGURED" /etc/lirc/lircmd.conf;then
	START_LIRCMD=false
fi

if [ -f /etc/lirc/hardware.conf ];then
	. /etc/lirc/hardware.conf
fi


case "$1" in
  start)
    if [ "$LOAD_MODULES" = "true" ] && [ "$START_LIRCD" = "true" ]; then
	load_modules $MODULES
    fi
    echo -n "Starting lirc daemon:"
    if $START_LIRCD; then
      echo -n " lircd"
      LIRCD_ARGS=`build_args $LIRCD_ARGS`
      start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS \
		< /dev/null
    fi
    if $START_LIRCMD; then
      echo -n " lircmd"
      start-stop-daemon --start --quiet --exec /usr/sbin/lircmd \
      		< /dev/null
    fi
    echo "."
    ;;
  stop)
    echo -n "Stopping lirc daemon:"
    echo -n " lircmd"
    start-stop-daemon --stop --quiet --exec /usr/sbin/lircmd
    echo -n " lircd"
    start-stop-daemon --stop --quiet --exec /usr/sbin/lircd
    echo "."
    ;;
  reload|force-reload)
    if $START_LIRCD; then
      start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircd
    fi
    if $START_LIRCMD; then
      start-stop-daemon --stop --quiet --signal 1 --exec /usr/sbin/lircmd
    fi
    ;;
  restart)
    $0 stop
    $0 start
    ;;
  *)
    echo "Usage: /etc/init.d/lircd {start|stop|reload|restart|force-reload}"
    exit 1
esac

exit 0
```

---

### Post by axelsvag on 2008-01-01
I have tried to find any solution around the net for a few days now. I suspect that the instruction for the volume knob is not suitable for ubuntu, or am I wrong. the text as you see in etc/init.d/lirc is completely different from the ubuntu style. So I grasp for a straw and ask if anyone with ubuntu installed got the volume knob to work? And if, what changes have they done in the system?  Or if somebody have some ideas how to convert the "daemon lircd $LIRCD_OPTIONS" and "killproc" into ubuntian?

---

### Post by erland on 2008-01-01
The following row:
```

start-stop-daemon --stop --quiet --exec /usr/sbin/lircd

```

Will result in that the lircd process is killed, so it is almost the same as "killproc lircd". 

The following row:
```

start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS

```
Is the one that does the same as the "lircd $LIRCD_OPTIONS" row, but as you see it will use $LIRCD_ARGS instead of  $LIRCD_OPTIONS.

The guide you refer to doesn't work straight away with the init.d scripts provided with Ubuntu. What you probably want to do is probably to replace the row that looks like this:
```

start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_ARGS

```

With something like this:
```

start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD_OPTIONS
start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- $LIRCD1_OPTIONS

```

This would correspond the the following rows in the guide:
```

lircd $LIRCD1_OPTIONS
lircd $LIRCD_OPTIONS

```

I think the stop rows in the guide that looks like this:
```

killproc lircd
killproc lircd1

```
Already will kill the process correctly with the line in the Mythbuntu init.d script that looks like this:
```

start-stop-daemon --stop --quiet --exec /usr/sbin/lircd

```

The principle with the editing of the init.d is that you want to start two lircd processes when you run "/etc/init.d/lircd start", one that is connected to /dev/lirc_imon and another one that is connected to /dev/lirc_mce. 

In the same way you want to make sure that both these processes are killed when you run "/etc/init.d/lircd stop".

To check which processes that are actually started, you can run:
```

ps aux|grep lircd

```

---

### Post by axelsvag on 2008-01-01
Thank you very much. Now I can continue with more confidence.

---

### Post by KjetilK on 2008-01-20
Thanks for this, it makes that much clearer, in particular that you need to run two separate lircd's. 

It doesn't quite work for me yet, though. 

I've set up the hardware.conf and edited the init.d script, and I think the lircd lines that are eventually launched looks like this:

```

start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- --driver=default --device=/dev/lirc_imon --output=/dev/lircd --pidfile=/var/run/lircd.pid --connect=localhost:8765
start-stop-daemon --start --quiet --exec /usr/sbin/lircd -- --driver=default --device=/dev/lirc_pvr --output=/dev/lircd1 --pidfile=/var/run/lircd1.pid --listen

```

I can't myself see anything wrong with these lines, except that I don't grok why one has --listen and the other has --connect. 

When I restart the server, according to ps, only one of them is running. 

I've tried running these manually in the terminal with the same result. Interestingly, it doesn't seem to matter which one I run first, only the first will be running when I run both according to ps.

If I run the line with --connect, the process will run, but I see in my syslog: 
Jan 20 21:18:26 tigger lircd-0.8.2[7433]: failure connecting to localhost
Jan 20 21:18:26 tigger lircd-0.8.2[7433]: Connection refused

Indeed, port 8765 is closed...

If I run the line with --listen, it clearly opens that port, but if I then launch the line with --connect, ps doesn't report afterwards that it is running, only the --listen line is reported as running. From what you wrote above, I would guess that's a Bad Sign. :-k

So, what's the final step I need here to make both running...?

---

### Post by RawMustard on 2008-01-25
I'm having problems getting two remotes working in gutsy also.  The lirc_streamzap remote and the Antec_Fusion_black Volume Knob.  The Streamzap runs just fine, but the Volume knob doesn't.  I can irrecord the knob and generate a successful lircd.conf file, but adding this to my existing /etc/lircd.conf file yields no results  in irw :(  I tried to connect directly to it as mentioned in the lirc docs by doing irw /dev/lirc1 but I get connection refused and refused if I do it using sudo.

It apears that the lirc_imon module is built into the kernel, because If I try and load it in my hardware.conf file, it fails at boot time.
So even though the module is loaded, I still need to tell lirc to use it right?

---

