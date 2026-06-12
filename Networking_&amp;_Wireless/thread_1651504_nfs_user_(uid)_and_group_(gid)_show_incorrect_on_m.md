---
title: "nfs user (uid) and group (gid) show incorrect on mounted nfs filesystem"
date: 2010-12-23
forum: Networking &amp; Wireless
---

### Post by stigen on 2010-12-23
Hello,

Client: Ubuntu 10.10, 32-bit
Server: Ubuntu 10.10 64-bit

I am currently having an issue showing the file permissions on a mounted nfs volume. The gid and uid show bizar values on the client:

-rw-------  1 4294967294 4294967294       6615 2010-12-23 11:36 .bash_history
-rw-r--r--  1 4294967294 4294967294        220 2010-02-22 22:50 .bash_logout
-rw-r--r--  1 4294967294 4294967294       3180 2010-02-22 22:50 .bashrc

Expected (where locutus is my user name, and the UID is 1000 on both server and client).

-rw-------  1 locutus locutus       6615 2010-12-23 11:36 .bash_history
-rw-r--r--  1 locutus locutus        220 2010-02-22 22:50 .bash_logout
-rw-r--r--  1 locutus locutus       3180 2010-02-22 22:50 .bashrc

The GID and UID are identical on the server as they are on the client (manual synchronization).
The GID and UID show correct when listing directly on the server.

My /etc/default/nfs-common contents on the server:

NEED_STATD=
STATDOPTS=
NEED_IDMAPD=yes
NEED_GSSD=no

my /etc/default/nfs-kernel-server 

RPCNFSDCOUNT=8
RPCNFSDPRIORITY=0
RPCMOUNTDOPTS=--manage-gids
NEED_SVCGSSD=no
RPCSVCGSSDOPTS=

my /etc/exports:

/home   *(rw,sync)

On the client side, I have these problems with an auto-mounter, as wel as with manual mounting.

Can someone help? Please let me know if you need additional information. (I am not an nfs expert).

Thank you,

Stijn

---

### Post by movieman on 2010-12-23
This page talks about setting NEED_IDMAPD as you have, but doesn't say whether it's on the server or client: maybe enabling it on the client will solve the problem? That uid is 'nfsnobody', which means something doesn't know what the correct ID is.

[https://help.ubuntu.com/community/NFSv4Howto](https://help.ubuntu.com/community/NFSv4Howto)

---

### Post by stigen on 2010-12-23
Thank you movieman.

Indeed, NEED_IDMAPD was not set in the file /etc/default/nfs-common on the client side.

Setting NEED_IDMAPD=yes on the client as well resolved the issue. Now client correctly shows user names and groups.

thanks!

Stijn

---

