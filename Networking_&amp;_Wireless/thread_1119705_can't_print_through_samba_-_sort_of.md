---
title: "can't print through samba - sort of"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by cnkbrown on 2009-04-08
I can print test pages, but nothing else.

I don't print often, so I don't know when exactly this problem kicked up. 

here's my error log;

```
cbrown@cbrown-laptop:~$ sudo cat /var/log/cups/error_log
E [06/Apr/2009:09:50:25 -0400] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [07/Apr/2009:08:41:18 -0400] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [07/Apr/2009:08:56:45 -0400] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [07/Apr/2009:08:59:06 -0400] [CGI] Unable to scan "@LOCAL"!
E [07/Apr/2009:09:01:54 -0400] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [07/Apr/2009:09:04:04 -0400] [CGI] Unable to scan "@LOCAL"!
E [07/Apr/2009:10:01:19 -0400] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [07/Apr/2009:10:03:27 -0400] [CGI] Unable to scan "@LOCAL"!
E [07/Apr/2009:16:36:47 -0400] Print-Job: Unauthorized
E [07/Apr/2009:16:39:10 -0400] Print-Job: Unauthorized
E [08/Apr/2009:08:38:56 -0400] Unable to bind socket for address 127.0.0.1:631 - Address already in use.
E [08/Apr/2009:08:43:41 -0400] Print-Job: Unauthorized
E [08/Apr/2009:08:44:37 -0400] Print-Job: Unauthorized
E [08/Apr/2009:08:45:01 -0400] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [08/Apr/2009:08:45:06 -0400] [Job 752] Session setup failed: NT_STATUS_LOGON_FAILURE
E [08/Apr/2009:08:45:06 -0400] [Job 752] Session setup failed: NT_STATUS_NO_SUCH_FILE
E [08/Apr/2009:08:45:07 -0400] [Job 752] Session setup failed: NT_STATUS_LOGON_FAILURE
E [08/Apr/2009:08:45:07 -0400] [Job 752] Tree connect failed (NT_STATUS_ACCESS_DENIED)
E [08/Apr/2009:08:45:07 -0400] PID 7272 (/usr/lib/cups/backend/smb) stopped with status 2!
E [08/Apr/2009:08:45:20 -0400] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [08/Apr/2009:08:45:28 -0400] [cups-driverd] Unable to write "/var/cache/cups/ppds.dat" - Permission denied
E [08/Apr/2009:08:46:00 -0400] Print-Job: Unauthorized
E [08/Apr/2009:08:50:45 -0400] Print-Job: Unauthorized
E [08/Apr/2009:08:51:04 -0400] Print-Job: Unauthorized
```

---

### Post by superprash2003 on 2009-04-08
you may need to specify a username and password to connect.. do you do that?

---

### Post by cnkbrown on 2009-04-08
Yes, I do.  w/out that I can't get the test page to print.  Also, there is a verify button for checking them, and hitting that tells me the printer is accessible.

---

