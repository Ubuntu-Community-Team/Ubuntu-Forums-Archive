---
title: "Basically hosed up my samba, how to restore"
date: 2009-09-15
forum: Networking &amp; Wireless
---

### Post by legalguy on 2009-09-15
Had some shared folders that were kind of working, then I starting mess around, installingm GADMIN-samba, pyNeighborhood, trying to set up servers etc.  Basically it's all hosed and can't get it working now.

Can anyone point to a guide to how to restore default settings, then a step by step guide on how to set it up?

I have 4 computers, all linux, on the same 192.168.x.x network off the same router.  One is wired, three are wireless.

I'd like the file transfer to go through the router, not the internet.  Limited upstream bandwidth on the dsl.

I'd like either a single group folder that is the same on all the machines, or else a common folder on one of the machines.

I'd like it not have to worry about if one of the client machines is on or off, it will sync when it connects, or in the middle of the night, whatever.

Some of the machines have multiple logins, want all users to be able to see the shared files.  With read/write (that doesn't need to be reset with every reboot)

Any ideas?  Maybe samba isn't right for this task?  I'm happy to RTFM but I want to be sure it's the right FM.

---

### Post by swerdna on 2009-09-15
"all Linux" -- you could use NFS

If you want to use Samba for a SOHO workgroup situation, read here:
[The Samba LAN Primer for Ubuntu: HowTo Set up an Ubuntu-Windows Home & Office LAN/Network]("http://ubuntu.swerdna.org/ubulanprimer.html")

You'd like: "a common folder on one of the machines"
Set up a samba server. Suitable shares are detailed here:
[Samba Server and Ubuntu / Kubuntu: HowTo Configure a Professional File Server on a SOHO LAN]("http://ubuntu.swerdna.org/ubusambaserver.html#shares")

---

