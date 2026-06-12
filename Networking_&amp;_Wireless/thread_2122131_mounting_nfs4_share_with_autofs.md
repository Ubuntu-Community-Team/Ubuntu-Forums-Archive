---
title: "mounting nfs4 share with autofs"
date: 2013-03-04
forum: Networking &amp; Wireless
---

### Post by benwayj on 2013-03-04
Its my understanding that when mounting a network share over a wifi connection fstab is not the way to mount the share so I'm trying to configure autofs to do it.

I can mount my share with the command:
```
sudo mount -t nfs4 -o rw,proto=tcp,port=2049 nfsservername:/ /mnt/nas
```

Although this appears to be read only.  I assume this is a separate problem with my server configuration.  Here is the /etc/exports from the server anyways:
```
/export		10.10.99.0/24(rw,fsid=0,insecure,no_subtree_check,async)
/export/user	10.10.99.0/24(rw,nohide,insecure,no_subtree_check,async)
```

my auto.master is just one line:
```
/mnt/nas	/etc/auto.nfs4	--timeout=90
```

my auto.nfs4 file is also one line:
```
-fstype=nfs4,rw,proto=tcp,port=2049 fileslut:/&
```

This does not successfully mount the share.  The mount point is empty although something is attempting to mount there as I can't say, mkdir a folder in the mountpoint as permissions are always denied.  More info:

```
:~$ sudo service autofs stop
autofs stop/waiting
user@client:~$ sudo automount -vf
Starting automounter version 5.0.6, master map /etc/auto.master
using kernel protocol version 5.02
lookup(dir): dir map /etc/auto.master.d missing or not readable
lookup(file): failed to read included master map dir:/etc/auto.master.d
mounted indirect on /mnt/nas with timeout 90, freq 23 seconds
user@client:~$ ls /mnt/nas
user@client:~$

```

This is a lot of moving parts I know and is all new to me but I'd appreciate any help the community could give.

---

### Post by benwayj on 2013-03-04
Bump.  80 views and no takers yet?

---

### Post by Toz on 2013-03-04
> /mnt/nas	/etc/auto.nfs4	--timeout=90
.....Try with the --ghost option, it will create the directory structure of the share so that you can at least see something. Like this:
```
/mnt/nas	/etc/auto.nfs4	--timeout=90 --ghost
```

> -fstype=nfs4,rw,proto=tcp,port=2049 fileslut:/&
.....Before using wildcards, try mapping directly to the export first to ensure it works.

> lookup(dir): dir map /etc/auto.master.d missing or not readable
lookup(file): failed to read included master map dir:/etc/auto.master.d
.....I think something might be wrong with your /etc/auto.master file. Can you post its full contents?

[Reference]("https://help.ubuntu.com/community/Autofs").

---

### Post by benwayj on 2013-03-05
Thank you so much for your reply.

I looked into my auto.master and it seems there was another line that I missed.
```
+dir:/etc/auto.master.d
```
It is now commented out.

Here is my revised auto.nfs4 file as per your recommendations
```
files -fstype=nfs4,rw,proto=tcp,port=2049 fileslut:/export
```

I enabled ghosting but that didn't seem to make a difference.
```
user@client:~$ sudo service autofs stop
autofs stop/waiting
user@client:~$ sudo automount -vf
Starting automounter version 5.0.6, master map /etc/auto.master
using kernel protocol version 5.02
mounted indirect on /mnt/nas with timeout 90, freq 23 seconds
ghosting enabled

^Zstatemachine:1363: got unexpected signal 20!

[1]+  Stopped                 sudo automount -vf
user@client:~$ sudo service autofs start
autofs start/pre-start, process 2904
user@client:~$ ls /mnt/nas
user@client:~$ 

```

I'm afraid I'm still missing something.  I did get rw to work though when I manually mount it, I had to change the permissions of the export directory on the server.

---

### Post by Toz on 2013-03-05
Just set it up on my system (13.04 install) to test.

To get it to work, my /etc/auto.master looks like this:
```
/mnt /etc/auto.nfs  --timeout=60 --ghost
```
...and my /etc/auto.nfs looks like this:
```
data	        192.168.1.254:/data
```

This gives me /mnt/data that has my exported nfs share mounted there.

---

