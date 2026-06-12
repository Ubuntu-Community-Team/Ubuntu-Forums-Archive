---
title: "mythbackend doesn't start correctly on boot"
date: 2008-01-08
forum: Mythbuntu
---

### Post by jpv on 2008-01-08
I'm probably doing something dumb, or have goofed something up, but I can't see it.

After my complete rebuild (see [http://ubuntuforums.org/showthread.php?t=658310](http://ubuntuforums.org/showthread.php?t=658310)), mythbackend won't start right when I reboot.  It starts, but it doesn't listen on any ports.  As soon as I do a restart then it *does* listen.  I can't find any relevant error messages or permission problems.

I know I could just add a restart command to rc.local, but that's ugly.  I'd rather fix the root cause, if anyone can give me a pointer.

Just after reboot:
[INDENT]
# pgrep -l myth
4653 mythbackend
5513 mythfrontend.re

# cat /var/run/mythtv/mythbackend.pid
4653

# netstat -lnp | grep '/my' 
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     4588/mysqld         
unix  2      [ ACC ]     STREAM     LISTENING     15704    4588/mysqld         /var/run/mysqld/mysqld.sock
[/INDENT]

Then restart:
[INDENT]
# /etc/init.d/mythtv-backend restart
Restarting MythTV server: mythbackend .
.

# pgrep -l myth
5513 mythfrontend.re
6241 mythbackend

# cat /var/run/mythtv/mythbackend.pid
6241

# netstat -lnp | grep '/my'
tcp        0      0 0.0.0.0:3306            0.0.0.0:*               LISTEN     4588/mysqld
tcp        0      0 0.0.0.0:6543            0.0.0.0:*               LISTEN     6241/mythbackend
tcp        0      0 0.0.0.0:6544            0.0.0.0:*               LISTEN     6241/mythbackend
udp        0      0 0.0.0.0:6549            0.0.0.0:*                          6241/mythbackend
udp        0      0 255.255.255.255:1900    0.0.0.0:*                          6241/mythbackend
udp        0      0 239.255.255.250:1900    0.0.0.0:*                          6241/mythbackend
unix  2      [ ACC ]     STREAM     LISTENING     15704    4588/mysqld         /var/run/mysqld/mysqld.sock
[/INDENT]


Mythfrontend and everything else starts fine, as far as I can tell.  I get a message from SSH about being unable to bind port 22 as it's already in use, but SSH is working fine, so not sure about that.  And NTP is listening on about 6 variations of port 123, which is about 4 too many (lo and eth0 IPv4 are fine).  Oh well.

---

### Post by jpv on 2008-01-12
Well, for not I've hacked-around the problem by editing the bottom of /etc/rc.local:

[INDENT]#exit 0

# Ugly work-around for mythbackend not starting correctly (2008-01-09)
/etc/init.d/mythtv-backend restart
[/INDENT]

It's very ugly, but it worked on my last test reboot, so...  I'd rather fix the root cause if I can ever find it...

---

### Post by superm1 on 2008-01-12
To me this would sound like an issue of the priorities of daemons that are starting.  Do you have a static address setup for your network card?  When you setup a static address, standard debian networking is used instead of NetworkManager.

If not, try to set one up.  In Hardy, the priority to mythbackend has been demoted to a lower number to give networking (NetworkManager) a longer time to come up.

---

### Post by jpv on 2008-01-16
> To me this would sound like an issue of the priorities of daemons that are starting.

I thought that too, so I added "$remote_fs $network" to "# Required-Start:" in /etc/init.d/mythtv-backend but it didn't help.


>  Do you have a static address setup for your network card? When you setup a static address, standard debian networking is used instead of NetworkManager.


 I am using DHCP with Network Manager, but now that you mention it I'm not sure why.  Maybe because the Mythbuntu installer didn't give me a choice?  Since I had to set up a fixed address for my frontend in DHCPd anyway, I did the same for the backend and called it a day.

I guess I can change that.  But shouldn't it still Just Work under DHCP?  I also don't get why I seem to be the only one with this problem.  I'd thing it would either work or it wouldn't... 


> If not, try to set one up. In Hardy, the priority to mythbackend has been demoted to a lower number to give networking (NetworkManager) a longer time to come up.

How do I change that number?  I'm confused because I have "# Default-Start:     24" yet:
[INDENT]/etc/rc0.d/K20mythtv-backend
/etc/rc1.d/K20mythtv-backend
/etc/rc2.d/S20mythtv-backend
/etc/rc3.d/S20mythtv-backend
/etc/rc4.d/S20mythtv-backend
/etc/rc5.d/S20mythtv-backend
/etc/rc6.d/K20mythtv-backend
[/INDENT]

Obviously I could go change the symlinks manually, but I'm interested to know how it's supposed to work.

---

### Post by vrix on 2008-01-26
I also encountered this problem that for some reason when after boot, then start the front end, I can't watch tv. It keeps on saying that the IP Address is not set up correctly or mythbackend was not started. The solution might be is to create a bash script executable file like this: 

```
#!/bin/bash

mythbackend | mythfrontend –service
```

It seems that mythbackend was not started during boot that's why we need to manually restart the backend like this: 

```
$sudo /etc/init.d/myth-backend restart
```

Hope this helps.

---

### Post by kentling on 2008-02-27
This may be a dead thread, but I seem to have had a similar problem on version 0.21 (from CVS).

I'm not sure if this is the 'right way' to do this, but I saw on the mythtv website that one could change the user that runs the backend daemon.  I Changed it to my login, and it boots right the first time; non of the above changes needed.

I wonder if this might explain what the other posters were noticing, with it working the second time, as it looked like they were running it that second time from their user account, not as the default 'mythtv' user.

I assume there is some kind of permissions problem, that I have access to some file that 'mythtv' user doesn't (we're both in mythtv group -- is there owner only permissions on something I own?), but until I have time to chase it down, I'm telling /etc/init.d/myth-backend to run the daemon as myself.

---

### Post by jubxie on 2008-02-28
Not sure if this is the problem for anyone here, but this is a specific problem with the HDhomeRun tuner. It seems to be a startup order issue. Delaying the start of mythbackend solves it.

[http://ubuntuforums.org/showthread.php?t=683389](http://ubuntuforums.org/showthread.php?t=683389)

---

### Post by superm1 on 2008-02-28
I've got an alternative solution to try.  Please make this file:  

/etc/network/if-up.d/mythtv-backend
```
#! /bin/sh
#Restart mythtv-backend automatically if the network
#goes down/up
set -e

# Don't bother to restart sshd when lo is configured.
if [ "$IFACE" = lo ]; then
    exit 0
fi

# Only run from ifup.
if [ "$MODE" != start ]; then
    exit 0
fi

#Only run if NetworkManager did this.
if [ "$METHOD" != "NetworkManager" ]; then
    exit 0
fi

echo "trying to start myth backend"
/etc/init.d/mythtv-backend restart || true

exit 0

```

Mark it executable (chmod +x) and reboot.  Should that work properly, then need to get some testing from folks not encountering the issue to see if it breaks anything.

---

### Post by gwynethh on 2008-03-30
> **superm1 said:**
> I've got an alternative solution to try.  Please make this file:  

/etc/network/if-up.d/mythtv-backend
```
#! /bin/sh
#Restart mythtv-backend automatically if the network
#goes down/up
set -e

# Don't bother to restart sshd when lo is configured.
if [ "$IFACE" = lo ]; then
    exit 0
fi

# Only run from ifup.
if [ "$MODE" != start ]; then
    exit 0
fi

#Only run if NetworkManager did this.
if [ "$METHOD" != "NetworkManager" ]; then
    exit 0
fi

echo "trying to start myth backend"
/etc/init.d/mythtv-backend restart || true

exit 0

```

Mark it executable (chmod +x) and reboot.  Should that work properly, then need to get some testing from folks not encountering the issue to see if it breaks anything.

So did this work for any/everyone? Being a noob with very limited mythbuntu experience I guess I will wait until 8.04 finalizes before I try Mythbuntu again.

---

