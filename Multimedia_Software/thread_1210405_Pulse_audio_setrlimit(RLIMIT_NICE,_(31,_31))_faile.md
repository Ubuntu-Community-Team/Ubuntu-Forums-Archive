---
title: "Pulse audio setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted"
date: 2009-07-11
forum: Multimedia Software
---

### Post by redman5087 on 2009-07-11
Can anyone help, Im using ubuntu 9.04.
I have a problem with pulseaudio.

pulseaudio --start gives the following message.

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: main.c: setrlimit(RLIMIT_RTPRIO, (9, 9)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: Giving up CAP_NICE
E: main.c: Daemon startup failed.


I searched the forums but didn't find something that helps.
Can anyone help?

---

### Post by raboofje on 2009-07-11
could you paste your /etc/security/limits.conf file?

---

### Post by redman5087 on 2009-07-11
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

---

### Post by redman5087 on 2009-07-11
I added the following to /etc/security/limits.conf

@pulse-rt - rtprio 99
@pulse-rt - memlock 512000
@pulse-rt - nice 31

still no luck, doesn't work

someone can help?

---

### Post by redman5087 on 2009-07-11
I changed the following

@pulse-rt - rtprio 99
@pulse-rt - memlock 512000
@pulse-rt - nice -10

Now when I start pulseaudio --start I get the following

I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: caps.c: Dropping root privileges.
I: caps.c: Limited capabilities successfully to CAP_SYS_NICE.
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: RLIMIT_RTPRIO is set to 99, allowing real-time scheduling.
I: main.c: RLIMIT_NICE is set to 30, allowing high-priority scheduling.
I: main.c: setrlimit(RLIMIT_NICE, (31, 31)) failed: Operation not permitted
I: core-util.c: Successfully gained nice level -11.
I: main.c: Giving up CAP_NICE
E: main.c: Daemon startup failed.

---

### Post by raboofje on 2009-07-11
So I guess this fixed the 'setrlimit(RLIMIT_RTPRIO...' error.

The messages are a bit puzzling. Not sure where that 30/31 comes from: nice values usually range from -20 to 19. Do you see that in the configuration anywhere?

---

### Post by redman5087 on 2009-07-11
I get the following message now

D: main.c: Started as real root: no, suid root: yes
I: main.c: We're in the group 'pulse-rt', allowing high-priority scheduling.
I: main.c: RLIMIT_RTPRIO is set to 99, allowing real-time scheduling.
I: main.c: RLIMIT_NICE is set to 35, allowing high-priority scheduling.
I: core-util.c: Successfully gained nice level -11.
D: main.c: Can realtime: yes, can high-priority: yes
I: main.c: Giving up CAP_NICE
D: main.c: Can realtime: yes, can high-priority: yes
E: main.c: Daemon startup failed.

I have no idea where it gets nice - 35

nice level /etc/pulse/daemon.conf is disabled

nice level /etc/security/limits.conf is set to -15

Strange

---

### Post by redman5087 on 2009-07-12
Can anyone help

---

### Post by raboofje on 2009-07-12
Hm, I don't even seen an error message there anymore :/

---

### Post by oliver69 on 2009-12-10
In Ubuntu 9.10 (Karmic) the group "pulse-rt" does not exist anymore and it is recommended anyway that the pulseaudio daemon runs in user-mode (not in system-mode).

A working solution for Karmic is comment #12 and #13 of [https://bugs.launchpad.net/bugs/265010](https://bugs.launchpad.net/bugs/265010)

---

