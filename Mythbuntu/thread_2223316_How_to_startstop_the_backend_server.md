---
title: "How to start/stop the backend server?"
date: 2014-05-10
forum: Mythbuntu
---

### Post by dannyboy79 on 2014-05-10
I know this seems like a silly question but I just upgraded to mythtv 0.27+fixes and I now can't stop/start the server using ```
sudo service mythbackend stop
``` I've read all I have to do is issue ```
sudo mythbackend stop
``` but that doesn't work either, it merely spits out the help information along with the following message "Received 'status' but unassociated arguments have not been enabled mythbackend version: fixes/0.27 [v0.27-229-g9f353cc]

Can someone please help me? My mythbackend.conf file looks like this and it's stored within /etc/init/
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

---

### Post by dannyboy79 on 2014-05-10
so that I can have auto-complete of the command and use tab, i created a symlink called mythtv-backend and stored it within /etc/init.d/ and pointed it at /etc/init/mythtv-backend and now using ```
sudo service myth
``` and hitting tab it autocompletes the command and works again for stopping my backend server. YEAHHHHHH

---

### Post by blm-ubunet on 2014-05-10
Solved ? workaround maybe..
```
sudo service mythtv-backend stop
```
auto-completion of your cmd should have found the service name..

[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
The upstart job conf file is named mythtv-backend.conf.

---

### Post by dannyboy79 on 2014-05-10
as i wrote above, there was no mythtv-backend file located within /etc/init.d/ therefore there was no way to run mythtv using the "service" thingy. Once I created the symlink pointing to the /etc/init/mythtv-backend.conf it started working again. I have no idea why Ubuntu 14.04 has some services started and stopped using ```
sudo service foo start/stop/restart/status
``` and some services are ran just by themselves. For example apache2 and mysql are both started and stopped using ```
sudo service mysql start
``` as an example

---

### Post by blm-ubunet on 2014-05-10
I get you now..
This bit was missing..
```
ln -s /lib/init/upstart-job /etc/init.d/mythtv-backend
```

Are you using mythbuntu distro (& not just mythbuntu ppa) ?
The author of
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
is also a mythbuntu dev/team member.
I imagine he/they would consider this to be a bug in the packaging/install scripts.

---

### Post by dannyboy79 on 2014-05-11
> **blm-ubunet said:**
> I get you now..
This bit was missing..
```
ln -s /lib/init/upstart-job /etc/init.d/mythtv-backend
```

Are you using mythbuntu distro (& not just mythbuntu ppa) ?
The author of
[http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration](http://www.mythtv.org/wiki/Upstart_mythbackend_Configuration)
is also a mythbuntu dev/team member.
I imagine he/they would consider this to be a bug in the packaging/install scripts.
i am using xubuntu 14.04 with mythbuntu control center installed but i do have an issue with MCC, it's this thread here where i ask if anyone else is having this issue. [http://ubuntuforums.org/showthread.php?t=2220885](http://ubuntuforums.org/showthread.php?t=2220885)

i wasn't missing anything, i didn't do what you posted. as I stated the solution i came up with in post #2, I did the following
[code]sudo ln -s /etc/init/mythtv-backend.conf /etc/init.d/mythtv-backend

---

