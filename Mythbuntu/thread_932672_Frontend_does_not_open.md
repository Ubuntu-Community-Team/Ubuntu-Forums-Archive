---
title: "Frontend does not open"
date: 2008-09-28
forum: Mythbuntu
---

### Post by aoshisan on 2008-09-28
Hey All !
I have been Googling & reading FAQ's all day.  The backend IP & pswd are OK.
Here is the var/log/mythtv/mythfrontend.log
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..

And nothing...

Please advise.

---

### Post by tgm4883 on 2008-09-28
> **aoshisan said:**
> Hey All !
I have been Googling & reading FAQ's all day.  The backend IP & pswd are OK.
Here is the var/log/mythtv/mythfrontend.log
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..
Starting mythfrontend.real..

And nothing...

Please advise.

Post your /var/lib/mythtv/mythfrontend.log file,

:EDIT:

The whole thing, I mean.

Also, try starting it from the command line and post that output as well

---

### Post by aoshisan on 2008-09-28
I don't show "/var/lib/mythtv" file.

Here is terminal startup:

murf@computer05:~$ sudo mythtv
[sudo] password for murf: 
2008-09-28 17:33:01.962 Using runtime prefix = /usr, libdir = /usr/lib
2008-09-28 17:33:01.966 XScreenSaver support enabled
2008-09-28 17:33:01.966 DPMS is active.
2008-09-28 17:33:01.966 Empty LocalHostName.
2008-09-28 17:33:01.966 Using localhost value of computer05
2008-09-28 17:33:01.967 Testing network connectivity to 192.168.0.105
2008-09-28 17:33:01.975 New DB connection, total: 1

---

### Post by tgm4883 on 2008-09-28
yea thats cause it should say /var/log, but you already got that.

you shouldn't need to sudo it though, just do

```
mythfrontend
```

---

