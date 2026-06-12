---
title: "can't reboot after installing apache"
date: 2013-06-07
forum: Networking &amp; Wireless
---

### Post by George Heine on 2013-06-07
Recently installed apache webserver on a spare laptop.  
This was for home network use only, mostly just to experiment.

Upon reboot, system hangs with a garbled message like
```

. . . . * Strting web server apache 2        the server's ful[OK]
lified domain name, using 127.0.0.1 for ServerName      [OK}

```


The most urgent questions are:
  - What is preventing the system from rebooting?
  - How can I fix the problem and boot? 

DETAILS:

I was able to get onto the system with a rescue disk and look at the history file.

The server was installed by first installing "tasksel", then installing "lamp-server" from the tasksel GUI.
(I generally prefer command-line to GUI, but was following an old thread in this forum, and couldn't
find any packages matching "lamp-server" in the repos.)

Found the entry for "lamp-server" in /usr/share/tasksel/ubuntu-tasks.desc:
```

Task: lamp-server
Section: server
Description: LAMP server
 Selects a ready-made Linux/Apache/MySQL/PHP server.
Key:
 apache2
 mysql-server
Packages: task-fields

```
Later in the history file, the following entry shows up:
```
sudo service apache2 restart

```
Can't find a matching "service apache2 stop" command.
Apparently I shut the system shut down without stopping the server.


Thanks for any help.

---

### Post by steeldriver on 2013-06-07
AFAIK that's a pretty standard error message from apache2 in a 'home' environment (i.e. one in which you don't have an actual domain) - it shouldn't have any effect on booting the system - iirc you can make it go away by putting 'ServerName localhost' in /etc/apache2/httpd.conf

Does it at least boot to a console login? if so are you sure you didn't just accidentally de-select the desktop (GUI) in tasksel when you selected the LAMP server?

---

### Post by George Heine on 2013-06-08
> make it go away by putting 'ServerName localhost' in /etc/apache2/httpd.conf

Went iin and edited httpd.conf as suggested.
No longer got a message about not knowing the FQDN, but boot halted with message:
"Starting web server apache2"

Restarted in recovery mode, updated the system, and removed apache2 (using aptitude).
Boot is still hung - it pauses at "Ubuntu 12.04", with two white dots and two red dots.

Sigh - maybe it's time to rebuild the system.
And stay away from tasksel.

---

### Post by steeldriver on 2013-06-08
I've never had any problem with tasksel myself, but fyi you should be able to install LAMP with an apt-get one liner (note the caret **^** at the end)

```
sudo apt-get install lamp-server^
```

---

### Post by George Heine on 2013-06-08
```
$ aptitude -s install lamp-server^
Couldn't find any package whose name or description matched "lamp-server^"
Couldn't find any package whose name or description matched "lamp-server^"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 46 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.
Would download/install/remove packages.
```

```
$ dpkg -l lamp-server*
No packages found matching lamp-server*.
```

????

---

### Post by Cheesemill on 2013-06-08
The lamp-server^ package is only available using apt-get not aptitude.

This has always puzzled me.

Anyway doing a 'sudo apt-get install lamp-server^' has exactly the same effect as installing using tasksel.

---

### Post by George Heine on 2013-06-09
> The lamp-server^ package is only available using apt-get not aptitude.
This has always puzzled me.

You're right; that does seem puzzling.

> Anyway doing a 'sudo apt-get install lamp-server^' has exactly the same effect as installing using tasksel.

Perhaps the following would work (see the extract from /usr/share/tasksel/ubuntu-tasks.desc in my first post.)
```
sudo aptitude install apache2  mysql-server
```
Will give it a try once my system is rebuilt and stable.

---

