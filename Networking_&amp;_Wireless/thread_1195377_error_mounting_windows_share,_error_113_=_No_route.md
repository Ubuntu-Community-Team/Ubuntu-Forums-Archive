---
title: "error mounting windows share, error 113 = No route to host"
date: 2009-06-23
forum: Networking &amp; Wireless
---

### Post by jeli2657 on 2009-06-23
I've followed the man page and online guides, I type:
```
 mount -t smbfs -o username=jesse,password=**** //192.168.1.108/D-drive /mnt/win
```

I get back:
```
mount error 113 = No route to host
Refer to the mount.cifs(8) manual page (e.g.man mount.cifs)
```

I can ping the IP fine.  I also tried:
```
smbclient -L server -U jesse
```
(server is the actual hostname, smbclient will resolve it, but mount and ping won't)
and I get back the following
```
Password: 
Domain=[SERVER] OS=[Windows Server (R) 2008 Standard 6001 Service Pack 1] Server=[Windows Server (R) 2008 Standard 6.0]

    Sharename       Type      Comment
    ---------       ----      -------
    ADMIN$          Disk      Remote Admin
    Brother HL-5140 Printer   Brother HL-5140
    C$              Disk      Default share
    D$              Disk      Default share
    D-drive         Disk      
    IPC$            IPC       Remote IPC
    print$          Disk      Printer Drivers
Domain=[SERVER] OS=[Windows Server (R) 2008 Standard 6001 Service Pack 1] Server=[Windows Server (R) 2008 Standard 6.0]

    Server               Comment
    ---------            -------

    Workgroup            Master
    ---------            -------

```

What am I doing wrong?

I've also configured the shared printer and can successfully print to it, so it seems weird that I can't open the file share...?

This is on a stock xubuntu 8.04

---

### Post by jeli2657 on 2009-06-23
I've also tried:
```
mount.smbfs  //192.168.1.108/D-drive /mnt/win -o username=jesse,password=****
```
But I get the same error message.

---

### Post by jeli2657 on 2009-06-23
Nevermind....
The I was putting in the wrong IP address...

---

