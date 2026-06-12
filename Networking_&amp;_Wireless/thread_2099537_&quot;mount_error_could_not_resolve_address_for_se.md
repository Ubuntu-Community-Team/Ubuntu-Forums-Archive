---
title: "&quot;mount error: could not resolve address for server: Unknown error&quot; mounting"
date: 2012-12-29
forum: Networking &amp; Wireless
---

### Post by spookyjack123 on 2012-12-29
I'm attempting to mount a CIFS share at //server/media to the mountpoint /NAS however when I use this: 

```
mount -t cifs -o ****,**** //server/media/ /NAS
```

I seem to get this back:

```
mount error: could not resolve address for server: Unknown error
```

Any ideas ? I'd really like to use my NAS :P :)

---

### Post by steeldriver on 2012-12-29
Can you actually ping the server by its unqualified hostname? 

```
ping server
```For me, I need to either use the numeric IP or (if avahi / zeroconf is running) *server.local*

```
$ sudo mount -t cifs //NAS-01/public /mnt/cifs/public
mount error: could not resolve address for NAS-01: Unknown error
$
$ sudo mount -t cifs //**NAS-01.local**/public /mnt/cifs/public
Password: 
$ ls /mnt/cifs/public/
Downloads  Program Files  Software 

```

---

### Post by spookyjack123 on 2012-12-29
> **steeldriver said:**
> Can you actually ping the server by its unqualified hostname? 

```
ping server
```For me, I need to either use the numeric IP or (if avahi / zeroconf is running) *server.local*

```
$ sudo mount -t cifs //NAS-01/public /mnt/cifs/public
mount error: could not resolve address for NAS-01: Unknown error
$
$ sudo mount -t cifs //**NAS-01.local**/public /mnt/cifs/public
Password: 
$ ls /mnt/cifs/public/
Downloads  Program Files  Software 

```

It will not ping it (Unknown host) however when I add .local to the end of server, it gives the same error, however it hangs for about 2 seconds instead of instantly outputting the mount error.

EDIT: Also If I try using the numeric IP, it gives me the following error:

```

mount error(22): Invalid argument
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs)

```

---

### Post by steeldriver on 2012-12-29
so try the IP

---

### Post by spookyjack123 on 2012-12-29
Sorry, I edited the reply at the exact same time you replied

---

### Post by spookyjack123 on 2012-12-30
Okay guys, I solved it, mount didn't want to play well with CIFS, so instead I got NFS running serverside, and mounted that instead with a different command. It works like a charm. Not sure if others are having the issue with CIFS mounting like this, and I don't really call this as solving it, but it works now.

---

### Post by steeldriver on 2012-12-30
maybe you don't have the cifs-utils package installed? I don't think it is by default

```
sudo apt-get install cifs-utils
```

iirc cifs-utils contains the mount.cifs stuff

---

### Post by spookyjack123 on 2012-12-30
> **steeldriver said:**
> maybe you don't have the cifs-utils package installed? I don't think it is by default

```
sudo apt-get install cifs-utils
```

iirc cifs-utils contains the mount.cifs stuff

I have it, still doesn't work on CIFS. NFS works

---

