---
title: "Can't mount windows share from local computer"
date: 2013-02-26
forum: Networking &amp; Wireless
---

### Post by 3hack on 2013-02-26
trying to mount a windows share on local windows box, to ubuntu running on macbook inside paralells

I tried

```

 /$ smbclient \\\\192.168.1.122\\Users -U gsl
Enter gsl's password: *********

session request to 192.168.1.122 failed (Called name not present)
session setup failed: NT_STATUS_LOGON_FAILURE
```

and tried
 
```

 /$ sudo mount -t cifs //192.168.1.122/Users /mnt/win7 -o username=gsl

mount: block device //192.168.1.122/Users is write-protected, mounting read-only

mount: cannot mount block device //192.168.1.122/Users read-only
```


and tried

```

 /$ sudo mount -t smbfs //192.168.1.122/Users /mnt/win7 -o username=gsl
mount: unknown filesystem type 'smbfs'
```


NOTE: i have created /mnt/win7

---

### Post by prodigy_ on 2013-02-26
[http://www.groupes.polymtl.ca/gchit/?page_id=238](http://www.groupes.polymtl.ca/gchit/?page_id=238)

---

