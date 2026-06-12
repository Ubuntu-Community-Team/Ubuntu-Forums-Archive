---
title: "NFS common utilities and NFS kernel daemon hangs on startup"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by nimonika on 2009-01-23
I am having problems at startup where the NFS common utilities fail and the NFS kernel daemon takes forever before ubuntu can startup. Please can someone help.

Thanks

---

### Post by dmizer on 2009-01-23
This is a common work around for the problem you are experiencing:

1) add the "[COLOR="Blue"]noauto[/COLOR]" option to your fstab line like so:
```
server:/share/path [COLOR="Red"]/mount/point[/COLOR] nfs [COLOR="Blue"]noauto[/COLOR],rsize=8192,wsize=8192,timeo=14,intr
```

2) as root (sudo or gksudo), edit /etc/rc.local and add your mount point (in red from fstab) so that the file looks like this:
```
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.

mount [COLOR="Red"]/mount/point[/COLOR]
exit 0

```

---

### Post by Lampi on 2009-02-13
That's one way to do so, here's a better one from [bug.report]("https://bugs.launchpad.net/ubuntu/+source/sysvinit/+bug/285013"):

> 
*Marcus Comstedt wrote on 2008-11-09:*
[...]
"Added the line "ASYNCMOUNTNFS=no" to the end of /etc/default/rcS"
now the fstab entries work again - I guess the nfs mount script kicks in too soon.

---

### Post by leatherman on 2009-02-14
I have something similar, but I'm not sure if it's the same issue.  I have tried all fixes in this thread but none of them solve my particular problem.

Booting up, my nfs mounts hang and after about a minute fail (I have four, only the first one hangs, the rest fail right away).  This also affects shutdown and reboot, both eventually just display a blank screen with a curser, I have to hit the reset button to get the machine to cycle.  The difference I guess is that I don't have to manually mount the drives after startup, they are mounted when I check, even though it says they failed.  

After searching around and finding nothing, my room mate suggested looking at the /etc/network/interfaces file.  it looked like this:
```

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# The primary network interface
auto eth0
#iface eth0 inet dhcp
```

I removed the comment in front of "iface eth0 inet dhcp" and restarted.  This time, the first two nfs mounts mounted fine, but ntp then started to hang, again, taking about a minute before it failed.  The second two nfs mounts load fine.  The system then started fine.  I then restarted to check that error, and it restarted fine.  I didn't have to hit the reset button to get it to cycle.  Shutdown worked as well.

The ntp service was then causing issues.  So I went into /etc/NetworkManager/nm-system-settings.conf and it was this:
```

[main]
plugins=ifupdown,keyfile

[ifupdown]
managed=false
```
So I changed the managed=false to true.  Restart.  NTP error is now gone, but the nfs mounts are hanging again.  I switch that back.  I then decided that NTP wasn't worth the hassle, so I removed NTP, and restarted.  This time, the first nfs mount worked fine, but then the second one hung and failed, as did the third and fourth.  So I reinstalled NTP.  I have no idea of what is going on here.  I'd consider myself a linux newb even though I have been using it for 7 years, and I wouldn't have gotten this far if not for my room mate, but he's stumped too.  

I don't think hardware is the issue as I have a seperate box with mythbuntu 8.10 installed on it, and it has the same issue.  The strange part is that my room mate has a myth setup as well, with 8.10 installed, but it doesn't have this issue.:confused:

Any help would be appreciated.

---

