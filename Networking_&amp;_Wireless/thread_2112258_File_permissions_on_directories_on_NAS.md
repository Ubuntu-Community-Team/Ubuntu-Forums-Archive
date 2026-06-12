---
title: "File permissions on directories on NAS"
date: 2013-02-04
forum: Networking &amp; Wireless
---

### Post by Carl H on 2013-02-04
I would appreciate some advice regarding the use of my NAS device. 

I have an Xubuntu PC and a MacBook laptop. The issue that I am having is that if I create a directory on the NAS from one machine, it appears as read-only on the other. 

A bit of sudo chmod is all that's required, but what do I need to configure to not need this?

---

### Post by LewisTM on 2013-02-04
I assume your NAS exports NFS shares. NFS, like all UNIX filesystems, stores ownerships as numeric IDs, irrespective of username. The primary UID in Ubuntu is 1000 (you can verify your UID with the command 'id'). In Macs, it's 500.

So the Mac box creates directories owned by 500 and the Ubuntu machine creates directories owned by 1000. Each are read-only for the other. There are many ways you could reconcile that: changing UIDs to match, adding both users to a group with rw access, or playing with Access Control Lists. It all depends on the degree of control you have over your NAS. So the question is: what are you running exactly?

Cheers!

---

### Post by Carl H on 2013-02-04
> **LewisTM said:**
> So the question is: what are you running exactly?

Xubuntu 12.10
MacOSX 10.8
The NAS is a QNAP TS210 with the latest firmware.

Thanks.

---

### Post by LewisTM on 2013-02-04
> **Carl H said:**
> Xubuntu 12.10
MacOSX 10.8
The NAS is a QNAP TS210 with the latest firmware.

Thanks.
I'll need more information that that. Are you accessing the shares through NFS? Are the IDs like I described? Can you use sudo to change file ownerships and permissions? Are you comfortable creating and editing groups? I can't propose any detailed solution without a better sense of the situation.

---

### Post by Carl H on 2013-02-06
**Are you accessing the shares through NFS? **
Yes, on both machines.

**Are the IDs like I described? **
500 and 1000 - yes.

**Can you use sudo to change file ownerships and permissions?**
Yes. 

**Are you comfortable creating and editing groups?**
I think so, I've done it before and I've just read up about it. 

**I can't propose any detailed solution without a better sense of the situation.**
Thanks for your assistance.

---

### Post by LewisTM on 2013-02-07
Thank you for the answers and sorry for the delay.

In brief, you should create a usergroup for your shares to which both Mac and Ubuntu users belong.

You can create a group on both machines using GUI or commandline tools. Graphically, go to Settings Manager -> Users and Groups -> Manage Groups -> Add

Create a group called nas with ID 1010 and add yourself to it.
On the Mac, do the same (I'm not sure how but it should be straightforward). It is critical that the group ID be the same.

In the Xfce terminal, navigate to your nas share and run these commands
```
sudo chgrp -R nas ./
sudo chmod -R g+w ./
sudo find ./ -type d -exec chmod g+s {} \;
```
This does the following:
1) Changes the group of all files and directories in the share to 'nas'.
2) Allows all files to be written by members of the nas group.
3) Sets the setgid bit on directories so that any new item gets owned by the nas group by default.

That's it. Have fun!

---

### Post by Carl H on 2013-02-12
Thank you. :)

---

