---
title: "start mysql at boot"
date: 2010-07-28
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by suoko on 2010-07-28
i'm testing a new software for hotels, gesthotel, and it uses mysql
I had to modify rc.local to start the service, which is not that nice.
Any chance to have it automatically started at boot ?

---

### Post by ranch hand on 2010-07-28
You should be able to add it to System>Preferences>Startup Applications.

---

### Post by jpeddicord on 2010-07-28
> **ranch hand said:**
> You should be able to add it to System>Preferences>Startup Applications.

Not really, it's a system service.

Mysqld *should* automatically start at boot. Is it present in `ls -l /etc/rc2.d | grep mysql`? If not, check in /etc/init for it; it may be started by Upstart.

---

### Post by cariboo on 2010-07-28
Do you actually have mysql-server-5.1 installed? Mysql-server is just an empty package.

---

### Post by VMC on 2010-07-28
> **jpeddicord said:**
> Not really, it's a system service.

Mysqld *should* automatically start at boot. Is it present in `ls -l /etc/rc2.d | grep mysql`? If not, check in /etc/init for it; it may be started by Upstart.

But there's another tab "Options" that might that might allow it to startup. Make sure its running first.

---

### Post by SevenMachines on 2010-07-28
if mysql isnt starting by default

$ sudo update-rc.d mysql defaults

should do it too

---

### Post by jpeddicord on 2010-07-28
> **VMC said:**
> But there's another tab "Options" that might that might allow it to startup. Make sure its running first.

GNOME and the desktop session doesn't have anything to do with system services. If you try to add "mysql" to your startup applications, it's not going to run because you don't have the necessary permissions.

Remembering running applications only applies to session-aware apps. System services again have nothing to do with the desktop session, so the session manager can't do anything about them.

---

### Post by seeker5528 on 2010-07-28
I've never had to do anything special to make mysql run.

If I open a terminal window and type:

```
sudo service mysql start
```

It tells me it's already running.

I never got into the database stuff much and avoided messing with MySQL anymore than was required for use with the packages that depend on it, so I don't know what kind of debconf configuration is provided in the packaging, but doing:

```
dpkg-reconfigure mysql-server-5.1
```

Should give you some basic set up, which may or may not include the option on whether you want it to start when the system starts or not.

Later, Seeker

---

