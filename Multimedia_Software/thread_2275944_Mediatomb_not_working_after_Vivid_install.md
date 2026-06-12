---
title: "Mediatomb not working after Vivid install"
date: 2015-04-29
forum: Multimedia Software
---

### Post by Davethehedgehog on 2015-04-29
I recently installed UBUNTU 15.04 and subsequently Mediatomb has stopped working.

I am getting this error message:

This web page has not been found

ERR_FILE_NOT_FOUND
Hide details
No web page was found for the web address: file:///var/lib/mediatomb/mediatomb.html

I tried reinstalling Mediatomb to no avail.  The config file looks OK.

Any help appreciated

---

### Post by nickolay-borisov on 2015-05-08
I have similar problem, mediatomb is not visible on the network after upgrade. However it is available if I run the client (vlc) locally. Presumably some udp related problem/misconfig?

---

### Post by Davethehedgehog on 2015-05-10
The solution seems to be to run mediatomb from the Terminal.  (Simply open a terminal window and type "mediatomb").
If you need access to the web UI there is a URL you can copy and past from the Terminal.

---

### Post by Davethehedgehog on 2015-05-10
The solution seems to be to run mediatomb from the Terminal.  (Simply open a terminal window and type "mediatomb").
If you need access to the web UI there is a URL you can copy and past from the Terminal.

---

### Post by Elfy on 2015-05-10
Glad to see you got somewhere, I had problems with it for a while during the vivid dev cycle - gave up in the end and used something else instead.

---

### Post by ballantony on 2015-05-16
Here's how to run it on bootup:  [http://blog.tonyballantyne.com/ubuntu-15-04-and-mediatomb/](http://blog.tonyballantyne.com/ubuntu-15-04-and-mediatomb/)

---

### Post by tymik on 2015-09-06
Running mediatomb from terminal is not a solution, just a workaround.  Check your /etc/default/mediatomb file if it does bind to 'lo' interface - if yes, change it to your interface that should provide mediatomb and it will be working running as a service.

---

### Post by BarryD9545 on 2015-09-06
> **tymik said:**
> Running mediatomb from terminal is not a solution, just a workaround.  Check your /etc/default/mediatomb file if it does bind to 'lo' interface - if yes, change it to your interface that should provide mediatomb and it will be working running as a service.

Thanks for the answer...but could you help a newb?

My default is:
[INDENT][SIZE=2][FONT=arial]## Network interface on which the server will run, you need to edit this![/FONT][/SIZE][/INDENT]
[INDENT][SIZE=2][FONT=arial]MT_INTERFACE="lo"
[/FONT][/SIZE][/INDENT]
[SIZE=2][FONT=arial]
I need some direction on what exactly i need to change it to.

Thanks for the help![/FONT][/SIZE]

---

### Post by BarryD9545 on 2015-09-07
[FONT=arial]I managed to piece together the info to get MT to not only run, but also have it start up at boot.[/FONT]

[FONT=arial]As administrator, open with and edit the file /etc/default/mediatomb[/FONT]

[FONT=arial]1. The MT_INTERFACE line [/FONT]_must_[FONT=arial] be edited from "l0" to [/FONT][COLOR=#FF0000][FONT=arial]eth0, [/FONT][/COLOR][COLOR=#000000][FONT=arial]or what may be appropriate for the system.
[/FONT][/COLOR][FONT=arial]2. For start at boot, add the NO_START="no" line (I made it first in the file, just to be sure).[/FONT]

[FONT=arial]Note that further down the file, there is an 'MT_PORT="50500"' setting which changes the web interface and port from 49152, which means it's necessary to change the web address in this setting for UI and remote access (I changed my web address and port routing). [/FONT]

[FONT=arial]Here is my file, it is default except as noted in [/FONT][COLOR=#ff0000][FONT=arial]RED[/FONT][/COLOR][COLOR=#000000][FONT=arial]:[/FONT][/COLOR]

```
## This is a sample configuration file for the MediaTomb daemon script
``````
## used on Fedora Core
## also used by Debian, since Jessie release

## By default the configuration will be created in /etc/mediatomb

[COLOR=#ff0000]# Set whether the daemon should be started. Set this value to anything
# but 'yes' to enable the daemon.  I left a space.
NO_START=" "[/COLOR]

[COLOR=#ff0000]## Network interface on which the server will run, you need to edit this!
MT_INTERFACE="eth0"[/COLOR]

## User defined command line options that may be passed to the server
MT_OPTIONS=""

## MediaTomb will be started on port 50500
MT_PORT="50500"

## MediaTomb will run as mediatomb
MT_USER="mediatomb"
MT_GROUP="mediatomb"

## Location of the PID file
MT_PIDFILE="/var/run/mediatomb.pid"

## Location of the log file
MT_LOGFILE="/var/log/mediatomb"

## Location of the config file/database
MT_HOME="/etc"
MT_CFGDIR="mediatomb"

# Debian: keep for compat with old sysv init script
# The route command and arguments to be used if INTERFACE is defined.
# These variables should normally be left unmodified.
ROUTE_ADD="/sbin/route add -net 239.0.0.0 netmask 255.0.0.0"
ROUTE_DEL="/sbin/route del -net 239.0.0.0 netmask 255.0.0.0"
```

The run these two commands in a terminal.

```
$ systemctl start mediatomb

$ sudo systemctl enable mediatomb
```

After putting in your password, it *should* look like nothing happened.

But MediaTomb will now be running, and will be there as a daemon in the future.

---

### Post by BarryD9545 on 2015-09-11
Tymik:

You got me started on the path to a total solution...

And [ballantony]("http://ubuntuforums.org/member.php?u=1385871"), you brought me home!

Thanks!

---

