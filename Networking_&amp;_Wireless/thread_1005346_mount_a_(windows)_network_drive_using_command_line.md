---
title: "mount a (windows) network drive using command line"
date: 2008-12-08
forum: Networking &amp; Wireless
---

### Post by idokus on 2008-12-08
I have a problem mounting a network drive, I need to do this in commandline, since I need it to be a script multiple users can use.

Manually I can mount it using the "connect to a windows network" tool in the places menu. So the server, share and credentials are valid.

```
root# mount -t cifs //<server>/Users$/<userdir> /mnt/local_mount/ -o credentials=/mnt/login
```

returns:

```
mount error 20 = Not a directory
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
``` 

I know the server-share and /mnt/local_mount both exists.

I hope you guys can help me out.

---

### Post by prshah on 2008-12-08
> **idokus said:**
> 
```
mount error 20 = Not a directory

``` 
I know the server-share and /mnt/local_mount both exists.


If local_mount a file, by any chance, instead of a directory?  ```
ls -l /mnt
```

---

### Post by idokus on 2008-12-09
it's a directory.

---

