---
title: "Issues with Apache?"
date: 2008-01-12
forum: Mythbuntu
---

### Post by rusty0101 on 2008-01-12
I'm running into a bit of a problem with the apache2 server under Mythbuntu. Since I run the same server (I think) under my ubuntu server platform, I think the issue is not specific to the server, but may be related to a configuration issue under Mythbuntu.

I built a dual core platform to run Mythbuntu on and after a recent apt-get update/upgrade cycle, discovered I could no longer see my Mythtweb server from various locations. Any time I log into the server and try kicking off the apache2 server, my system seems to vanish. To try to diagnose the situation, I launched 'top' in one ssh session and in another ssh session I started apache2. The top portion of top gives me:

```

top - 20:54:17 up  1:36,  3 users,  load average: 488.33, 911.75, 33.46
Tasks: 27511 total,   2 running, 27509 sleeping,   0 stopped,   0 zombie
Cpu(s):  1.2%us, 85.4%sy,  0.0%ni,  0.2%id, 13.1%wa,  0.0%hi,  0.2%si,  0.0%st
Mem:   2067504k total,  2018336k used,    49168k free,      668k buffers
Swap:  2000084k total,  2000084k used,        0k free,     1784k cached

```

Needless to say the system seems a bit sluggish.

I sorted the output of top by pid, (higher pids will be at the top) and I see:

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND            
32767 root      17   0  4384  168    4 S    0  0.0   0:00.00 apport             
32766 root      11  -5     0    0    0 S    0  0.0   0:00.00 khelper            
32765 root      18   0  4388  168    4 S    0  0.0   0:00.00 apport             
32764 root      11  -5     0    0    0 S    0  0.0   0:00.00 khelper    

```

with the aport and khelper processes filling the rest of the listing. And yes, 'ps -ef' presents a screen filled with stuff like:
```

root      9566  9565  0 20:36 ?        00:00:00 /usr/bin/python /usr/share/appor
root      9567    11  0 20:36 ?        00:00:00 [khelper]
root      9568  9567  0 20:36 ?        00:00:00 /usr/bin/python /usr/share/appor
root      9569    11  0 20:36 ?        00:00:00 [khelper]

```

Eventually I start seeing messages about no resources available to fork if I try to run a command in a shell.

It looks like either /etc/init.d/apache2 or one of the other apps associated with apache is fork bombing my system. Based upon the output of ps, I'm thinking that the problem is in either /usr/share/apport, or a configuration file for apache. 

If the load average at the top of the output of top is confusing, I think it should be. The fact that I got any response at all, including a display out of top, with load averages in any of the timeframes that are in excess of 900 is impressive to me, much less a load that high.

Looking for help on what I should be looking for in that file to fix this.

Thank you.

-Rusty :confused:

---

### Post by rusty0101 on 2008-01-13
After a bit of digging, it appears that apport is a collection of tools for collecting information about applications that have crashed. Now I need to determine what app is crashing causing what looks like a fork bomb. I have done a re-install on php5-common, and apport, as they are apps that had 'crash' reports in /var/crash/, and have tried to do similarly for a few other packages, but I keep running into crashes like this.

---

### Post by rusty0101 on 2008-01-13
Well, it looks like the problem is not restricted to appache and related tools. I get similar results when I try to run the mythbuntu configuration tools from the setup screen. I would love to just go in and do a re-download all packages and remove-reinstall all of them on the off chance that when I had some bad memory in the system a package updated and was corrupted. At the moment none of the tv-tuner cards in the system are working, and so on. I can watch tv, so long as it's through an external hdhomerun tuner, or I can watch previously recorded programming, but nothing new gets recorded.

Would really like to see a revert function for packages, but I'm not sure that would work here. Looks like I'll have to reinstall from scratch and loose all the recordings I already have.

Kind of wondering where the instructions are for Mythbuntu Hardy Herron are, as they have already releasd alpha 3 of the Ubuntu release, and I know that alpha 2 recognized my network interface on the motherboard. (Would like to pull the usb-ethernet adapter...)

---

### Post by faginbagin on 2008-01-13
Hi Rusty,

While I can't help you figure out what's crashing, I have gone through a couple of O/S reinstalls involving mythtv. As long as your recordings are on a different partition than root, and you don't touch it when you reinstall the O/S and mysql isn't crashing, you should be able to backup and restore your recording data. See:
[http://mythtv.org/docs/mythtv-HOWTO-23.html](http://mythtv.org/docs/mythtv-HOWTO-23.html)
This chapter has two sections of interest:
23.5 "Saving or restoring the database"
23.7 "Moving your data to new hardware"
I've followed 23.7 when reinstalling and when I didn't trust the configurations I had done in the past, but did trust my recording data.

HTH

---

### Post by rusty0101 on 2008-01-15
Yep, that allowed me to restore my video content. It's a wait and see project now to see if the re-installation of Mythbuntu fixes the issue's I've had.

---

