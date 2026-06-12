---
title: "Selective automatic mounting of cifs shares"
date: 2009-05-20
forum: Networking &amp; Wireless
---

### Post by veloce on 2009-05-20
Since upgrading to Jaunty, I've noticed a long delay in starting up my laptop when I'm not connected to the work network.  During the delay I get three long pauses with a CIFS connection error after each.  I am assuming this is caused by the attempt to mount the cifs shares that I use when connected to work.

What I'd like is a way of suppressing the attempt to connect if the server isn't available (e.g. it can't be pinged).

Anyone know where to start on this?  Can I just modify the startup script somewhere?

Is there a better way of defining the automatic mounting so that it doesn't have to time out to prove it's not available?

---

### Post by veloce on 2009-05-26
Bump?

---

### Post by dmizer on 2009-05-26
What is your fstab mount line for your CIFS share?

---

### Post by Iowan on 2009-05-26
> **dmizer said:**
> What is your fstab mount line for your NFS share? Also, please post /etc/exports from the server.

NFS... or CIFS???

---

### Post by dmizer on 2009-05-26
> **Iowan said:**
> NFS... or CIFS???

Note to self: NEVER post before having coffee :(

---

### Post by veloce on 2009-05-26
```
//hera/CokeDrive /Music cifs defaults,credentials=/home/.smbpwdOlympus,umask=0000 0 0

```

I've also just realised that I have 10 shares in the list (6 from 1 server 4 from another) but I definitely don't get 10 errors.  I can't see any differences between the fstab lines other than location and mount point of course.

---

### Post by Boondoklife on 2009-05-26
> **veloce said:**
> ```
//hera/CokeDrive /Music cifs defaults,credentials=/home/.smbpwdOlympus,umask=0000 0 0

```I've also just realised that I have 10 shares in the list (6 from 1 server 4 from another) but I definitely don't get 10 errors.  I can't see any differences between the fstab lines other than location and mount point of course.


I personaly mount my drives the same way, but you could also look into using /etc/NetworkManager/dispatcher.d and putting a script in there to try to ping the server and connect the drives if the ping was true.

here is what I use in my fstab
```
//server/public /media/public cifs auto,user,credentials=/root/.credentials,iocharset=utf8,dir_mode=0666,file_mode=0777 0 0
```

---

### Post by dmizer on 2009-05-26
> **veloce said:**
> ```
//hera/CokeDrive /Music cifs defaults,credentials=/home/.smbpwdOlympus,umask=0000 0 0

```

I've also just realised that I have 10 shares in the list (6 from 1 server 4 from another) but I definitely don't get 10 errors.  I can't see any differences between the fstab lines other than location and mount point of course.

Are all of your shares available once you're logged in? What type of network connection do you use? Also, please attach (as text documents) the smb.conf files of the two servers.

---

### Post by veloce on 2009-05-27
When I am connected at work (ethernet) everything works nicely, all the shares are mounted in the appropriate place and it all happens nice and quickly.

It's when I'm not connected to the network that I get this really annoying, go and make a cuppa, delay.  (It's really annoying if I am at a clients - it's bad enough have to do two start up procedures - one for linux, one for the windows vm!)

(I don't have a login to the servers so can't give the smb.conf for them but it's not when I can connect that's the problem.)

Sounds like I need to investigate maletek's idea as a place to put a script.  I want to keep the lines in fstab but make it a manual mount so that if I connect to the network via our vpn I can still mount them easily.

---

### Post by dmizer on 2009-05-27
> **veloce said:**
> When I am connected at work (ethernet) everything works nicely, all the shares are mounted in the appropriate place and it all happens nice and quickly.

It's when I'm not connected to the network that I get this really annoying, go and make a cuppa, delay.  (It's really annoying if I am at a clients - it's bad enough have to do two start up procedures - one for linux, one for the windows vm!)

(I don't have a login to the servers so can't give the smb.conf for them but it's not when I can connect that's the problem.)

Sounds like I need to investigate maletek's idea as a place to put a script.  I want to keep the lines in fstab but make it a manual mount so that if I connect to the network via our vpn I can still mount them easily.

As a possible workaround (not a fix), add the "noauto" option to your shares. Then add "mount -a" to /etc/rc.local so it looks like this:
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

[COLOR="Red"]mount -a[/COLOR]
exit 0
```

---

