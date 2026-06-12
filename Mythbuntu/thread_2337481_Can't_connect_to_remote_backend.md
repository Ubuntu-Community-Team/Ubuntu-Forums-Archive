---
title: "Can't connect to remote backend"
date: 2016-09-18
forum: Mythbuntu
---

### Post by carrucha2 on 2016-09-18
I wiped my old setup recently and installed mythbuntu 16.04.  I set it up and after fixing a couple of things that weren't working and got it recording.  That machine is a dedicated backend.

For a frontend, I'm trying to use my firetv.  I've got MRMC installed that I'm attempting to use, but I haven't ever done it or anything else on a firetv (if someone has some recommendations on how to achieve this on a firetv please share).  Unfortunately, the frontend will not connect.  I tried MythTvPlayer on Windows to compare, as well as something on my android phone, and they will not connect either.

I've done a few tweaks to try to fix it, but so far haven't been able to get a connection.  What am I missing?

My setup:
Dedicated backend
```

DVR-B1 (192.168.1.200)
Mythbuntu 16.04
Port: 6543
Status port: 6544
Security pin: 0000
Ipv4 address: 127.0.0.1
Ipv6 address: ::1
Listen on link-local addresses: checked
Master backend ip address: 127.0.0.1
Master backend port: 6543

```

Master frontend (not used)
        database settings
```

host: localhost
port: 3306
database: mythconverg
user: mythtv
password: mypassword

```

The master frontend seems to work fine.

My desired frontend:
Something that runs on firetv.
Trying MRMC currently

Frontends I've tried:
    MRMC (Mythtv pvr client)
```

Mythtv backend hostname or ip: dvr-b1
Mythtv backend port: 6543
Mythtv backend port for api services: 6544
Mythtv security pin for api services: 0000

```
Error: Mythtv pvr client - No response from mythtv backend

MythTvPlayer 0.7.2
```

Trying either dvr-b1 or 192.168.1.200 I get errors like:
Could not connect to backend: 'dvr-b1', port: '6543'

```

Mythling on android
```

Failed to connect to dvr-b1/192.168.1.200 (port 6544)... connection refused

```

My fixes after installation:

/etc/mysql/conf.d/mythtv.cnf
```

[mysqld]
bind-address=::

# fixes fatal mysql connection errors
sql_mode=NO_ENGINE_SUBSTITUTION

```

Updated mysql privileges using this

```

GRANT ALL PRIVILEGES ON *.* TO 'mythtv'@'%' WITH GRANT OPTION;

```

I can connect to mysql directly from my windows machine, but the mythtv clients don't connect.

The security key test connection in mythbuntu control centre on the backend passes with key 0000.

---

### Post by uteck on 2016-09-18
Did you use myth control center to enable access to remote frontends?

It looks like you are missing the IP of the backend in the settings.  Look in /etc/mysql/my.cnf and set the bind-address to the system IP if you are doing it manually.

---

### Post by carrucha2 on 2016-09-19
I have in Mythbuntu Control Centre > MySQL Configuration > Master Backend Role 
MySQL service on ethernet interfaces (required for remote Frontend or Backend) - Enabled

---

### Post by carrucha2 on 2016-09-19
My /etc/mysql/my.cnf doesn't have anything in it but the includes for other files.

I have tried variations of these in my [COLOR=#000000]/etc/mysql/conf.d/mythtv.cnf[/COLOR]
# bind-address=::
# bind-address 0:0:0:0:0:ffff:c0a8:1c8
# bind-address 192.168.1.200
# skip-networking
# bind-address 127.0.0.1

Can you be more specific?

---

### Post by deadflowr on 2016-09-19
The ip is listed as loopback instead of the LAN address.
```
DVR-B1 (192.168.1.200)
Mythbuntu 16.04
Port: 6543
Status port: 6544
Security pin: 0000
Ipv4 address: **127.0.0.1**
Ipv6 address: ::1
Listen on link-local addresses: checked
Master backend ip address: **127.0.0.1**
Master backend port: 6543
```

127.0.01 is a  loopback address and can only be access from the local machine.
Change these settings to the LAN address to access remotely.

---

### Post by carrucha2 on 2016-09-19
Thanks. 

I changed those two bolded ones to my ip, now I get this from mythweb:

Error Unable to connect to the master backend at 192.168.1.200:6543. Is it running?

My mysql conf has just
 # bind-address 192.168.1.200

---

### Post by uteck on 2016-09-19
Try restating the mysql server so it reads the new config file.
Also, a config line that start with a # are not read.  Anything after the # is treated as a comment by the program and not instructions.  Remove the # to enable that setting.  Placing a # in front of items is a quick way to disable them, but makes it easy to re-enable them.

---

### Post by carrucha2 on 2016-09-20
OK, it looks like stupid mysql 5.7 changed things, so I had to put this into /etc/mysql/mysql.conf.d/mysqld.cnf instead.

```

# commented out to allow external networking
# bind-address          = 127.0.0.1

```



More info: [http://serverfault.com/questions/782118/mysql-5-7-bind-address-doesnt-work](http://serverfault.com/questions/782118/mysql-5-7-bind-address-doesnt-work)

Thanks guys.

---

### Post by carrucha2 on 2016-09-21
I guess I spoke too soon.  This fixed everything and worked great until I rebooted.  It was having new connection problems after that.  Here's how I got past that and some notes.

Problem
```

Unable to connect to the master backend at 192.168.1.200:6543.
Is it running?

mythtv-status --verbose 

Failed to load Perl API
Couldn't communicate with 192.168.1.200 on port 6543:  IO::Socket::INET::MythTV: connect: Connection refused

```

Solution
```

* sudo cp /lib/systemd/system/mythtv-backend.service /etc/systemd/system/
* sudo nano /etc/systemd/system/mythtv-backend.service
* insert: ExecStartPre=/usr/bin/nm-online --quiet --timeout=5 above the existing ExecStartPre=... line.
* reboot

```

Src: [https://ubuntuforums.org/showthread.php?t=2320224](https://ubuntuforums.org/showthread.php?t=2320224)

---

