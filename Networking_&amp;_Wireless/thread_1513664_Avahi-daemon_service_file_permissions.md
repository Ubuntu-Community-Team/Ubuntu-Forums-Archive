---
title: "Avahi-daemon service file permissions???"
date: 2010-06-19
forum: Networking &amp; Wireless
---

### Post by fr33loder on 2010-06-19
Hi all!

In a previous [thread]("http://ubuntuforums.org/showthread.php?t=1482573") I had detailed an issue I was having with avahi not firing up properly at startup.
As a bit of background: the services available on the server aren't advertising until I restart the avahi-daemon manually after startup - The syslog shows the daemon starting on boot, but it never seems to access the service file.

I was wondering if it is possible that this may be a file permission problem?

the afpd.service file is currently set to '-rw-r--r--' (ie. all can read, owner [root] can write).

is it possible this may be the problem???

(and while I have your attention....would a samba server on the same system cause any potential conflict?)

Thanks in advance!

---

### Post by fr33loder on 2010-06-19
OK.. a little more info...and a brief glimmer of hope:

I changed the file permission on the afpd.service file to -rwxrwxrwx, rebooted, and the advertising of services worked correctly...however, I rebooted again to confirm and it didn't work!

relevant section of syslog from successful boot:

```

Jun 20 10:36:47 gandalf avahi-daemon[915]: Network interface enumeration completed.
Jun 20 10:36:47 gandalf avahi-daemon[915]: Registering new address record for fe80::21a:4dff:fe45:74c9 on eth0.*.
Jun 20 10:36:47 gandalf avahi-daemon[915]: Server startup complete. Host name is gandalf.local. Local service cookie is 2216900596.
Jun 20 10:36:47 gandalf avahi-daemon[915]: Service "gandalf AFP" (/services/afpd.service) successfully established.
Jun 20 10:36:47 gandalf avahi-daemon[915]: Registering HINFO record with values 'X86_64'/'LINUX'.
Jun 20 10:36:47 gandalf postfix/master[1077]: fatal: open lock file /var/lib/postfix/master.lock: cannot open file: Permission denied
Jun 20 10:36:47 gandalf afpd[1108]: Registering CNID module [last]
Jun 20 10:36:47 gandalf afpd[1108]: Registering CNID module [cdb]
Jun 20 10:36:47 gandalf afpd[1108]: Registering CNID module [dbd]
Jun 20 10:36:47 gandalf afpd[1108]: Loading ConfigFile
Jun 20 10:36:47 gandalf kernel: [   12.008092] NET: Registered protocol family 5
Jun 20 10:36:48 gandalf afpd[1108]: main: atp_open: Cannot assign requested address
Jun 20 10:36:48 gandalf afpd[1108]: dsi_tcp: hostname 'gandalf' resolves to loopback address      
Jun 20 10:36:48 gandalf afpd[1108]: dsi_tcp (Chooser will not select afp/tcp) Check to make sure gandalf is in /etc/hosts and the correct domain is in /etc/resolv.conf: Success
Jun 20 10:36:48 gandalf afpd[1108]: ASIP started on 0.0.0.0:548(5) (2.0.5)
Jun 20 10:36:48 gandalf afpd[1108]: uam: loading (/usr/lib/netatalk/uams_clrtxt.so)
Jun 20 10:36:48 gandalf afpd[1108]: uam: uams_clrtxt.so loaded
Jun 20 10:36:48 gandalf afpd[1108]: uam: loading (/usr/lib/netatalk/uams_dhx2.so)
Jun 20 10:36:48 gandalf afpd[1108]: uam: uams_dhx2.so loaded
Jun 20 10:36:48 gandalf afpd[1108]: uam: "DHX2" available
Jun 20 10:36:48 gandalf afpd[1108]: uam: "Cleartxt Passwrd" available
Jun 20 10:36:48 gandalf afpd[1108]: Finished parsing Config File
Jun 20 10:36:48 gandalf /etc/mysql/debian-start[1170]: Upgrading MySQL tables if necessary.  
Jun 20 10:36:48 gandalf /etc/mysql/debian-start[1173]: /usr/bin/mysql_upgrade: the '--basedir' option is always ignored
Jun 20 10:36:48 gandalf /etc/mysql/debian-start[1173]: Looking for 'mysql' as: /usr/bin/mysql
Jun 20 10:36:48 gandalf /etc/mysql/debian-start[1173]: Looking for 'mysqlcheck' as: /usr/bin/mysqlcheck
Jun 20 10:36:48 gandalf /etc/mysql/debian-start[1173]: This installation of MySQL is already upgraded to 5.1.41, use --force if you still need to run mysql_upgrade
Jun 20 10:36:48 gandalf /etc/mysql/debian-start[1180]: Checking for insecure root accounts.
Jun 20 10:36:48 gandalf /etc/mysql/debian-start[1184]: Triggering myisam-recover for all MyISAM tables
Jun 20 10:36:50 gandalf init: plymouth-stop pre-start process (1233) terminated with status 1
Jun 20 10:36:53 gandalf dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
Jun 20 10:36:53 gandalf dhclient: DHCPOFFER of 192.168.0.52 from 192.168.0.1
Jun 20 10:36:53 gandalf dhclient: DHCPREQUEST of 192.168.0.52 on eth0 to 255.255.255.255 port 67

```

HELP?!?!?!?!

Thanks!

---

