---
title: "Cannot ssh into ubuntu computer"
date: 2010-03-31
forum: Networking &amp; Wireless
---

### Post by them on 2010-03-31
I'm having a problem with my ubuntu 9.10 machine.
I can ssh out of the computer, but not in.
I have /etc/init.d/ssh, but not /etc/init.d/sshd - don't know if this is normal

If I run /etc/init.d/ssh status I get:
robot@cora:~$ sudo /etc/init.d/ssh status
 * could not access PID file for sshd

If I run /etc/init.d/ssh restart (or stop then start) then I can ssh both ways. But I cannot get this to work automatically at boot. The machine is going to be in a remote location, so I need the ability to ssh INTO it after reboot, which I don't have.

I have confirmed that start files are located in /etc/rc3.d/S16ssh

I've uninstalled and reinstalled openssh-server (via "apt-get remove openssh-server" and "apt-get install openssh-server") and this did not help.

There are both /etc/ssh/ssh_config and /etc/ssh/sshd_config files that look like they are standard (compared to what I've found from web searches). /etc/init.d/ssh is also standard.

Any one have any ideas? Thanks.

---

### Post by Schitso on 2010-03-31
What is the output of the following?
```
pgrep -l ssh
```

At bootup, that is.

---

### Post by Iowan on 2010-03-31
Peek inside /*etc/init.d/ssh* and you'll see:```
#! /bin/sh

### BEGIN INIT INFO
# Provides:             sshd
# Required-Start:       $network $local_fs $remote_fs
# Required-Stop:
# Default-Start:        2 3 4 5
# Default-Stop:         0 1 6
# Short-Description:    OpenBSD Secure Shell server
### END INIT INFO

```I also noticed no such file on my workstation. 
The (Hardy) server has:
/etc/rc1.d/K84ssh
/etc/rc2.d/S16ssh
/etc/rc3.d/S16ssh 
/etc/rc4.d/S16ssh 
/etc/rc5.d/S16ssh

---

### Post by them on 2010-04-01
> **Schitso said:**
> What is the output of the following?
```
pgrep -l ssh
```At bootup, that is.


```
pgre -l ssh
> 1204 ssh-agent
```

---

### Post by mikewhatever on 2010-04-01
Have you installed the ssh-server package? Don't think it's there by default.

---

### Post by them on 2010-04-01
> **mikewhatever said:**
> Have you installed the ssh-server package? Don't think it's there by default.

I have openssh-server installed and I tried uninstalling and reinstalling it with no luck.

It looks like it's a problem with ssh starting up (as pointed out /etc/init.d/ssh -> sshd in ubuntu). I tried moving /etc/rc3.d/S16ssh to /etc/rc3.d/S99ssh (thinking that maybe the system was trying to startup ssh too early in the boot process), but no joy :(

---

### Post by Schitso on 2010-04-01
Hm. Have you verified that /etc/init.d/ssh and the rc.x ssh scripts are flagged as executable?

Edit: I guess they probably are, since you reinstalled it... Do you see anything about SSH when your computer is booting?

---

### Post by seangee on 2010-04-01
First thing I do when I install is```
 sudo apt-get install ssh
```
This should install both client and server

FWIW the second thing I do is edit /etc/ssh/sshd_config and set PermitRootLogin no - old habit ;)

---

### Post by them on 2010-04-20
**Solved** (but not in a good way)

After trying every iteration of (re)installing openssh-server via apt-get, modifying /etc/rcX.d files, using update-rc.d and even writing my own /etc/init.d/sshd file none of this worked.

What I had to do was this:

The computer auto-logs in as a user other than root.
Went into System->Preferences->Startup Applications
and added an ssh startup that runs '/usr/bin/sudo /etc/init.d/ssh start'

This finally worked, but isn't ideal since ssh starting is now dependent on the user auto-login. So if anyone has any other ideas or insights I'll still take them gladly.

---

