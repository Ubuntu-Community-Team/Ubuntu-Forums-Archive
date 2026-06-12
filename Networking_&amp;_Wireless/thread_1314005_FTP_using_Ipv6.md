---
title: "FTP using Ipv6"
date: 2009-11-04
forum: Networking &amp; Wireless
---

### Post by MelanieS on 2009-11-04
Hello everybody!

I'm trying to use ftp with ipv6. I installed proftpd, but what command do I have to use in order to connect a client to the ftp server over ipv6?

Thanks in advance

---

### Post by sanderj on 2009-11-04
On the machine on which the FTP server is installed, have you tried 'ftp ::1'?

---

### Post by puppywhacker on 2009-11-04
I don't think the command line ftp client supports IPv6. Since ftp is normally uses plain text passwords over the wire it might be better to use sftp instead. The command would then be
```
sftp ::1
or
sftp [::1]

```

---

### Post by sanderj on 2009-11-04
> **puppywhacker said:**
> I don't think the command line ftp client supports IPv6. Since ftp is normally uses plain text passwords over the wire it might be better to use sftp instead. The command would then be
```
sftp ::1
or
sftp [::1]

```

I tried, but sftp does not work on the IPv6 address of ftp.surfnet.nl. Probable cause: sftp is ... secure-ftp. ;-)

How about lftp: plain ftp, over IPv6. Proof:

```

ubuntu@ubuntu:~$ lftp 2001:610:1:80aa:192:87:102:42
lftp 2001:610:1:80aa:192:87:102:42:~> dir
lrwxrwxrwx    1 0        509             1 Nov 08  2007 ftp -> .
lrwxrwxrwx    1 0        0               3 Oct 12  2007 mirror -> pub
lrwxrwxrwx    1 0        0              26 Sep 18  2008 pub -> vol/1/.CLUSTER/var_ftp/pub
lrwxrwxrwx    1 0        0              27 Oct 16  2007 site -> vol/1/.CLUSTER/var_ftp/site
drwxr-xr-x    7 0        0            4096 Jul 02  2008 vol
lftp 2001:610:1:80aa:192:87:102:42:/> exit
ubuntu@ubuntu:~$
```

So the OP should use 'lftp ::1' to test his/her own ftp server.

---

### Post by sanderj on 2009-11-04
And of course Firefox does FTP over IPv6: click this URL:


[ftp://[::1]/](ftp://[::1]/)

And if you've got IPv6 connectivty (easy way: "sudo apt-get install miredo"), you can click this:

[ftp://[2001:610:1:80aa:192:87:102:43]/](ftp://[2001:610:1:80aa:192:87:102:43]/)

---

