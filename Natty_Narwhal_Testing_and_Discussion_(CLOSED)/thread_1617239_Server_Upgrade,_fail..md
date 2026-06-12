---
title: "Server Upgrade, fail."
date: 2010-11-09
forum: Natty Narwhal Testing and Discussion (CLOSED)
---

### Post by nperry on 2010-11-09
Was bored at work this morning, so thought I would play with natty on my vps - Yes I know, but I love playing with traffic.

Something I've never seen before, anyone able to shed any light?


> Preconfiguring packages ...
Setting up base-files (5.0.0ubuntu25) ...
exec: 3: /usr/lib/update-notifier/update-motd-cpu-checker: not found
run-parts: /etc/update-motd.d/20-cpu-checker exited with return code 2
exec: 3: /usr/lib/update-notifier/update-motd-updates-available: not found
run-parts: /etc/update-motd.d/90-updates-available exited with return code 2
exec: 3: /usr/lib/update-notifier/update-motd-reboot-required: not found
run-parts: /etc/update-motd.d/98-reboot-required exited with return code 2
dpkg: error processing base-files (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports has already been reached
                                                                    Errors were encountered while processing:
 base-files
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up base-files (5.0.0ubuntu25) ...
exec: 3: /usr/lib/update-notifier/update-motd-cpu-checker: not found
run-parts: /etc/update-motd.d/20-cpu-checker exited with return code 2
exec: 3: /usr/lib/update-notifier/update-motd-updates-available: not found
run-parts: /etc/update-motd.d/90-updates-available exited with return code 2
exec: 3: /usr/lib/update-notifier/update-motd-reboot-required: not found
run-parts: /etc/update-motd.d/98-reboot-required exited with return code 2
dpkg: error processing base-files (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 base-files

---

### Post by jfernyhough on 2010-11-09
Are you trying to do a dist-upgrade from Maverick to Natty? If so, it will fail at this point as the upgrade magic doesn't exist. For the moment, to upgrade you have to change all instances of "maverick" to "natty" in /etc/apt/sources.list - or at least that's how I've always done it at the beginning of the development cycle!

---

### Post by nperry on 2010-11-09
That is the way I always upgrade to the development cycle. Change to natty in source list then safe upgrade.

---

