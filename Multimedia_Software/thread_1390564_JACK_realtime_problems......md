---
title: "JACK realtime problems....."
date: 2010-01-25
forum: Multimedia Software
---

### Post by rookworm on 2010-01-25
Hello all.

Simple problem here: I'm trying to run JACK using realtime priority on Ubuntu Studio 9.10. I have searched the forums, and applied everything I read.

This is my /etc/security/limits.conf :

```
# /etc/security/limits.conf
#
#Each line describes a limit for a user in the form:
#
#<domain>        <type>  <item>  <value>
#
#Where:
#<domain> can be:
#        - an user name
#        - a group name, with @group syntax
#        - the wildcard *, for default entry
#        - the wildcard %, can be also used with %group syntax,
#                 for maxlogin limit
#        - NOTE: group and wildcard limits are not applied to root.
#          To apply a limit to the root user, <domain> must be
#          the literal username root.
#
#<type> can have the two values:
#        - "soft" for enforcing the soft limits
#        - "hard" for enforcing hard limits
#
#<item> can be one of the following:
#        - core - limits the core file size (KB)
#        - data - max data size (KB)
#        - fsize - maximum filesize (KB)
#        - memlock - max locked-in-memory address space (KB)
#        - nofile - max number of open files
#        - rss - max resident set size (KB)
#        - stack - max stack size (KB)
#        - cpu - max CPU time (MIN)
#        - nproc - max number of processes
#        - as - address space limit (KB)
#        - maxlogins - max number of logins for this user
#        - maxsyslogins - max number of logins on the system
#        - priority - the priority to run user process with
#        - locks - max number of file locks the user can hold
#        - sigpending - max number of pending signals
#        - msgqueue - max memory used by POSIX message queues (bytes)
#        - nice - max nice priority allowed to raise to values: [-20, 19]
#        - rtprio - max realtime priority
#        - chroot - change root to directory (Debian-specific)
#
#<domain>      <type>  <item>         <value>
#

#*               soft    core            0
#root            hard    core            100000
#*               hard    rss             10000
#@student        hard    nproc           20
#@faculty        soft    nproc           20
#@faculty        hard    nproc           50
#ftp             hard    nproc           0
#ftp             -       chroot          /ftp
#@student        -       maxlogins       4

@audio          -       rtprio          99


@audio - memlock 509290

@audio - nice -10
# End of file
```

This is what Jack has to say about things:

```
19:39:24.637 Startup script...
19:39:24.640 artsshell -q terminate
sh: artsshell: not found
19:39:25.042 Startup script terminated with exit status=32512.
19:39:25.043 JACK is starting...
19:39:25.043 /usr/bin/jackd -R -dalsa -dhw:0 -r44100 -p1024 -n2
19:39:25.061 JACK was started with PID=3264.
no message buffer overruns
jackd 0.116.1
Copyright 2001-2005 Paul Davis and others.
jackd comes with ABSOLUTELY NO WARRANTY
This is free software, and you are welcome to redistribute it
under certain conditions; see the file COPYING for details
JACK compiled with System V SHM support.
cannot use real-time scheduling (FIFO at priority 10) [for thread -1215908160, from thread -1215908160] (1: Operation not permitted)
cannot create engine
19:39:25.143 JACK was stopped successfully.
19:39:25.144 Post-shutdown script...
19:39:25.144 killall jackd
jackd: no process found
19:39:25.555 Post-shutdown script terminated with exit status=256.
19:39:27.132 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.
```

uname -a  :

```
Linux faptop 2.6.31-9-rt #152-Ubuntu SMP PREEMPT RT Thu Oct 15 05:01:14 UTC 2009 i686 GNU/Linux

```

seems to work if i run JACK as root, but then none of the apps seem to interface with it.

what am I doing wrong?

---

### Post by rookworm on 2010-01-30
added self to group "audio" fixed problem

---

