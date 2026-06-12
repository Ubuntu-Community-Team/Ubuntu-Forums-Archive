---
title: "Software Center Crashes"
date: 2010-09-30
forum: Maverick Meerkat Testing and Discussion (CLOSED)
---

### Post by TheWeakSleep on 2010-09-30
Just did a fresh install of the release candidate, and everything was working fine until not too long ago and now every time I try and open the software center, it crashes.

When run through the terminal it outputs this:

```
Traceback (most recent call last):
  File "/usr/bin/software-center", line 38, in <module>
    import softwarecenter.log 
  File "/usr/share/software-center/softwarecenter/log.py", line 92, in <module>
    backupCount=5)
  File "/usr/lib/python2.6/logging/handlers.py", line 112, in __init__
    BaseRotatingHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/handlers.py", line 64, in __init__
    logging.FileHandler.__init__(self, filename, mode, encoding, delay)
  File "/usr/lib/python2.6/logging/__init__.py", line 827, in __init__
    StreamHandler.__init__(self, self._open())
  File "/usr/lib/python2.6/logging/__init__.py", line 846, in _open
    stream = open(self.baseFilename, self.mode)
IOError: [Errno 13] Permission denied: '/home/andrew/.cache/software-center/software-center.log'

```

Though I don't really understand it.
Is this something I should report?

---

### Post by mperry on 2010-10-01
I just tried changing the permission of that log file to root:root and I get the same error. When I change the log file back to me owning it, the problem goes away. Perhaps caused  by running as root user? Not sure since I see errors when I run sudo software-center in the terminal.

---

### Post by 23dornot23d on 2010-10-01
Everything seems to be working well for me .... 

I usually just use aptitude .... but thought I would give UCS a try 

and am impressed so far ....  are you fully uptodate .....

I get errors if I do 

sudo software-center 

too

keith@keith-laptop:~$ sudo software-center
[sudo] password for keith: 
WARNING:softwarecenter.fixme:logs to the root logger: '('/usr/share/software-center/softwarecenter/view/widgets/mkit_themes.py', 675, 'retrieve')'
WARNING:root:No styling hints for OSX-NiX were found... using Human hints.
WARNING:softwarecenter.backend.scagent:error in query_info 'Operation not supported'
WARNING:softwarecenter.fixme:logs to the root logger: '('/usr/share/software-center/softwarecenter/db/update.py', 367, '_error_cb')'
WARNING:root:error: Operation not supported
INFO:softwarecenter.app:software-center-agent finished with status 1
WARNING:softwarecenter.fixme:logs to the root logger: '('/usr/lib/pymodules/python2.6/dbus/proxies.py', 400, '_introspect_error_handler')'
ERROR:dbus.proxies:Introspect error on :1.156:/: dbus.exceptions.DBusException: org.freedesktop.DBus.Error.AccessDenied: Rejected send message, 1 matched rules; type="method_call", sender=":1.159" (uid=0 pid=13746 comm="/usr/bin/python) interface="org.freedesktop.DBus.Introspectable" member="Introspect" error name="(unset)" requested_reply=0 destination=":1.156" (uid=0 pid=13194 comm="/usr/bin/python))

---

### Post by sikander3786 on 2010-10-01
Might also be caused by installation of a newer version Python? Did you...?

---

### Post by seeker5528 on 2010-10-01
> **mperry said:**
> Not sure since I see errors when I run sudo software-center in the terminal.

If it writes files in your home directory issuing 'sudo software-center' is bad. You should use 'sudo -H software-center' or use gksudo or kdesudo.

Later, Seeker

---

### Post by TheWeakSleep on 2010-10-01
Thanks for the replys, for whatever reason the files belonged to root, so I changed them back, and a recent update fixed the issues.

---

### Post by Mr. Picklesworth on 2010-10-01
> **seeker5528 said:**
> If it writes files in your home directory issuing 'sudo software-center' is bad. You should use 'sudo -H software-center' or use gksudo or kdesudo.

Later, Seeker

Actually, you shouldn't run software-center as root at all :)

It expects to run as a regular, unprivileged user. To install software, it uses PolicyKit with a new piece of software called AptDaemon. This way the privileged operation of installing software is a separate process, which vastly improves security, usability and coolness. (Since the GUI for Software Center knows who you are and can do neat things without the risk of being tricked into running arbitrary commands as root).

We're moving in that direction for everything, really, so expect to use sudo less and less for graphical applications.

---

