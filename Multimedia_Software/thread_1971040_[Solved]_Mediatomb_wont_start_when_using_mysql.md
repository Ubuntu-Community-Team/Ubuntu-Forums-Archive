---
title: "[Solved] Mediatomb wont start when using mysql"
date: 2012-05-02
forum: Multimedia Software
---

### Post by HectorG on 2012-05-02
I had an issue where I wanted mediatomb to start on machine startup. For some reason the init scripts for upstart didn't check for a running mysql being up before starting mediatomb , hence it would always fail causing me to start it manually :mad:.


Here is the error I would get in /var/log/mediatomb.log. If I start manuay after a complete boot it would wok without an issue. "sudo service mediatomb start"

2012-05-02 02:30:51    INFO: Configuration check succeeded.
2012-05-02 02:30:51   ERROR: The connection to the MySQL database has failed: mysql_error (2002): "Can't connect to local MySQL server through socket '/var/run/mysqld/mysqld.sock' (2)"


Anyways after struggling with it for a three days on and off I learned how upstart works and put 3 words in my mediatomb.conf file that fixed the issue. ;) Note I am on Ubuntu 12.04 with both mysql and mediatomb as upstart jobs.


in /etc/init/mediatomb.conf

change this line 

start on (local-filesystems and net-device-up IFACE!=l0)

to

start on (started mysql and local-filesystems and net-device-up IFACE!=l0)

Enjoy!! Hope this helps someone...

Here is the entire file if you really need it...

-----------------------------------------------------------------------------------------------------

description "MediaTomb UPnP media server"
author      "Daniel van Vugt <vanvugt in launchpad>"

start on (started mysql and local-filesystems and net-device-up IFACE!=l0)
stop on runlevel [!2345]
respawn

env CONFIGXML=/etc/mediatomb/config.xml
env LOGFILE=/var/log/mediatomb.log
env DEFAULT=/etc/default/mediatomb

script
        [ -r $DEFAULT ] && . $DEFAULT
        [ ! $USER ] && USER=root
        [ ! $GROUP ] && GROUP=$USER
        if [ -n "$INTERFACE" ]; then
                INTERFACE_ARG="-e $INTERFACE"
                $ROUTE_ADD $INTERFACE
        fi
        exec mediatomb \
                -c $CONFIGXML \
                -u $USER \
                -g $GROUP \
                -l $LOGFILE \
                $INTERFACE_ARG \
                $OPTIONS
end script

post-stop script
        [ -r $DEFAULT ] && . $DEFAULT
        if [ -n "$INTERFACE" ]; then
                $ROUTE_DEL $INTERFACE
        fi
end script

---

### Post by SixedUp on 2012-06-30
Thanks - you just saved ne 3 days debugging!

---

### Post by HectorG on 2012-06-30
Happy to hear it helped you out!  :-D

---

### Post by mljbr4 on 2012-07-24
Thanks for this solution - it worked perfectly and saved me a heap of time.

---

