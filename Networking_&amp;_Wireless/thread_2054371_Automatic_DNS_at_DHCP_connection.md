---
title: "Automatic DNS at DHCP connection"
date: 2012-09-07
forum: Networking &amp; Wireless
---

### Post by jsam000 on 2012-09-07
Hello,

 I have a machine I need to connect to dhcp on multiple networks successively (Windows Server, Linux Server ....) and his name has to be registered on the DNS server upon connection.

For now, I realize tests with a DHCP server and DNS Windows Server 2008 (the most common) and my machine acquires an IP address at the connection, but is not registered on the DNS server. Enabling Samba enables recording on the DNS server but I can not let Samba permanently activated.

 I really need the DNS record to make at the connection.

Here is the configuration of my machine:


/etc/dhcp3/dhclient.conf

```
option rfc3442-classless-static-routes code 121 = array of unsigned integer 8;

#send host-name "andare.fugue.com";
#send dhcp-client-identifier 1:0:a0:24:ab:fb:9c;
#send dhcp-lease-time 3600;
#supersede domain-name "fugue.com home.vix.com";
#prepend domain-name-servers 127.0.0.1;
request subnet-mask, broadcast-address, time-offset, routers,
        domain-name, domain-name-servers, domain-search, host-name,
        netbios-name-servers, netbios-scope, interface-mtu,
        rfc3442-classless-static-routes, ntp-servers;
#require subnet-mask, domain-name-servers;
timeout 6;
retry 1;
```/etc/network/interfaces

```
auto lo
iface lo inet loopback
auto eth0
iface eth0 inet dhcp
```/etc/init.d/networking

```
#!/bin/sh -e
### BEGIN INIT INFO
# Provides:          networking
# Required-Start:    mountkernfs $local_fs
# Required-Stop:     $local_fs
# Should-Start:      ifupdown
# Should-Stop:       ifupdown
# Default-Start:     S
# Default-Stop:      0 6
# Short-Description: Raise network interfaces.
### END INIT INFO

PATH="/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin"

[ -x /sbin/ifup ] || exit 0

. /lib/lsb/init-functions

process_options() {
    [ -e /etc/network/options ] || return 0
    log_warning_msg "/etc/network/options still exists and it will be IGNORED! Read README.Debian of netbase."
}

check_network_file_systems() {
    [ -e /proc/mounts ] || return 0

    if [ -e /etc/iscsi/iscsi.initramfs ]; then
        log_warning_msg "not deconfiguring network interfaces: iSCSI root is mounted."
        exit 0
    fi

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

check_network_swap() {
    [ -e /proc/swaps ] || return 0

    exec 9<&0 < /proc/swaps
    while read DEV MTPT FSTYPE REST; do
        case $DEV in
        /dev/nbd*|/dev/nd[a-z]*|/dev/etherd/e*)
            log_warning_msg "not deconfiguring network interfaces: network swap still mounted."
            exit 0
            ;;
        esac
    done
    exec 0<&9 9<&-
}

start_on_boot () {
        process_options

        log_action_begin_msg "Configuring network interfaces"
        if ifup -a; then
            log_action_end_msg $?
        else
            log_action_end_msg $?
        fi
}

case "$1" in
start)
        start_on_boot &
#       process_options
#
#       log_action_begin_msg "Configuring network interfaces"
#       if ifup -a; then
#           log_action_end_msg $?
#       else
#           log_action_end_msg $?
#       fi
        ;;

stop)
        check_network_file_systems
        check_network_swap

        log_action_begin_msg "Deconfiguring network interfaces"
        if ifdown -a --exclude=lo; then
            log_action_end_msg $?
        else
            log_action_end_msg $?
        fi
        ;;

force-reload|restart)
        process_options

        log_warning_msg "Running $0 $1 is deprecated because it may not enable again some interfaces"
        log_action_begin_msg "Reconfiguring network interfaces"
        ifdown -a --exclude=lo || true
        if ifup -a --exclude=lo; then
            log_action_end_msg $?
        else
            log_action_end_msg $?
        fi
        ;;

*)
        echo "Usage: /etc/init.d/networking {start|stop}"
        exit 1
        ;;
esac

exit 0
```Thank you in advance for your help

 Jsam000

---

