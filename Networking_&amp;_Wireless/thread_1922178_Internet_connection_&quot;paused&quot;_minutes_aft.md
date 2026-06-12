---
title: "Internet connection &quot;paused&quot; minutes after logged in"
date: 2012-02-08
forum: Networking &amp; Wireless
---

### Post by tengan on 2012-02-08
Hello world,

I'm experiencing a problem where (usually) a few minutes after booting and logging in to Ubuntu, my internet connection is lost. Or perhaps not "lost", but tabs in Firefox keeps loading, so I don't get an error message but nothing happens. Spotify runs fine btw.

For some reason I've gotten this feeling that it's not a problem with Firefox, but something in Ubuntu. Like if pgl has a delayed start and when it's initializing the Internet requests from my computer with DNS fails (and Spotify uses IP and not DNS right?).

**Output from /var/log/syslog:**
```
Feb  8 13:50:39 tengan-PRIMARY rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1266" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Feb  8 13:53:03 tengan-PRIMARY sudo: pam_ecryptfs: pam_sm_authenticate: /home/tengan is already mounted
Feb  8 13:55:17 tengan-PRIMARY sudo: pam_ecryptfs: pam_sm_authenticate: /home/tengan is already mounted
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: Connected to dbus system bus.
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: Started.
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: ASCII: 134643 entries loaded from "/var/lib/pgl/master_blocklist.p2p"
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: Blocking 134643 IP ranges (835406860 IPs).
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: NFQUEUE: binding to queue 92
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: ACCEPT mark: 20
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: REJECT mark: 10
tengan@tengan-PRIMARY:~$ cat /var/log/syslog
Feb  8 13:50:39 tengan-PRIMARY rsyslogd: [origin software="rsyslogd" swVersion="5.8.1" x-pid="1266" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
Feb  8 13:53:03 tengan-PRIMARY sudo: pam_ecryptfs: pam_sm_authenticate: /home/tengan is already mounted
Feb  8 13:55:17 tengan-PRIMARY sudo: pam_ecryptfs: pam_sm_authenticate: /home/tengan is already mounted
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: Connected to dbus system bus.
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: Started.
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: ASCII: 134643 entries loaded from "/var/lib/pgl/master_blocklist.p2p"
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: Blocking 134643 IP ranges (835406860 IPs).
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: NFQUEUE: binding to queue 92
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: ACCEPT mark: 20
Feb  8 13:55:26 tengan-PRIMARY pgld: INFO: REJECT mark: 10
Feb  8 13:57:48 tengan-PRIMARY pgld: INFO: Closing logfile: /var/log/pgl/pgld.log
Feb  8 13:57:48 tengan-PRIMARY pgld: INFO: Reopened logfile: /var/log/pgl/pgld.log
Feb  8 13:57:48 tengan-PRIMARY pgld: WARN: pgld dbus is already initialized.
Feb  8 13:57:48 tengan-PRIMARY pgld: ERROR: Cannot initialize D-Bus
Feb  8 13:57:57 tengan-PRIMARY anacron[1371]: Job `cron.daily' terminated (mailing output)
Feb  8 13:57:57 tengan-PRIMARY anacron[1371]: Can't find sendmail at /usr/sbin/sendmail, not mailing output
Feb  8 13:57:57 tengan-PRIMARY anacron[1371]: Job `cron.weekly' started
Feb  8 13:57:57 tengan-PRIMARY anacron[5440]: Updated timestamp for job `cron.weekly' to 2012-02-08
Feb  8 13:57:59 tengan-PRIMARY anacron[1371]: Job `cron.weekly' terminated
Feb  8 13:57:59 tengan-PRIMARY anacron[1371]: Normal exit (2 jobs run)
Feb  8 14:00:26 tengan-PRIMARY pgld: INFO: Connected to dbus system bus.
Feb  8 14:00:26 tengan-PRIMARY pgld: INFO: Started.
Feb  8 14:00:26 tengan-PRIMARY pgld: INFO: ASCII: 134643 entries loaded from "/var/lib/pgl/master_blocklist.p2p"
Feb  8 14:00:26 tengan-PRIMARY pgld: INFO: Blocking 134643 IP ranges (835406860 IPs).
Feb  8 14:00:26 tengan-PRIMARY pgld: INFO: NFQUEUE: binding to queue 92
Feb  8 14:00:26 tengan-PRIMARY pgld: INFO: ACCEPT mark: 20
Feb  8 14:00:26 tengan-PRIMARY pgld: INFO: REJECT mark: 10
```**Output from /var/log/pgl/pgld.log**
```
Feb  8 13:50:39 INFO: Reopened logfile: /var/log/pgl/pgld.log
Feb  8 13:50:39 WARN: pgld dbus is already initialized.

Feb  8 13:50:39 ERROR: Cannot initialize D-Bus
Feb  8 13:55:26 INFO: Connected to dbus system bus.
Feb  8 13:55:26 INFO: Started.
Feb  8 13:55:26 INFO: ASCII: 134643 entries loaded from "/var/lib/pgl/master_blocklist.p2p"
Feb  8 13:55:26 INFO: Blocking 134643 IP ranges (835406860 IPs).
Feb  8 13:55:26 INFO: NFQUEUE: binding to queue 92
Feb  8 13:55:26 INFO: ACCEPT mark: 20
Feb  8 13:55:26 INFO: REJECT mark: 10
Feb  8 13:57:48 INFO: Closing logfile: /var/log/pgl/pgld.log
Feb  8 13:57:48 INFO: Reopened logfile: /var/log/pgl/pgld.log
Feb  8 13:57:48 WARN: pgld dbus is already initialized.

Feb  8 13:57:48 ERROR: Cannot initialize D-Bus
Feb  8 14:00:26 INFO: Connected to dbus system bus.
Feb  8 14:00:26 INFO: Started.
Feb  8 14:00:26 INFO: ASCII: 134643 entries loaded from "/var/lib/pgl/master_blocklist.p2p"
Feb  8 14:00:26 INFO: Blocking 134643 IP ranges (835406860 IPs).
Feb  8 14:00:26 INFO: NFQUEUE: binding to queue 92
Feb  8 14:00:26 INFO: ACCEPT mark: 20
Feb  8 14:00:26 INFO: REJECT mark: 10
```I would say that the internet came back after 13:55, and was gone a few minutes prior to that.
I'm in the dark here and just fishing for some luck with what the heck's going on here.
Would be grateful for guidance at what to debug.

**Computer:** PC with installed Ubuntu 11.10 64-bit on SSD. /var/log mounted in ramdisk at bootup.

---

### Post by jre on 2012-03-30
Please see [here]("http://ubuntuforums.org/showpost.php?p=11805584&postcount=602") and previous posts. pgl 2.1.3 packages for oneiric/precise are broken. pgld dies after every reload, which happens e.g. after every automatic blocklist update, which happens shortly after boot.
The pglcmd.wd (watchdog) realizes this problem after 5 minutes and restarts pgl.

Until we have fixed that problem, try the natty packages.

---

