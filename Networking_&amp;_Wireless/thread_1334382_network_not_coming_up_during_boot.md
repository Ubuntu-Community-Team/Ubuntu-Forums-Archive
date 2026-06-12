---
title: "network not coming up during boot"
date: 2009-11-22
forum: Networking &amp; Wireless
---

### Post by satbunny on 2009-11-22
For various reasons I have problems with network manager, probably since Dell have an odd network card in my PC.

So I usually use static IPs and not Network Manager.

Foolishly I tried Network manager on 9.04 and it was flaky so I tried wicd and it was flaky, and so I am back to a static IP.

However, the network is not coming up during boot. It can be easily brought up with a 

> sudo /etc/init.d/networking restart

but that isn't what I want, especially since my fstab is full of CIFS shares that are failing.

So.. how can I log the bootup and see what is failing?
OR
What should I check..

Here is my /etc/network/interfaces file:

> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
#mapping hotplug
#        script grep
#        map eth0

# The primary network interface
auto eth0
iface eth0 inet static
        address 192.168.2.167
        netmask 255.255.255.0
        network 192.168.2.0
        broadcast 192.168.2.255
        gateway 192.168.2.1

My /etc/NetworkManager/nm-system-settings.conf is:

> 
[main]
plugins=ifupdown,keyfile

no-auto-default=00:1a:a0:9d:20:7b,

[ifupdown]
managed=false

Network Manager and WICD are NOT installed.

---

### Post by satbunny on 2009-11-23
bump

---

### Post by Iowan on 2009-11-23
Do you have */etc/rcS.d/S40networking*?

---

### Post by satbunny on 2009-11-25
Yes. It is a link to:

> ../init.d/networking


the contents of which are:

> #!/bin/sh -e
### BEGIN INIT INFO
# Provides:          networking
# Required-Start:    mountkernfs ifupdown $local_fs
# Required-Stop:     ifupdown $local_fs
# Default-Start:     S
# Default-Stop:      0 6
# Short-Description: Raise network interfaces.
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

[ -x /sbin/ifup ] || exit 0

. /lib/lsb/init-functions

# helper function to set the usplash timeout. [https://launchpad.net/bugs/21617](https://launchpad.net/bugs/21617)
usplash_timeout () {
	TIMEOUT=$1
	if [ -x /sbin/usplash_write ]; then
	    /sbin/usplash_write "TIMEOUT $TIMEOUT" || true
	fi
}

process_options() {
    [ -e /etc/network/options ] || return 0
    log_warning_msg "/etc/network/options still exists and it will be IGNORED! Read README.Debian of netbase."
}

check_network_file_systems() {
    [ -e /proc/mounts ] || return 0

    exec 9<&0 < /proc/mounts
    while read DEV MTPT FSTYPE REST; do
	case $DEV in
	/dev/nbd*|/dev/nd[a-z]*|/dev/etherd/e*)
	    log_warning_msg "not deconfiguring network interfaces: network devices still mounted."
	    exit 0
	    ;;
	esac
	case $FSTYPE in
	nfs|nfs4|smbfs|ncp|ncpfs|cifs|coda|ocfs2|gfs|pvfs|pvfs2|fuse.httpfs|fuse.curlftpfs)
	    log_warning_msg "not deconfiguring network interfaces: network file systems still mounted."
	    exit 0
	    ;;
	esac
    done
    exec 0<&9 9<&-
}

case "$1" in
start)
	process_options

	log_action_begin_msg "Configuring network interfaces"
	usplash_timeout 120
	if [ "$VERBOSE" != no ]; then
	    if ifup -a; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	else
	    if ifup -a >/dev/null 2>&1; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	fi
	usplash_timeout 15
	;;

stop)
	check_network_file_systems

	log_action_begin_msg "Deconfiguring network interfaces"
	if [ "$VERBOSE" != no ]; then
	    if ifdown -a --exclude=lo; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	else
	    if ifdown -a --exclude=lo >/dev/null 2>/dev/null; then
		log_action_end_msg $?
	    else
		log_action_end_msg $?
	    fi
	fi
	;;

force-reload|restart)
	process_options

	log_action_begin_msg "Reconfiguring network interfaces"
	ifdown -a --exclude=lo || true
	if ifup -a --exclude=lo; then
	    log_action_end_msg $?
	else
	    log_action_end_msg $?
	fi
	;;

*)
	echo "Usage: /etc/init.d/networking {start|stop|restart|force-reload}"
	exit 1
	;;
esac

exit 0



---

### Post by satbunny on 2009-11-27
Reading around it seems to be a longstanding issue with the e1000 and e1000e kernel drivers, or more accurately the Intel firmware within the networking device, since there have been reports of issues with Windows 7.

I have found that using static IP and editing my /etc/NetworkManager/nm-system-settings.conf to read helps.

> 
[main]
plugins=ifupdown,keyfile

#no-auto-default=00:1a:a0:9d:20:7b,

[ifupdown]
managed=true

---

