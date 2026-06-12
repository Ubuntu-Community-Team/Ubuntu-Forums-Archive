---
title: "Trying to get a script working (auto start up apache2 on boot time)"
date: 2010-10-30
forum: Networking &amp; Wireless
---

### Post by qisheng on 2010-10-30
Hi Dear Helpers,
below is the code i try compiling but having some problems seems like i cant find some function directory and also some syntax error . 



#!/bin/sh
#
# Startup script for the Apache Web Server
#
# chkconfig: 345 85 15
# description: Apache is a World Wide Web server. It is used to serve \
# HTML files and CGI.
# processname: /etc/init.d/httpd
# pidfile: /etc/init.d/httpd.pid
# config: /etc/init.d/httpd.conf

# Source function library.
. /etc/rc.d/init.d/functions

# See how we were called.
case “$1&#8243; in
start)
echo -n “Starting httpd: ”
daemon etc/init.d/httpd -DSSL
echo
touch /var/lock/subsys/httpd
;;
stop)
echo -n “Shutting down http: ”
killproc httpd
echo
rm -f /var/lock/subsys/httpd
rm -f /var/run/httpd.pid
;;
status)
status httpd
;;
restart)
$0 stop
$0 start
;;
reload)
echo -n “Reloading httpd: ”
killproc httpd -HUP
echo
;;
*)
echo “Usage: $0 {start || stop || restart || reload || status}”
exit 1
esac

exit 0

---

