---
title: "New freenx connection issue."
date: 2011-09-26
forum: Networking &amp; Wireless
---

### Post by odror on 2011-09-26
OS: Ubuntu 11.10
free-nx: version 0.73

I know that there are no deb files for my OS version. I compiled it from the source. it was working for about 3 weeks. in the last three days I was not able to connect. I get the following error:

> NX> 148 Server capacity: not reached for user: XXXX
NX> 105 startsession  --link="adsl" --backingstore="1" --encryption="1" --cache="16M" --images="64M" --shmem="1" --shpix="1" --strict="0" --composite="1" --media="0" --session="0922" --type="unix-kde" --geometry="1274x971" --client="winnt" --keyboard="pc102/en_US" --screeninfo="1274x971x32+render" 

NX> 1000 NXNODE - Version 3.2.0-73 OS (GPL, using backend: 3.5.0)
NX> 700 Session id: myserver-1000-525F81FC59EAF1B5BDAF7F60AD4808FD
NX> 705 Session display: 1000
NX> 703 Session type: unix-kde
NX> 701 Proxy cookie: 45427efe4cf4714bcd860d82a56ff561
NX> 702 Proxy IP: 127.0.0.1
NX> 706 Agent cookie: 45427efe4cf4714bcd860d82a56ff561
NX> 704 Session cache: unix-kde
NX> 707 SSL tunneling: 1
/usr/NX/bin/nxserver: line 1531: 32732 Terminated              sleep $AGENT_STARTUP_TIMEOUT
NX> 105 NX> 596 Session startup failed.
NX> 1004 Error: NX Agent exited with exit status 1. To troubleshoot set SESSION_LOG_CLEAN=0 in node.conf and investigate "/home/XXXX/.nx/F-C-myserver-1000-525F81FC59EAF1B5BDAF7F60AD4808FD/session". You might also want to try: ssh -X myserver; /usr/NX/bin/nxnode --agent to test the basic functionality. Session log follows:
NX> 1006 Session status: closed
NX> 1001 Bye.
Can't open /usr/NX/var/db/running/sessionId{525F81FC59EAF1B5BDAF7F60AD4808FD}: No such file or directory.
mv: cannot stat `/usr/NX/var/db/running/sessionId{525F81FC59EAF1B5BDAF7F60AD4808FD}': No such file or directory
/usr/NX/bin/nxserver: line 562: kill: (32356) - No such process
NX> 280 Exiting on signal: 15


Any help will be appreciated.

---

### Post by nandelbosc on 2011-10-14
The same here.

Did you solved it?

---

### Post by odror on 2011-10-14
Yes it is working now. I installed the tar files. I also deleted the .Xauthority files. Try the second one first. Let me know if it works.

---

### Post by nandelbosc on 2011-10-15
thank's, It's working now too.

But I installed the propietary deb files from nomachine. When I have time I invetigate more deeply what was happened.

---

### Post by odror on 2011-10-15
> **nandelbosc said:**
> thank's, It's working now too.

But I installed the propietary deb files from nomachine. When I have time I invetigate more deeply what was happened.

I tried the deb files, but for some reason it did not work for me. That is why I used the tar files.

---

