---
title: "Mounting nfs shares, OpenSolaris, VirtualBox"
date: 2009-09-14
forum: Networking &amp; Wireless
---

### Post by jirimracek on 2009-09-14
I run Ubuntu x64 as a VirtualBox host with several Ubuntu 32 bit guest machines and one OpenSolaris.  I export a few shares from the host to be nfs mounted on guest machines.  Works fine between Ubuntu machines, didn't work on OpenSolaris client and has been a source of major frustration.  Mostly I got "security mode does not match the server exporting" when trying to mount the shares.  
There is a very nice writeup [http://blogs.sun.com/tdh/entry/some_nasty_nfsv3_interactions_at](http://blogs.sun.com/tdh/entry/some_nasty_nfsv3_interactions_at) describing the problem as well as how to get the machines to talk to each other.

I figured I can't be the only one running into this problem and perhaps this will save someone a few hours of googling.

Jiri

---

### Post by ttabbal on 2009-10-23
I'm trying to do the reverse, opensolaris server Ubuntu 9.04 client. I can't get nfs mounts to work. I keep getting "mount.nfs: access denied by server while mounting <mountpoint>". This is with command line mount and with autofs. Anyone have any idea what's up? I tried -o sec=sys on the mount line, but that seems to apply more to solaris clients than servers.

---

### Post by ttabbal on 2009-10-23
Found a fix for my issue. OpenSolaris has an NFS bug that requires a reverse name lookup. For static IP machines, add them to /etc/hosts on the OpenSolaris server or use your DHCP server to assign the names so it can find them.

---

