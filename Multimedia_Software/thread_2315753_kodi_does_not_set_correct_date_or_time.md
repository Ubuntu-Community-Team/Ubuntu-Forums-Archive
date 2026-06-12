---
title: "kodi does not set correct date or time"
date: 2016-03-02
forum: Multimedia Software
---

### Post by ethanay on 2016-03-02
Problem:  Kodi does not set the correct date and time, shows something like the year 1970 or 1969, even when you set the correct NTP servers.  Raspberry Pi does not have a hardware clock, so depends entirely on NTP to have access to correct date and time, which may be necessary for some other functions to run effectively.  Especially if you are modifying rather than merely storing and accessing files via Kodi or the underlying operating system.  It did not have any NTP servers set, so I set them, but the problem persisted.

For some reason, ntpd commands such as 
```
ntpd -q -p 0.pool.ntp.org
``` were not working, returning "bad address."   Then I tried to ping out, and found that no DNS was occurring.  The solution was either to find the IP address for the NTP servers or correct the DNS problem.  I looked at my network settings and found the issue:  DNS server was set to an incorrect IP address for some reason.  Changing it to a correct address (in my case, my router at 192.168.0.1) resolved the issue.

This problem occurs on OpenELEC installed on a RaspberryPi -- it might occur in other contexts, too.

---

