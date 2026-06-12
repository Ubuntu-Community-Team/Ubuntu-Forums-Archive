---
title: "nfs wont start"
date: 2010-11-03
forum: Networking &amp; Wireless
---

### Post by eyelessfade on 2010-11-03
When I run /etc/init.d/nfs-kernel-server I get:
```
 * Exporting directories for NFS kernel daemon...           [ OK ]
* Starting NFS kernel daemon 
rpc.nfsd: Setting version failed: errno 16 (Device or resource busy)
rpc.nfsd: writing fd to kernel failed: errno 13 (Permission denied)
rpc.nfsd: unable to set any sockets for nfs                       [fail]

``` 

In /var/log/messages I get
```
Nov  3 15:31:43 computer kernel: [  104.710475] svc: failed to register lockdv1 RPC service (errno 13).
Nov  3 15:35:08 computer kernel: [  309.205273] svc: failed to register lockdv1 RPC service (errno 13).
```

I got this in 10.04, and I still get it in 10.10.
It doesn't matter if /etc/exports is populated or not.

---

### Post by SeijiSensei on 2010-11-03
Are you running "**sudo** /etc/init.d/nfs-kernel-server"?  You can't start this service as an ordinary user.  I'm guessing that's why you get those "permission denied" errors.

---

### Post by eyelessfade on 2010-11-04
yes. The message error wouldn't have occurred if I didn't.

---

### Post by Jose Catre-Vandis on 2010-11-04
```
sudo /etc/init.d/nfs-kernel-server start/restart/stop
```

Choose 1 of the three

---

### Post by eyelessfade on 2010-11-05
Wow. There really should be a "I am not a newbie" subforum.

For this thread to possibly to go further. Let us assume I have been using *nix for the last 12 years, and I am currently employed as a computer engineer dealing with *nix exclusively.

I have currently got NFS working by purging every last scrap of nfs related packages, and reinstalled them (Not dared to reboot). I have gotten it to work before, but it always goes away after a reboot. grub-update has been the only way to get it to work again after that, and not only did that work either.

---

### Post by Jose Catre-Vandis on 2010-11-05
Have you checked for the version of nfs being run. In 10.04 and 10.10 this was important for getting nfs to serve up shares, although admittedly it related more to exports and fstab entries in the client. given your experience you will already have this covered, no doubt? ;0)

Check the last couple of pages of the nfs howto on the forum:

[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)

---

### Post by james_fried on 2011-07-18
Just had this exact problem - didn't have people telling me to use `sudo` though ;)

Simple solution was to run `sudo dpkg-reconfigure portmap` and make sure that it wasn't loopbacked. A quick restart with `sudo /etc/init.d/portmap restart` then got NFS working just fine.

Hope that helps a googler.

J

---

### Post by aspora.isernia on 2011-08-02
> **james_fried said:**
> 
Hope that helps a googler.

J

It helped...
Thanks

---

### Post by mkilivan on 2011-08-08
> **james_fried said:**
> Just had this exact problem - didn't have people telling me to use `sudo` though ;)

Simple solution was to run `sudo dpkg-reconfigure portmap` and make sure that it wasn't loopbacked. A quick restart with `sudo /etc/init.d/portmap restart` then got NFS working just fine.

Hope that helps a googler.

J

It doesn't work for me. Do you have another suggestion?

---

### Post by meekamoo on 2011-09-14
I managed to get it working by disabling ipv6.

In /etc/hosts comment out the line that begins with ::1

---

### Post by AllGamer on 2012-01-31
> **james_fried said:**
> Just had this exact problem - didn't have people telling me to use `sudo` though ;)

Simple solution was to run `sudo dpkg-reconfigure portmap` and make sure that it wasn't loopbacked. A quick restart with `sudo /etc/init.d/portmap restart` then got NFS working just fine.

Hope that helps a googler.

J

Thank you!

yes arrived here via google and indeed 
sudo **dpkg-reconfigure portmap** was indeed the setting that was causing the issue (ubuntu 10.10)
ironically in ubuntu 11.10 there was no need to run that command nfs ran fine right off the bat after install

---

