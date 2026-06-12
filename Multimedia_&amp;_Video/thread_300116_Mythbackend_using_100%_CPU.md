---
title: "Mythbackend using 100% CPU"
date: 2006-11-15
forum: Multimedia &amp; Video
---

### Post by tawsi on 2006-11-15
Before posting it as a bug I thought I'd better ask on here in case its something I've misconfigured.

I'm using mythtv for the mythvideo plugin (not got a tuner in the PC). Most of the time it works great but I've noticed that after a while (hours normally) mythbackend starts to sit at 100% cpu usage. Is this a normal for mythbackend?

---

### Post by dannyboy79 on 2006-11-15
could you explian to me why you are using the mthtc backend if you don't have a tv card? i mean what does the mythvideo plugin allow you to do?

---

### Post by superm1 on 2006-11-15
Well this shouldn't really be occurring especially without a tuner card.  If you can run the backend with some verbosity switches, and this is happening consistently - that'd be the ideal way to debug it.

Edit /etc/default/mythtv-backend.  Add any switches for verbosity there.  

Restart the backend process with 
```
sudo /etc/init.d/mythtv-backend restart
```

dannyboy-
Mythvideo is a plugin for mythtv's frontend.  It allows you browse videos that you have stored in a folder and launch them from mythtv in an external player or in the internal frontend viewer.

---

### Post by tawsi on 2006-11-16
I've set the verbose setting to all so hopefully when it next happens something will stand out. It's been pretty consistent, I've had to restart the backend almost daily since I set it up a couple of weeks ago.

---

### Post by tawsi on 2006-11-24
Unfortunately the log doesn't show anything different happening when it's using 100% cpu. However, for my purposes disabling the backend doesn't seem to cause any problems.

---

### Post by superm1 on 2006-11-24
Perhaps its just an issue caused when a master backend doesn't have any tuners for it.  If just disabling the backend solves it for you, i'll hold off until I hear of someone else with this problem before reporting it upstream.

---

### Post by grunties on 2006-11-28
I've heard of this problem, and am currently having it with a mythtv installation.

The computer is a 1.6Ghz p4, 1gb ram, with 3 40gb drives, hauppauge 150, and mythtv drive/mount formatted as reiserfs.  Here is the last output from mythbackend.log:

2006-11-28 07:43:57.197 MainServer::HandleAnnounce Monitor
2006-11-28 07:43:57.365 adding: desktop as a client (events: 0)
2006-11-28 07:43:57.402 MainServer::HandleAnnounce Monitor
2006-11-28 07:43:57.403 adding: desktop as a client (events: 1)
2006-11-28 07:43:57.503 Reschedule requested for id -1.
2006-11-28 07:43:57.882 Scheduled 7 items in 0.4 = 0.23 match + 0.15 place
2006-11-28 10:31:21.306 MainServer::HandleAnnounce Monitor
2006-11-28 10:31:21.312 adding: desktop as a client (events: 0)
2006-11-28 10:31:24.805 MainServer::HandleAnnounce Monitor
2006-11-28 10:31:24.808 adding: desktop as a client (events: 0)
2006-11-28 10:31:30.091 MainServer::HandleAnnounce Monitor
2006-11-28 10:31:30.092 adding: desktop as a client (events: 0)
2006-11-28 10:31:35.772 MainServer::HandleAnnounce Monitor
2006-11-28 10:31:35.796 adding: desktop as a client (events: 0)
2006-11-28 12:11:27.379 MainServer::HandleAnnounce Monitor
2006-11-28 12:11:27.388 adding: desktop as a client (events: 0)
2006-11-28 12:11:37.668 MainServer::HandleAnnounce Monitor
2006-11-28 12:11:37.670 adding: desktop as a client (events: 0)
2006-11-28 12:12:40.290 MainServer::HandleAnnounce Monitor
2006-11-28 12:12:40.292 adding: desktop as a client (events: 0)
2006-11-28 12:12:57.503 MainServer::HandleAnnounce Monitor
2006-11-28 12:12:57.505 adding: desktop as a client (events: 0)
2006-11-28 12:12:57.763 Reschedule requested for id 56.
2006-11-28 12:12:58.007 Scheduled 8 items in 0.2 = 0.22 match + 0.03 place
2006-11-28 12:13:12.328 MainServer::HandleAnnounce Monitor
2006-11-28 12:13:12.332 adding: desktop as a client (events: 0)
2006-11-28 19:22:02.518 MainServer::HandleAnnounce Monitor
2006-11-28 19:22:02.523 adding: desktop as a client (events: 0)
2006-11-28 19:22:24.502 MainServer::HandleAnnounce Monitor
2006-11-28 19:22:24.538 adding: desktop as a client (events: 0)
2006-11-28 19:22:42.007 MainServer::HandleAnnounce Monitor
2006-11-28 19:22:42.009 adding: desktop as a client (events: 0)
2006-11-28 19:23:33.916 MainServer::HandleAnnounce Monitor
2006-11-28 19:23:33.918 adding: desktop as a client (events: 0)
2006-11-28 19:23:50.819 MainServer::HandleAnnounce Monitor
2006-11-28 19:23:50.821 adding: desktop as a client (events: 0)


This is the usual top when not recording

top - 19:29:03 up 1 day,  3:38,  2 users,  load average: 1.12, 1.27, 1.24
Tasks:  72 total,   1 running,  71 sleeping,   0 stopped,   0 zombie
Cpu(s): 27.1%us, 41.4%sy,  1.8%ni,  8.1%id,  0.1%wa,  0.0%hi, 21.6%si,  0.0%st
Mem:   1035488k total,  1017112k used,    18376k free,    81080k buffers
Swap:  1614492k total,    17640k used,  1596852k free,   768468k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
 5574 mythtv    15   0  236m  35m  12m S 97.9  3.5   1487:02 mythbackend
    1 root      16   0  1632  536  448 S  0.0  0.1   0:01.42 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0
    3 root      34  19     0    0    0 S  0.0  0.0   0:00.00 ksoftirqd/0
    4 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 watchdog/0
    5 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 events/0
    6 root      10  -5     0    0    0 S  0.0  0.0   0:00.01 khelper
    7 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kthread
    9 root      10  -5     0    0    0 S  0.0  0.0   0:00.09 kblockd/0
   10 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpid
   11 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 kacpi_notify
   83 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 kseriod
  116 root      15   0     0    0    0 S  0.0  0.0   0:00.00 pdflush
  117 root      15   0     0    0    0 S  0.0  0.0   0:00.37 pdflush
  118 root      15   0     0    0    0 S  0.0  0.0   0:00.57 kswapd0
  119 root      20  -5     0    0    0 S  0.0  0.0   0:00.00 aio/0
 1747 root      10  -5     0    0    0 S  0.0  0.0   0:00.00 khubd


I saw a post a while back about acpi (apic?) being enabled and taking the system resources incorrectly.  I'm not sure how to disable that in the startup kernel parameters, so when it exausts the resources for some time, and then it crashes, I just hit the button and reboot it.

Installed:

ii  libmyth-0.20                               0.20-0.2ubuntu2                   Common library code for MythTV and add-on mo
ii  mythtv                                     0.20-0.2ubuntu2                   A personal video recorder application (clien
ii  mythtv-backend                             0.20-0.2ubuntu2                   A personal video recorder application (serve
ii  mythtv-common                              0.20-0.2ubuntu2                   A personal video recorder application (commo
ii  mythtv-database                            0.20-0.2ubuntu2                   A personal video recorder application (datab
ii  mythtv-frontend                            0.20-0.2ubuntu2                   A personal video recorder application (clien
ii  mythtv-themes                              0.20-0.1                          Additional themes for MythTV
ii  mythweb                                    0.20-0.6ubuntu4                   Web interface add-on module for MythTV



Anyone else know?

---

### Post by superm1 on 2006-11-29
Well to boot with noapic or acpi=off

At the grub boot screen hit e to edit the line you would be booting

add **noapic** to the end or **acpi=off** to the end.

Hit b to boot.  This is a one time only thing, if it works well for you then you can edit grub.conf to make it permanent.

---

### Post by hesoez on 2006-11-29
The backend is only necessary if you want to use a tv-card, mythvideo, mythmusic, mythdvd, ... will all work. You will have to setup your database and configure mythfrontend to use it.

---

### Post by grunties on 2006-12-12
[http://www.gossamer-threads.com/lists/mythtv/commits/226024?page=last](http://www.gossamer-threads.com/lists/mythtv/commits/226024?page=last)

It looks like a bug in MythTV.  There is a workaround and a fix as described in the article.

G

---

### Post by superm1 on 2006-12-12
As it appears, running with --no-upnp solves this for the people having the issue.  The proper patched release will be released to feisty eventually and hopefully backported.

---

### Post by mraudiofreak on 2007-02-20
What are you supposed to run with --no-upnp? I can't seem to run it with mythbackend and I don't really know where else to look. I searched the forums but didn't find anything. A specific command would be nice.
Also, will running without upnp in this way disable networking on my machine? Will it disable any important features in myth, such as guide data retrevial?
Thanks

---

### Post by superm1 on 2007-02-20
> **mraudiofreak said:**
> What are you supposed to run with --no-upnp? I can't seem to run it with mythbackend and I don't really know where else to look. I searched the forums but didn't find anything. A specific command would be nice.
Also, will running without upnp in this way disable networking on my machine? Will it disable any important features in myth, such as guide data retrevial?
Thanks
Edit /etc/default/mythtv-backend
Add the following line:
```
ARGS="--noupnp"
```
Restart the backend process
```
sudo /etc/init.d/mythtv-backend restart
```
It won't disable any networking of the machine other than streaming to UPNP compat devices.

---

### Post by superm1 on 2007-02-20
Correction:

make 
ARGS="--noupnp"
be 
EXTRA_ARGS="--noupnp"

---

### Post by GrammatonCleric on 2007-02-22
Not sure if I'm doing something wrong but I get the following when I try to disable upnp using what you have listed above....


```


Starting MythTV server: mythbackendInvalid argument: --noupnp


```

---

### Post by superm1 on 2007-02-22
> **GrammatonCleric said:**
> Not sure if I'm doing something wrong but I get the following when I try to disable upnp using what you have listed above....


```


Starting MythTV server: mythbackendInvalid argument: --noupnp


```
I don't recall the exact commit that included upnp, but my guess would be that you are on an older 0.20-fixes (edgy's release was an older snapshot).
I have a newer edgy snapshot at [http://home.eng.iastate.edu/~superm1/dists/edgy](http://home.eng.iastate.edu/~superm1/dists/edgy)

---

