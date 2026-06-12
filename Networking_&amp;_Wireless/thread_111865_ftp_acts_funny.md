---
title: "ftp acts funny"
date: 2006-01-03
forum: Networking &amp; Wireless
---

### Post by rajko on 2006-01-03
I tryed to use ftp to connect to linux host.
with ftp:
*I can connect, verification of user name and pass OK, but when dir or ls commands are used nothing happens.
*wget wont even login
*ncftp works fine for first file and then it reports some error
ncftpget -R stops after first file

I tryed to do the same thing from other linux machine(solaris) and it worked fine(ftp and wget).

Does any one else have simmilar problems?

here is my ftp -d qwe.hr output:
Connected to qwe.hr.
220 Leut ftp server
ftp: setsockopt: Bad file descriptor
Name (qwe.hr:rajko): ftp
---> USER ftp
331 Anonymous login ok, send your complete email address as your password.
Password:
---> PASS XXXX
230 Access granted for ftp.
---> SYST
215 UNIX Type: L8
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> dir
ftp: setsockopt (ignored): Permission denied
---> PORT 192,168,0,10,134,82
200 PORT command successful
---> LIST
*** at this point nothing happens ... for few minutes  and then ...
425 Unable to build data connection: Connection timed out

here is my wget -d output:
--11:05:27--  [ftp://qwe.hr/rajko/finished](ftp://qwe.hr/rajko/finished)
  (try: 9) => `qwe.hr/rajko/.listing'
Found qwe.hr in host_name_addresses_map (0x80909e0)
Connecting to qwe.hr|199.199.68.130|:21... connected.
Created socket 4.
Releasing 0x080909e0 (new refcount 1).
Logging in as anonymous ...
Error in server response, closing control connection.
Closed fd 4
Retrying.

As you can see I'm behind router, but even when I redirect all ports(0-65535) to this machine same thing happens.

Rajko.

---

