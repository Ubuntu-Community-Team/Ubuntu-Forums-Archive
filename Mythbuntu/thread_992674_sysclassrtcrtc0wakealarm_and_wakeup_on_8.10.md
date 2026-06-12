---
title: "/sys/class/rtc/rtc0/wakealarm and wakeup on 8.10"
date: 2008-11-25
forum: Mythbuntu
---

### Post by d_morgan on 2008-11-25
While trying to setup my system for wakeup following these [instructions]("https://help.ubuntu.com/community/MythTV/Install/WhatNext/ACPIWake") I run into a problem or possibly a bug.

When I try to modify the file /sys/class/rtc/rtc0/wakealarm I get a permission denied error.
```
sudo echo 0 > /sys/class/rtc/rtc0/wakealarm
bash: /sys/class/rtc/rtc0/wakealarm: Permission denied

```

The strange thing is that this command doesn't prompt me for the password with sudo (and not because I've entered my password previously).  I can open a brand new term and issue the command and it won't prompt me for a password.

/sys/class/rtc/rtc0 is a symbolic link on my system so i tried going directly to the hard path but it gives the same result.

I can  use nano to edit the file, and writing the file out works but when i open the file back up to see my edits they are gone.

Does anyone know if /sys/class/rtc/rtc0/wakealarm is a device file that is write only?

about my system...
Ubuntu 8.10 i386 desktop
mythtv-common:
  Installed: 0.21.0+fixes18722-0ubuntu1
frontend and backend installed on the same machine
dual boot with winxp (probably not relevant)
Shuttle SG33G5 motherboard/system
Phoenix BIOS
  I've tried wake from alarm enabled and disabled


...and a short shout out to say that mythtv, ubuntu, and mythbuntu folks are all great for their amazing opensource software.

---

### Post by evilg33k on 2008-11-25
What does your /etc/sudoers say for your user?

---

### Post by Milan Knizek on 2008-11-25
> **d_morgan said:**
> 

When I try to modify the file /sys/class/rtc/rtc0/wakealarm I get a permission denied error.
```
sudo echo 0 > /sys/class/rtc/rtc0/wakealarm
bash: /sys/class/rtc/rtc0/wakealarm: Permission denied

```

The strange thing is that this command doesn't prompt me for the password with sudo (and not because I've entered my password previously).  I can open a brand new term and issue the command and it won't prompt me for a password.


While I am not sure why you are not asked for a password (depends on your sudoers file), I still had issues to make rtc alarm working this way. I have read somewere that using sudo is not enough, you actually must be a root. (I cannot find the page anymore, so maybe I am wrong.)

For myself, I changed the ownership to root:mythtv and added group permission rights to the file and then there is no need to use sudo.

```

$ cat /etc/rc.local
chown root:mythtv /sys/class/rtc/rtc0/wakealarm
chmod 664 /sys/class/rtc/rtc0/wakealarm
exit 0

```

this file should already exist and it is run during start up of the computer.

---

### Post by friends on 2009-02-21
> **d_morgan said:**
> 
```
sudo echo 0 > /sys/class/rtc/rtc0/wakealarm
bash: /sys/class/rtc/rtc0/wakealarm: Permission denied

```


Just thought you might like to know this error is because the '>' in the above command has a low precedence. What you want it to do is sudo (echo 0 > /sys/...) but it is actually doing (sudo echo 0) > (/sys/...), so the redirection is done as a normal user and sudo never gets called. If you'd rather not change the permissions of /sys/... you could use
```
sudo bash -c "echo 0 > /sys/..."
```

---

