---
title: "Teamspeak and possible solution?"
date: 2008-01-10
forum: Multimedia Production
---

### Post by ethernaly on 2008-01-10
Hi, at first sorry for my bad english, I try to do a search but sometimes I've problem with the translation.
So I decided to make a new 3d.

Well I'm a teamspeak user, and I've also a server.
With Ubuntu the server run greatly without crash! But the client have a big problem..
Infacts when I start Teamspeak, I can't hear the other application's sound.

For example if I want to tell in TS while I'm playing UrbanTerror, the TS's sound works, but UrT's sound doesn't work....

I try to install alsa-oss and I try to launch TS with:
```
aoss teamspeak
```

but the sound of TS i terrible, like a permanent LAG...

somebody knows a good solution?


thx a lot and sorry for my terrible english :D

---

### Post by kvonb on 2008-01-10
-

---

### Post by ethernaly on 2008-01-10
```
#!/bin/sh
### BEGIN INIT INFO
# Provides:          bootmisc
# Required-Start:    $local_fs hostname $remote_fs
# Required-Stop:     $local_fs
# Default-Start:     S
# Default-Stop:
# Short-Description: Miscellaneous things to be done during bootup.
# Description:
### END INIT INFO

PATH=/usr/sbin:/usr/bin:/sbin:/bin
[ "$DELAYLOGIN" ] || DELAYLOGIN=yes
. /lib/init/vars.sh

do_start () {
	#
	# If login delaying is enabled then create the flag file
	# which prevents logins before startup is complete
	#
	case "$DELAYLOGIN" in
	  Y*|y*)
		echo "System bootup in progress - please wait" > /var/lib/initscripts/nologin
		;;
	esac

	# Create /var/run/utmp so we can login.
	: > /var/run/utmp
	if grep -q ^utmp: /etc/group
	then
		chmod 664 /var/run/utmp
		chgrp utmp /var/run/utmp
	fi

	# Set pseudo-terminal access permissions.
	if [ ! -e /dev/.devfsd ] && [ -c /dev/ttyp0 ]
	then
		chmod -f 666 /dev/tty[p-za-e][0-9a-f]
		chown -f root:tty /dev/tty[p-za-e][0-9a-f]
	fi

	# Update motd
	uname -snrvm > /var/run/motd
	[ -f /etc/motd.tail ] && cat /etc/motd.tail >> /var/run/motd

	# Save kernel messages in /var/log/dmesg
	if which dmesg >/dev/null 2>&1
	then
		savelog -q -p -c 5 /var/log/dmesg
		dmesg -s 524288 > /var/log/dmesg
		chgrp adm /var/log/dmesg || :
	elif [ -c /dev/klog ]
	then
		savelog -q -p -c 5 /var/log/dmesg
		dd if=/dev/klog of=/var/log/dmesg &
		sleep 1
		kill $!
		[ -f /var/log/dmesg ] && { chgrp adm /var/log/dmesg || : ; }
	fi

	# Remove bootclean's flag files.
	# Don't run bootclean again after this!
	rm -f /tmp/.clean
}

case "$1" in
  start|"")
	do_start
	;;
  restart|reload|force-reload)
	echo "Error: argument '$1' not supported" >&2
	exit 3
	;;
  stop)
	# No-op
	;;
  *)
	echo "Usage: bootmisc.sh [start|stop]" >&2
	exit 3
	;;
esac

:
```
sorry this is my /etc/init.d/bootmisc.sh ... where I need to write that 2 lines?

the game is in /home/myname/Giochi/UrbanTerror/ioUrbanTerror.i386

after the addon I need to save and reboot my pc?

---

### Post by kvonb on 2008-01-10
-

---

### Post by kvonb on 2008-01-10
-

---

### Post by ethernaly on 2008-01-10
do I need something to do run this tips?

I insert the line...I save and I reboot my system, but nothing I can't hear the sound of the game :(

other suggestion?

---

### Post by kvonb on 2008-01-11
-

---

### Post by elderhail on 2008-01-11
Excuse for my english:

   The problem is in teamspeak not in game because this problem is present when use teamspeak indedendent other audio user. 

thank you:

   elderhail

---

### Post by kvonb on 2008-01-11
_-_

---

### Post by kvonb on 2008-01-11
_-_

---

### Post by ethernaly on 2008-01-11
sorry I come back home now :P

this is  cat /proc/asound/modules :
```
0 snd_hda_intel
 1 snd_usb_audio
 2 saa7134_alsa

```

this is the launcher from terminal:
```
cd Giochi/UrbanTerror/
./ioUrbanTerror.i386
```

the launcher in applications-->games have this command line:
```
/home/ethernaly/Giochi/UrbanTerror/ioUrbanTerror.i386
```

need something else?

thx a lot!

---

### Post by kvonb on 2008-01-11
-

---

