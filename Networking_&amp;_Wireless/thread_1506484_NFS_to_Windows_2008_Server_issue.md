---
title: "NFS to Windows 2008 Server issue"
date: 2010-06-10
forum: Networking &amp; Wireless
---

### Post by hicotton02 on 2010-06-10
Mornin' yall

Been having an issue with my mythbuntu 10.04 box connecting with my Windows Server 2008 running Services for NFS.
Here is my /etc/fstab:
```
# /etc/fstab: static file system information.
Hyperv:/Media   /mnt/mythtv     nfs     _netdev,nfsvers=3,rsize=8192,wsize=8192,tcp     0       0

```

Those options was from me messing around trying things out. This setup works intermittently. The problem is that it takes 5-10 minutes to mount. and so far it has taken 30 mins to try to browse. now I can restart mythbuntu and sometimes it will work right out of the gate, other times it takes forever. Even when it takes a long time, once the initial "ls" is ran, its running at 100%.

I ran wireshark to see if i could see what was going on because im not seeing anything in the logs except for "server timed out" And the servers NFS log just shows "mount suceeded" I have the packet dump saved if that would help but i dont know what to try next.

---

### Post by hicotton02 on 2010-06-10
changed the options to _netdev and thats it, looks like it is running better now, will continue to monitor. has anyone else even tried this?

---

