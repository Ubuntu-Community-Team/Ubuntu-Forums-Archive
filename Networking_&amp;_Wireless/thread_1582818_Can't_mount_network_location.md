---
title: "Can't mount network location"
date: 2010-09-27
forum: Networking &amp; Wireless
---

### Post by X3nopro on 2010-09-27
I added this line to the fstab file:

```
//SERVER/dfs/users/USER /media/USER cifs uid=1000,gid=1000,username=USER,password=PASSWORD 0 0
``` and when I try to run 

```
sudo mount -a
```I get the error:
> mount error(11): Resource temporarily unavailable
Refer to the mount.cifs(8) manual page (e.g. man mount.cifs) The line worked fine on Ubuntu 10.04 but is causing this error on 10.10

---

### Post by RikoW on 2010-09-30
Hi,

I have exactly the same problem. Worked fine in 10.04 now in 10.10 (optimistic/impatient :) update today)

Cheers,
         Riko

---

### Post by RikoW on 2010-10-01
try:

```
sudo apt-get install keyutils
```
 
works for me!

Source:

[HTML]https://bugs.launchpad.net/ubuntu/+source/samba/+bug/493565[/HTML]

it's an old thread but hey ... :)

Cheers,

             Riko

---

### Post by X3nopro on 2010-10-12
Thanks that worked.

---

