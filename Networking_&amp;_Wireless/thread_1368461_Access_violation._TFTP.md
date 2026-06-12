---
title: "Access violation. TFTP"
date: 2009-12-30
forum: Networking &amp; Wireless
---

### Post by kulikovskiy_d on 2009-12-30
Hi!

Have problem with tftp server 

```
 tftpd 0.17-17ubuntu1 
```I'm success download from tftp, but when upload pop error message "Access violation". Permissions set correctly to root directory (777).

from inetd.conf
```
tftp            dgram   udp     wait    nobody  /usr/sbin/tcpd  /usr/sbin/in.tftpd /tftp


```When I try to upload file debug messages says:

```
inetd -d
ADD: tftp proto=udp, wait.max=1.256 user:group=nobody:(default) builtin=0 server=/usr/sbin/tcpd
someone wants tftp
2604 execv /usr/sbin/tcpd
reaping asked for
2604 reaped, status 0
restored tftp, fd 4

```nobody user can write to directory:

```
$ cd /tftp
$ touch test
$ rm test
```Please help, tftp very critical service for me ((

---

