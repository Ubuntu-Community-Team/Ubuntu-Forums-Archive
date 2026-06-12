---
title: "Basic Connections"
date: 2009-05-09
forum: Networking &amp; Wireless
---

### Post by andrew.co.za on 2009-05-09
Hi,
How do i set up a simple lan connection, i really thought it would be as simple as plugging the cable in. Every time i try to connect by clicking on Auto eth1 it tries to connect for a few minutes then fails. The rest of the PC's on the network are windows PC's.

I'm using ubuntu 9.04, my HSDPA internet connection works without any problems.

---

### Post by kay-man on 2009-05-09
you'll need samba to connect to windows pc's.

Run this in a terminal (or use a package manager):

```
sudo apt-get install smbclient
```

Then you need to configure samba by editing /etc/samba/smb.conf.

There's plenty of documentation around to get you on your way. One important thing is to enter the name of your workgroup, or you still won't be able to access you win machines. All the way at the top of this file (in the [global] section) should be something like this:

```
# Change this to the workgroup/NT-domain name your Samba server will part of
workgroup = [your workgroup name here without the square braces]

```

---

### Post by superprash2003 on 2009-05-09
first you need to make sure that you are getting an ip address.. are all these machines connected to a router? post output of **ifconfig** from the terminal

---

### Post by Iowan on 2009-05-09
If machine has valid IP address, can it **ping** the Windows machines?  Most Ubuntu versions come with Samba client already installed, but you must insure it is in same workgroup as Windows machines.  There may be a GUI way to do it, but I usually just backup my **/etc/samba/smb.conf**, then use **nano** to make changes.

Maybe like this:> **jstevans said:**
> I used the "General Properties" tab in 8.10's "Admin > System > Shared Folders" to put my Xubuntu machine onto the same workgroup as my other machines.

---

### Post by andrew.co.za on 2009-07-13
Turns out the switch (router) was the problem, Ubuntu plug and play networking works fine :P

---

