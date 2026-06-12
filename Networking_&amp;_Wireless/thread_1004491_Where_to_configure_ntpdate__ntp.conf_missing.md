---
title: "Where to configure ntpdate / ntp.conf missing"
date: 2008-12-07
forum: Networking &amp; Wireless
---

### Post by betnexrel on 2008-12-07
I'd like to configure the timeservers for ntpdate or disable ntpdate without removing the package (e.g. to invoke ntpdate manually)

In /etc/defaults/ntpdate it says it uses /etc/ntp.conf but this file is missing.

The system clock is apparently set automatically because it's quite accurate...does anyone know where the config files are?



Release: Kubuntu 8.10

---

### Post by iponeverything on 2008-12-07
```
sudo apt-get install ntp

```

---

### Post by betnexrel on 2008-12-07
thx, ok, that would provide an ntp.conf file
but I don't want to install a daemon. As I said, automatic synchronisation seems to work already, without ntp being installed, I just can't figure out from which file(s) the timeserver(s) and the frequency of the queries are taken.

---

### Post by betnexrel on 2008-12-07
Or am I totally wrong and the default installation of (K)Ubuntu _doesn't_ connect to ntp servers? (and the accuracy of the clock is chance)

---

### Post by Dr Small on 2008-12-07
> **betnexrel said:**
> Or am I totally wrong and the default installation of (K)Ubuntu _doesn't_ connect to ntp servers? (and the accuracy of the clock is chance)
That's probably so.
You need the NTP daemon to sync your clock with the timeservers. Having it run as a daemon does not mean it is acting as a server, unless you edit the config file and change listen to *

The config file should be here:
```
/etc/openntpd/ntpd.conf
```

---

### Post by betnexrel on 2008-12-07
I've tested it now by setting the clock to the wrong time, rebooted and the time was correct again. A simple

ntpdate <server>

in a script somewhere would be enough. The package ntp doesn't have to be installed, although, according to the manpage of ntpdate, the daemon is the better solution because of better algorithms for syncing with several servers.

but my issue was rather to keep control over internet connections generally.

A 

grep -iR ntpdate /etc

yields some results but they depend on variables and I don't know if and when the scripts are executed, takes more knowledge/time

it could also be in KDE.'set date & time automatically' was unchecked in System Settings, but since KDE4 is still very new, it might be ignored.

---

