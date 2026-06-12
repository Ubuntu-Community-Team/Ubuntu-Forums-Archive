---
title: "Delaying start of Samba"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by FooAtari on 2010-01-24
I am currently using NFS to share files between Linux machines, however I think Samba is a better option for sharing with my single Windows PC.  Although I'm not sure which provides better performance.

However my computer sometimes hangs during boot due to the bug with nmbd, [https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169](https://bugs.launchpad.net/ubuntu/+source/samba/+bug/462169)

I have read that adding a Start 5 to the Samba init script to delay it starting until the network interfaces are up is a workaround for the problem.  However I ma not sure how to do this.

Can someone help me out with how to do this? Or would it be just as easy to setup an NFS client on the windows machine instead?

---

### Post by suseendran.rengabashyam on 2010-01-25
Hi,
       I guess one solution would be to start your SAMBA daemon from /etc/rc.local by doing the following:       

```
sudo update-rc.d -f samba remove
```and add the following to /etc/rc.local, just above "exit 0"
       

```
/etc/init.d/samba start
```Another best solution would be to update your SAMBA. The bug which  you had mentioned has been fixed in the latest release of SAMBA i.e in  samba (2:3.4.0-3ubuntu5.3).

---

### Post by FooAtari on 2010-01-25
Thanks for that. Will need to check I'm running latest Samba if problem persists will try your fix anyway.

---

