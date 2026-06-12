---
title: "persistent internet issues"
date: 2010-12-13
forum: Networking &amp; Wireless
---

### Post by JakeFrederix on 2010-12-13
I did a clean install of the latest version of Ubuntu.
For some reason, there are still internet-issues.

When I tried out the following command
```

telnet
open ftp.microsoft.com 21

```I got

```

telnet: Unable to connect to remote host: Connection timed out

```Also, during install of the new ubuntu, it was unable to reach the repos for downloading.

Odd thing is that I can go online, and that when I type 'ftp.microsoft.com' in my browser, it displays the file-hierarchy.

Can anyone give any insight as to what's happening?

Kind regards,
Jake

---

### Post by JakeFrederix on 2010-12-19
It's apparently an issue with my router.
It keeps feeding me my own IP as a nameserver, which messes up most programs.
I manually overwrite the /etc/resolv.conf file.

Problem is that I have to overwrite this file ever single time my computer makes connection with my router.
By some streak of luck though, I was switching ISP's anyway, so I'm getting a new router next month.

---

