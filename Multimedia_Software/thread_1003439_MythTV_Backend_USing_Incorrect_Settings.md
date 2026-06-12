---
title: "MythTV Backend USing Incorrect Settings"
date: 2008-12-06
forum: Multimedia Software
---

### Post by Tux+ on 2008-12-06
I am having problems with my Myth backend starting up. I'm using Ubuntu 8.04 and did have a MythTV install previously on Ubuntu 7.10 but the only thing that was carried forward from the 7.10 was the home directory.

In the mythtv-setup all the settings look fine and the settings are saved because when I complete the install and re-run mythtv-setup the settings are correct and still the same.
The problem is when I look in the logs of the mythtv-backend service it prints out the incorrect IP address and password. I noticed these settings were from the old install on 7.10.

If I start the backend manually using the command:
```
mythbackend
```
The correct settings are used and my front end can connect to it.

It's odd that the service uses the old myth settings and I wouldn't have thought the mythtv-backend service use and config files in the home directory as this is the only directory that existed in 7.10.

Is there a way to manually change the backend config file to match my new setup?

For people interested here's my backend log file with the incorrect / previous myth install details:
```

Would you like to configure the database connection now? [yes]  
[console is not interactive, using default 'yes']
Database host name: [192.168.0.5]  
[console is not interactive, using default '192.168.0.5']
Should I test connectivity to this host using the ping command? [yes]  
[console is not interactive, using default 'yes']
Database non-default port: [3306]  
[console is not interactive, using default '3306']
Database name: [mythconverg]  
[console is not interactive, using default 'mythconverg']
Database user name: [mythtv]  
[console is not interactive, using default 'mythtv']
Database password: [WCSFFPs2]  
[console is not interactive, using default 'WCSFFPs2']
Unique identifier for this machine (if empty, the local host name will be used):  
[console is not interactive, using default '']
Would you like to use Wake-On-LAN to retry database connections? [no]  
[console is not interactive, using default 'no']
2008-12-06 10:16:03.437 Cannot connect to port 3306 on database host 192.168.0.5
2008-12-06 10:16:03.443 Cannot connect to port 3306 on database host 192.168.0.5

Cannot connect to port 3306 on database host 192.168.0.5

```

After that it repeats in the log.

---

