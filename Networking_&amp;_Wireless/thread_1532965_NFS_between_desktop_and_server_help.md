---
title: "NFS between desktop and server help"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by UntoOthers on 2010-07-17
[SIZE=3]What I am trying to achieve is a similar system to how windows networks.

I have a folder on my server (/var/www) and I would like to share it via NFS so that when the server is on a folder appears in the network folder of my desktop and I am able to add, edit and delete folders and files as my non-root user (ryan).

So far I have managed to install the NFS server and client and configured /etc/exports as so

```
/var/www/ *(rw,sync,no_root_squash)
```I have then been able to mount the folder to my client using:

/etc/auto.master

[/SIZE]```
[SIZE=3]/home/server    /etc/auto.server --ghost --timeout=60[/SIZE]
```[SIZE=3]

/etc/auto.server

```
www 192.168.2.80:/var/www
```[/SIZE]

[SIZE=3]This isn't what I want and I was still unable to add, edit or delete folders and files. [/SIZE]
[SIZE=3]
[/SIZE][SIZE=3]Any help would be greatly appreciated.

[/SIZE]

---

### Post by UntoOthers on 2010-07-18
Anyone?

---

