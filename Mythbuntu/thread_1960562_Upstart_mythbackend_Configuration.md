---
title: "Upstart mythbackend Configuration"
date: 2012-04-17
forum: Mythbuntu
---

### Post by Paulgirardin on 2012-04-17
After upgrading to 0.25 mythbackend does not start.

I've tried to use the script on the Upstart mythbackend Configuration page but I don't think I have the script configured correctly.

Can anyone compare my original mythtv-backend.conf file with the one new one that I have done to see where I might have made a mistake?

Original:

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

#expect fork
respawn
respawn limit 2 3600

pre-start script 
    [ -x /usr/sbin/mysqld ] || exit 0
    for i in `seq 1 30` ; do
       /usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping && exit 0
       sleep .5
    done
end script

script
	test -f /etc/default/locale && . /etc/default/locale || true
	LANG=$LANG /usr/bin/mythbackend --syslog local7 --user mythtv
end script
```

New one:

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        ulimit -c unlimited                              
        . /etc/default/locale                            
        export LANG
        export LC_ALL=$LANG
        ARGS="--syslog local7"                           
        sleep 5                                         
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend --user mythtv $ARGS $EXTRA_ARGS
end script
```

---

### Post by nickrout on 2012-04-17
What I don't get is that Mario Limonciello wrote the scripts, and is a mythbuntu developer. However the script shipped with 12.04 (beta) is different to what is posted on the wiki.

Shipped with mythbuntu:

```
~$ cat /etc/init/mythtv-backend.conf
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

#expect fork
respawn
respawn limit 2 3600

pre-start script
    [ -x /usr/sbin/mysqld ] || exit 0
    for i in `seq 1 30` ; do
       /usr/bin/mysqladmin --defaults-file=/etc/mysql/debian.cnf ping && exit 0
       sleep .5
    done
end script

script
        test -f /etc/default/locale && . /etc/default/locale || true
        LANG=$LANG /usr/bin/mythbackend --syslog local7 --user mythtv
end script

```

wiki:

```
# MythTV Backend service

description     "MythTV Backend"
author          "Mario Limonciello <superm1@ubuntu.com>"

start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on starting shutdown

#expect fork
respawn

script
        ulimit -c unlimited                              # Note 1.
        . /etc/default/locale                            # Note 2.
        export LANG
        export LC_ALL=$LANG
        ARGS="--logfile /var/log/mythtv/mythbackend.log" #
        ARGS="--logpath /var/log/mythtv"                 # Note 3. (choose 1)
        ARGS="--syslog local7"                           #
        sleep 5                                          # Note 4.
        test -f /etc/default/mythtv-backend && . /etc/default/mythtv-backend || true
        /usr/bin/mythbackend --user mythtv $ARGS $EXTRA_ARGS
end script
```

for completeness I add the notes from the wiki:

```
1, In 0.25 use ulimit -c unlimited to allow mythbackend core files or ulimit -c 0 to inhibit them.

2, 0.25 and above verify that the LANG and (LC_ALL or LC_CTYPE) variables are set. If /etc/default/locale (or an equivalent) doesn't exist, the value for LANG and related language settings can be seen by typing locale on the command line.

3, --logfile is used prior to 0.25, use --logpath or --syslog with 0.25 and above. See Logging.

4, IPv6 users may find that net-device-up IFACE does not guarantee that their addresses are available for the backend to bind to and should add a sleep 5 before starting it. 
```

---

### Post by Paulgirardin on 2012-04-18
I followed the steps 1 to 4 on the wiki.
I wasn't sure what step 1 should be so I left it as is.

---

### Post by Paulgirardin on 2012-04-18
I received a suggestion on another thread that fixed the problem.
Change IFACE!=lo to IFACE=lo in the following line in mythtv-backend.conf 
 
start on (local-filesystems and net-device-up IFACE!=lo and started udev-finish)
stop on runlevel [016]

---

### Post by nickrout on 2012-04-18
So to clarify, are you running a single combined BE/FE with the backend listening on localhost? (Not an external IP address).

If so, i can see how this fix applies.

However such a setup is not very desirable, as you will have to reconfigure a whole lot of stuff to ever use another frontend.

Still nobody has answered why mythbuntu ships with one upstart configuration script, but a different one by the same author is posted on the wiki.

Mario??

---

### Post by tgm4883 on 2012-04-18
> **nickrout said:**
> So to clarify, are you running a single combined BE/FE with the backend listening on localhost? (Not an external IP address).

If so, i can see how this fix applies.

However such a setup is not very desirable, as you will have to reconfigure a whole lot of stuff to ever use another frontend.

Still nobody has answered why mythbuntu ships with one upstart configuration script, but a different one by the same author is posted on the wiki.

Mario??

If I had to guess, it's because he hasn't updated the one in the wiki lately.

---

### Post by Paulgirardin on 2012-04-19
> **nickrout said:**
> So to clarify, are you running a single combined BE/FE with the backend listening on localhost? (Not an external IP address).

If so, i can see how this fix applies.

However such a setup is not very desirable, as you will have to reconfigure a whole lot of stuff to ever use another frontend.

Still nobody has answered why mythbuntu ships with one upstart configuration script, but a different one by the same author is posted on the wiki.

Mario??

That is correct.I set it up that way as I am unlikely to be running multiple frontends.(happily single):lolflag:

---

