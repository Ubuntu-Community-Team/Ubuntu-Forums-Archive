---
title: "100% CPU usage (1 thread) mythbackend and mythfrontend"
date: 2014-06-28
forum: Mythbuntu
---

### Post by westont on 2014-06-28
Within the last week my 14.04 mythbuntu system has started to have 100% CPU usage on two of the four cores. One is being used by mythbackend and the other by mythfrontend. This, of course, is not ideal.

Has anyone else experienced this?

My logs don't seem to have anything interesting or useful.

What do you need to diagnose this?

---

### Post by uteck on 2014-07-02
What process is taking up the cpu?  run: top -c
If you have commerce skip enabled, that might be it processing the recoding to find the commercials.

---

### Post by westont on 2014-07-04
> **uteck said:**
> What process is taking up the cpu?  run: top -c
If you have commerce skip enabled, that might be it processing the recoding to find the commercials.

Thanks for your time - htop is how I identified this. I know the commercial detection can use a decent amount, but that isn't whats going on here. 
I have an A10 AMD CPU with 4 cores, and two cores are being maxed, one by 1) mythbackend, and the other by 2) mythfrontend.real.

If I manually stop both, (exiting mythfrontend and "sudo stop mythtv-backend") then of course my cpu load drops near 0. If I then restart mythtv-backend, it stays around 15%-25% CPU usage for a while, then at some point jumps back up to 100% and stays there indefinitely.

I'd really like to fix this as it is causing my CPU temperature to stay much higher than I would prefer. I'm running 14.04 mythbuntu with 0.27 mythtv.

---

### Post by uteck on 2014-07-05
Try looking at what the process is doing in /proc.  From htop get the PID, then;
ls -l /proc/PID/
That might give you more info about what it is doing.

---

### Post by westont on 2014-07-07
Thanks! I am over my head with that command, here are the outputs:

Mythfrontend:
> 0 Jul  7 09:09 attr
0 Jul  7 09:09 autogroup
0 Jul  7 09:09 auxv
0 Jul  7 09:08 cgroup
0 Jul  7 09:09 clear_refs
0 Jul  6 11:03 cmdline
0 Jul  7 09:09 comm
0 Jul  7 09:09 coredump_filter
0 Jul  7 09:09 cpuset
0 Jul  6 11:09 cwd -> /
0 Jul  7 09:09 environ
0 Jul  6 11:03 exe -> /usr/bin/mythfrontend.real
0 Jul  6 11:09 fd
0 Jul  6 11:09 fdinfo
0 Jul  7 09:09 gid_map
0 Jul  7 09:08 io
0 Jul  7 09:09 latency
0 Jul  7 09:09 limits
0 Jul  7 09:09 loginuid
0 Jul  7 09:09 map_files
0 Jul  6 11:03 maps
0 Jul  7 09:09 mem
0 Jul  7 09:09 mountinfo
0 Jul  7 09:09 mounts
0 Jul  7 09:09 mountstats
0 Jul  7 09:09 net
0 Jul  7 09:09 ns
0 Jul  7 09:09 numa_maps
0 Jul  7 09:09 oom_adj
0 Jul  7 09:09 oom_score
0 Jul  7 09:09 oom_score_adj
0 Jul  7 09:09 pagemap
0 Jul  7 09:09 personality
0 Jul  7 09:09 projid_map
0 Jul  6 11:09 root -> /
0 Jul  7 09:09 sched
0 Jul  7 09:09 schedstat
0 Jul  7 09:09 sessionid
0 Jul  7 09:09 smaps
0 Jul  7 09:09 stack
0 Jul  6 11:03 stat
0 Jul  7 09:08 statm
0 Jul  7 09:08 status
0 Jul  7 09:09 syscall
0 Jul  7 09:08 task
0 Jul  7 09:09 timers
0 Jul  7 09:09 uid_map
0 Jul  7 09:09 wchan

mythbackend:
>  0 Jul  7 09:10 attr
 0 Jul  7 09:10 autogroup
 0 Jul  7 09:10 auxv
 0 Jul  7 09:08 cgroup
 0 Jul  7 09:10 clear_refs
 0 Jul  5 22:02 cmdline
 0 Jul  7 09:10 comm
 0 Jul  7 09:10 coredump_filter
 0 Jul  7 09:10 cpuset
 0 Jul  5 22:09 cwd -> /
 0 Jul  7 09:10 environ
 0 Jul  5 22:09 exe -> /usr/bin/mythbackend
 0 Jul  5 22:09 fd
 0 Jul  5 22:09 fdinfo
 0 Jul  7 09:10 gid_map
 0 Jul  7 09:08 io
 0 Jul  7 09:10 latency
 0 Jul  7 09:10 limits
 0 Jul  7 09:10 loginuid
 0 Jul  7 09:10 map_files
 0 Jul  5 22:09 maps
 0 Jul  7 09:10 mem
 0 Jul  7 09:10 mountinfo
 0 Jul  7 09:10 mounts
 0 Jul  7 09:10 mountstats
 0 Jul  7 09:10 net
 0 Jul  7 09:10 ns
 0 Jul  7 09:10 numa_maps
 0 Jul  7 09:10 oom_adj
 0 Jul  7 09:10 oom_score
 0 Jul  7 09:10 oom_score_adj
 0 Jul  7 09:10 pagemap
 0 Jul  7 09:10 personality
 0 Jul  7 09:10 projid_map
 0 Jul  5 22:09 root -> /
 0 Jul  7 09:10 sched
 0 Jul  7 09:10 schedstat
 0 Jul  7 09:10 sessionid
 0 Jul  7 09:10 smaps
 0 Jul  7 09:10 stack
 0 Jul  5 22:02 stat
 0 Jul  7 09:08 statm
 0 Jul  7 09:08 status
 0 Jul  7 09:10 syscall
 0 Jul  7 09:08 task
 0 Jul  7 09:10 timers
 0 Jul  7 09:10 uid_map
 0 Jul  7 09:10 wchan

Anything interesting there?

---

### Post by uteck on 2014-07-07
Not as helpful as I had hoped for.  Was the CPU maxed out then?
The other option is to tail the log and see what it is doing when it is 100%.
tail /var/log/mythtv/mythtv/mythbackend.log
tail -50 for the last 50 lines or tail -f to follow the log and print new lines as they are added to the log. control-c to exit.

Does the frontend unit have the accelerated video drivers installed?  If it is doing cpu rendering that would take 100%.

---

### Post by westont on 2014-07-07
Yes - thanks again for looking. So I've run mythtv for several years now, on 12.04 and now 14.04, and hadn't had this happen before about 2 weeks ago. 
Both of those procs are when the CPU is at 100% for mythbackend and 100% for mythfrontend, and neither are doing anything. mythbackend has no recordings happening, no processing needed at all. mythfrontend is sitting at the main menu, nothing else. I do have the open source AMD graphics drivers working and accelerated video working. Prior to whatever is causing this, mythfrontend was using less than 20% cpu when watching TV or videos, and near nothing when at the main menu (as expected).

The log is pretty worthless in my opinion, maybe I need to change the log level. This is while CPU usage is 100% on mythbackend, from the mythbackend.log:
> Jul  7 19:01:22 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 14 2014-07-08T23:30:00Z EITScanner
Jul  7 19:01:22 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:06:41 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 13 2014-07-08T11:30:00Z EITScanner
Jul  7 19:06:41 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:11:01 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 11 2014-07-08T11:00:00Z EITScanner
Jul  7 19:11:01 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:12:08 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 14 2014-07-08T23:30:00Z EITScanner
Jul  7 19:12:08 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.03 match + 0.00 check + 0.03 place
Jul  7 19:13:06 hda mythbackend: mythbackend[594]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 10.0 GB w/freq: 15 min
Jul  7 19:16:23 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 12 2014-07-08T11:30:00Z EITScanner
Jul  7 19:16:23 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:19:12 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 12 2014-07-08T11:30:00Z EITScanner
Jul  7 19:19:12 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:21:44 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 13 2014-07-08T11:30:00Z EITScanner
Jul  7 19:21:44 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:24:37 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 13 2014-07-08T11:30:00Z EITScanner
Jul  7 19:24:37 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:27:06 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 14 2014-07-08T23:30:00Z EITScanner
Jul  7 19:27:06 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:28:09 hda mythbackend: mythbackend[594]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 10.0 GB w/freq: 15 min
Jul  7 19:30:03 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 14 2014-07-08T23:30:00Z EITScanner
Jul  7 19:30:03 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:39:51 hda mythbackend: mythbackend[594]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Jul  7 19:39:51 hda mythbackend: mythbackend[594]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: hda as a client (events: 0)
Jul  7 19:39:55 hda mythbackend: mythbackend[594]: I ProcessRequest mainserver.cpp:1443 (HandleAnnounce) MainServer::ANN Monitor
Jul  7 19:39:55 hda mythbackend: mythbackend[594]: I ProcessRequest mainserver.cpp:1445 (HandleAnnounce) adding: hda as a client (events: 0)
Jul  7 19:41:34 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 11 2014-07-08T11:00:00Z EITScanner
Jul  7 19:41:34 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.00 check + 0.03 place
Jul  7 19:43:12 hda mythbackend: mythbackend[594]: N Expire autoexpire.cpp:264 (CalcParams) AutoExpire: CalcParams(): Max required Free Space: 10.0 GB w/freq: 15 min
Jul  7 19:43:53 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2139 (HandleReschedule) Reschedule requested for MATCH 0 2 10 2014-07-12T23:30:00Z EITScanner
Jul  7 19:43:53 hda mythbackend: mythbackend[594]: I Scheduler scheduler.cpp:2252 (HandleReschedule) Scheduled 55 items in 0.1 = 0.02 match + 0.01 check + 0.03 place

---

### Post by uteck on 2014-07-12
Not informative at all.  Another option might be the database is tossing an error and making mythbackend do some extra work/  Tail -30 /var/log/mythtv/mythtvbackend I think should read the last 30 lines.  Might be a crashed table that needs repair?

---

### Post by neutron68 on 2014-12-20
A similar situation is occurring for a few of us with the mythfrontend.re process:

[http://ubuntuforums.org/showthread.php?t=2251955](http://ubuntuforums.org/showthread.php?t=2251955)
[https://forum.mythtv.org/viewtopic.php?f=36&t=496](https://forum.mythtv.org/viewtopic.php?f=36&t=496)

---

