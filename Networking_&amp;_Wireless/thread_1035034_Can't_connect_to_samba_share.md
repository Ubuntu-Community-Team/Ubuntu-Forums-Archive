---
title: "Can't connect to samba share"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by whollycow on 2009-01-09
I am trying to connect to a samba share on a remote server with no luck.  I am connected via VPN but entering the server and share information produces a "folder contents could not be displayed: connection timed out" error.  

Running smbclient -d 3 //server/share produces the following:

```
lp_load_ex: refreshing parameters
Initialising global parameters
params.c:pm_process() - Processing configuration file "/etc/samba/smb.conf"
Processing section "[global]"
added interface eth0 ip=fe80::230:1bff:fe46:94a9%eth0 bcast=fe80::ffff:ffff:ffff:ffff%eth0 netmask=ffff:ffff:ffff:ffff::
added interface eth0 ip=146.151.107.147 bcast=146.151.111.255 netmask=255.255.248.0
Client started (version 3.2.3).
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: Permission denied
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/gencache.tdb: No such file or directory
resolve_lmhosts: Attempting lmhosts lookup for name name@server<0x20>
resolve_wins: Attempting wins lookup for name name@server<0x20>
resolve_wins: WINS server resolution selected and no WINS servers listed.
resolve_hosts: Attempting host lookup for name name@server<0x20>
resolve_hosts: getaddrinfo failed for name name@server [No address associated with hostname]
name_resolve_bcast: Attempting broadcast lookup for name name@server<0x20>
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
Connection to name@server failed (Error NT_STATUS_BAD_NETWORK_NAME)

```

I'm not sure what to make of this output but I can ping the server just fine.

The exact same setup runs without problems on my Hardy box but I'm having no luck in Ibex.  What can I do?

---

### Post by whollycow on 2009-01-09
For reference, I have also tried connecting with the IP address, rather than the server name.  Still no luck.

---

### Post by superprash2003 on 2009-01-09
are you able to browse the shares?? like under nautilus .. under location type smb://x.x.x.x where x.x.x.x is ip of server

---

### Post by whollycow on 2009-01-10
Trying to connect through Nautilus produces the "folder contents could not be displayed" error.

---

### Post by whollycow on 2009-01-10
Bump

---

### Post by whollycow on 2009-01-14
Bump

I know there's somebody out there with some samba skills...

---

### Post by capscrew on 2009-01-14
```
tdb(unnamed): tdb_open_ex: could not open file /var/run/samba/unexpected.tdb: No such file or directory
```

This indicates that Samba is not installed correctly or configured appropriately.

this is the contents of my /var/run/samba ```

ls -l /var/run/samba
total 116K
-rw-r--r-- 1 root root  40K 2009-01-14 18:05 brlock.tdb
-rw-r--r-- 1 root root  12K 2009-01-14 18:05 connections.tdb
-rw-r--r-- 1 root root  696 2009-01-14 18:05 gencache.tdb
-rw-r--r-- 1 root root  40K 2009-01-14 18:05 locking.tdb
-rw------- 1 root root  696 2009-01-14 18:05 messages.tdb
-rw-r--r-- 1 root root    5 2009-01-14 18:05 nmbd.pid
-rw-r--r-- 1 root root  696 2009-01-14 18:05 sessionid.tdb
-rw-r--r-- 1 root root    5 2009-01-14 18:05 smbd.pid
-rw-r--r-- 1 root root 4.0K 2009-01-14 18:14 unexpected.tdb

```

Note that the time of creation is now.  These are current parameters created at boot time.  They appear to be world readable too. 

Post your ls -l view of /var/run/samba

---

### Post by whollycow on 2009-01-16
Here is the ls -l of /var/run/samba:

```
user@host:~$ ls -l /var/run/samba
total 104
-rw-r--r-- 1 root root          90112 2009-01-16 13:22 connections.tdb
-rw------- 1 root root            696 2009-01-16 13:22 messages.tdb
-rw-r--r-- 1 root root              5 2009-01-16 13:22 nmbd.pid
drwxr-x--- 2 root winbindd_priv    40 2009-01-16 13:22 winbindd_privileged

```

I'm running an unmodified samba so I can't figure out why mine would be missing some of the files that I apparently don't have.

Edit: FYI there's nothing in the winbindd_privileged directory

---

### Post by capscrew on 2009-01-16
Post the output of:```
ps -ef|grep mbd
```

I don't see the smbd.pid file.  To me that means samba is not running.

Just a thought; we are looking at the server hosts files, correct?

Edit: It we are talking about a client then we need to see your smb.conf file from the server.  In addition we need to check the addressing scheme.  I did notice that it can't find the address requested.```
resolve_hosts: getaddrinfo failed for name name@server [No address associated with hostname]
```

---

### Post by whollycow on 2009-01-17
> **capscrew said:**
> Edit: It we are talking about a client then we need to see your smb.conf file from the server.  In addition we need to check the addressing scheme.  I did notice that it can't find the address requested.```
resolve_hosts: getaddrinfo failed for name name@server [No address associated with hostname]
```

Yes, this is a client.  I don't have access to the server's smb.conf (by the way, I replaced the name and server for privacy, but I can ping the server just fine).

The part that is most frustrating is that I had no problems connecting before my clean install of Ibex.  Everything worked in Hardy without any configuration and now it magically doesn't.

I have looked through a number of related bugs and it looks like samba (and specifically cifs) in Ibex was a royal disaster.  Unfortunately, the fixes that I can find in bug reports haven't worked and I'm not savvy enough to find the root of my problem by myself.

---

### Post by capscrew on 2009-01-17
Whollycow,

Your not going to like this but here goes anyway.  I suggest you go back to Hardy (8.04).  There are a lot of things that are not stabilized with Intrepid (8.10).  The Gnome libs for Nautilus have changed and it is causing pain for many users.  I have a Hardy Samba server and a Gutsy (7.10) client.  Until things stabilize I won't upgrade.

---

### Post by whollycow on 2009-01-17
I was afraid of that.  Thanks for your help.  I knew there had been some major problems but I was hoping there was a way to hack my way out of it.

Luckily, I have my trusty old laptop with Hardy still installed so I can do what I need from there.  Here's to hoping things are fixed in Jaunty...

---

### Post by whollycow on 2009-02-17
It appears that this issue has been fixed with recent updates (2/16/09) to gvfs in Ibex.

---

