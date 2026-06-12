---
title: "Samba doesn't want to mount..."
date: 2009-10-24
forum: Networking &amp; Wireless
---

### Post by Crafty Kisses on 2009-10-24
Hey guys Montana here, and I'm just having a bit of trouble mounting Samba, it worked this morning, but then just decided to stop working, pretty weird. So to mount Samba I run:
```
mount -t cifs (my directory)
```
Then I receive the following error when I have attempted to mount Samba:
```
mount error: could not find target server.
```
Here are the only interesting lines in the **/var/log/samba** file:
```
/var/run/smbd.pid exists and process id 873 is running.
lib/util_sock.c:write_socket_data(413)
```
On some side notes here, my kernel routing table is fine, I've also tried dropping port 445 which was suggested by some folks, so I ran:
```
iptables -I INPUT 1 -p tcp --dport 445 -j DROP
```
Same results though, I still cannot mount Samba. I've tried numerous things so far and nothing has worked, I'm thinking it could be a possible update I took.

---

### Post by uncle-c on 2009-10-24
Did you state a "mount point " ? For example 

```

$ mount -t cifs /server-address/directory /mnt/share

```

Where **/mnt/share** is a directory on the *local machine* onto which the share is mounted.

Ports that need to be open for Samba to work properly are :
[B]
UDP 137
UDP 138
TCP 139
TCP 445[/B]

---

### Post by Iowan on 2009-10-24
I presume you've seen **dmizer**'s [How-To]("http://ubuntuforums.org/showthread.php?t=288534").

---

