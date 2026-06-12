---
title: "How do you make Nagios3 alert on a 0 threshold"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by RainyCity on 2011-08-15
I have a hopefully simple problem. I have a process that needs to run all the time and sometimes it fails silently. I have Nagios3 installed on a server and it's doing NRPE checks on the target machine and it can see the process in question. I can set alerts to for values that are greater than the current state but how do I set an alert for less than the current state?

Example okay state:
PROCS OK: 1 processes with args 'test', command name 'example'

Example critical state:
PROCS OK: 0 processes with args 'test', command name 'example'

Current NRPE command on target server:
command[check_procs]=/usr/lib/nagios/plugins/check_procs -a test -C example

---

