---
title: "Troubleshoot Samba"
date: 2011-01-20
forum: Networking &amp; Wireless
---

### Post by David_UK on 2011-01-20
Hi

I have 3 pc's on home network.  All dual boot Windows and Ubuntu.  All have Samba installed, plus personal file sharing.

When all 3 are booted into linux, all 3 show the public folders on all 3 pc's, but only 2 can access the other pc's folders.

I can't find any difference between the systems to explain why one pc (10.04) cannot mount either of the other two public folders: 

*Unable to mount location.  DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus) *

even though their icons are shown in 'network'.

The public folder on the troublesome pc can be accessed from the other two (10.04 & 10.10).

Any suggestions gratefully received.  Thanks

---

### Post by Morbius1 on 2011-01-20
Kinda confused by your post. The title references Samba but then you say you're using "Personal File Sharing" - PFS.

PFS has nothing to do with Samba. PFS sets up a baby apache file server and uses avahi to broadcast the only folder it's capable of sharing and thats the Public folder in your home directory.

SO the first thing I would do is make sure all things avahi are running on both the server and the client:

Check to see if avahi is running:
```
sudo service avahi-daemon status
```If it's not running start it:
```
sudo service avahi-daemon start
```The other thing you need to check is that the avahi port is open on your systems. If I remember correctly it's port 5353/udp (zeroconfig). If you haven't done anything with the firewalls on either system it should be open though.

---

### Post by David_UK on 2011-01-21
Hello Morbius1, thanks for your reply.

> **Morbius1 said:**
> PFS has nothing to do with Samba.Ah, I didn't know that.  In that case I have Samba *and* PFS running on all 3 machines.  PFS is the problem with this one pc.  The avahi-daemon is up and running on all of the pc's.

I installed a GUI for the firewall on the problem pc, but as I had no idea how to configure it I uninstalled it. 

The output of ***iptables -L*** is:

```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Which I gather means that no rules are in place.  I did change the name of that computer a while ago by editing /etc/hosts, could that have caused the problem?  Is it possible to remove PFS, including all the config and reinstall?

Thanks

---

### Post by Morbius1 on 2011-01-21
You don't need to uninstall PFS just disable it. In a terminal run:
```
gnome-file-share-properties
```
And uncheck "Share public Files on Network"

As for the Samba part you might want to post the output of the following command and specify which hosts are giving you problems:
```
smbtree
```

---

### Post by David_UK on 2011-01-22
Morbius1
Thanks for your reply.  I can't reproduce the fault now so I'm confused but happy.  I'll start a new thread if I run into problems again.
Cheers.I

---

### Post by bradshaw_k1te on 2012-01-30
[FONT="Arial Black"][SIZE="4"]I fell in here and found my help. So I am also SOLVED.  smbtree is a powerful neat tool.  I found my problem as  I had had two different workgroups in my home.  I set everything to WORKGROUP and pc's netbooks, macs, and linux are all happily talking again. Thanks Ubuntu Forum.  Bradshaw, Shrewsbury, MA, Jan 30 2012:popcorn:[/SIZE][/FONT]

---

