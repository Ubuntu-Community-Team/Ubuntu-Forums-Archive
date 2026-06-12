---
title: "Jack  will not start in realtime"
date: 2010-11-01
forum: Multimedia Software
---

### Post by buddykoerner on 2010-11-01
Hello,

I am not able to start JACK in realtime mode. This is a bummer. here is the error message I get:

p, li { white-space: pre-wrap; } [COLOR=#999999]11:58:20.745 Patchbay deactivated.[/COLOR]
 [COLOR=#999999]11:58:20.746 Statistics reset.[/COLOR]
 [COLOR=#66cc99]11:58:20.812 ALSA connection graph change.[/COLOR]
 [COLOR=#cccc99]11:58:21.008 ALSA connection change.[/COLOR]
 [COLOR=#999999]11:58:24.082 Startup script...[/COLOR]
 [COLOR=#990099]11:58:24.084 artsshell -q terminate[/COLOR]
 sh: artsshell: not found
 [COLOR=#999999]11:58:24.487 Startup script terminated with exit status=32512.[/COLOR]
 [COLOR=#999999]11:58:24.487 JACK is starting...[/COLOR]
 [COLOR=#990099]11:58:24.488 /usr/bin/jackd -dalsa -r44100 -p1024 -n2 -D -Chw:1 -Phw:1[/COLOR]
 [COLOR=#999999]11:58:24.491 JACK was started with PID=2485.[/COLOR]
 jackd 0.118.0
 Copyright 2001-2009 Paul Davis, Stephane Letz, Jack O'Quinn, Torben Hohn and others.
 jackd comes with ABSOLUTELY NO WARRANTY
 This is free software, and you are welcome to redistribute it
 under certain conditions; see the file COPYING for details
 JACK is running in realtime mode, but you are not allowed to use realtime scheduling.
 Please check your /etc/security/limits.conf for the following lines
 and correct/add them:
   @audio          -       rtprio          100
   @audio          -       nice            -10
 After applying these changes, please re-login in order for them to take effect.
 You don't appear to have a sane system configuration. It is very likely that you
 encounter xruns. Please apply all the above mentioned changes and start jack again!
 [COLOR=#999999]11:58:24.531 JACK was stopped with exit status=255.[/COLOR]
 [COLOR=#999999]11:58:24.532 Post-shutdown script...[/COLOR]
 [COLOR=#990099]11:58:24.532 killall jackd[/COLOR]
 jackd: no process found
 [COLOR=#999999]11:58:24.941 Post-shutdown script terminated with exit status=256.[/COLOR]
 [COLOR=#ff0000]11:58:26.631 Could not connect to JACK server as client. - Overall operation failed. - Unable to connect to server. Please check the messages window for more info.[/COLOR]




When I open  /etc/security/limits.conf there is no line for @audio. this is what my file looks like:




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

# End of file






Should I add the @audio in? i dont want to make the problem worse...


please help.


thanks,
-buddy

[COLOR=#ff0000]
[/COLOR]

---

### Post by lisati on 2010-11-01
Duplicate of [http://ubuntuforums.org/showthread.php?t=1610998](http://ubuntuforums.org/showthread.php?t=1610998)

Please do not start dupilcate threads.

---

