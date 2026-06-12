---
title: "network problems 9.04"
date: 2009-12-16
forum: Networking &amp; Wireless
---

### Post by mikest on 2009-12-16
I have a dual boot system with Ubuntu 9.04 and Ubuntu 9.10 installed
on separate partitions on the same drive.

The networking to the outside world has stopped working on the 9.04

Internally, on my own LAN things are fine.  I can ping, ftp, etc. to my other
computers and it works.

But, trying to use Firefox or Thunderbird does not work.

I'm about ready to start over and re-install the systems but I'd really like to
know what went wrong.

Any help appreciated.

Mike S.

---

### Post by fibercode on 2009-12-16
If you can get to your LAN without a problem then it seems that the issue could be your DNS settings.

Can you post the results of this command:

cat /etc/resolv.conf

---

### Post by Iowan on 2009-12-16
As a crosscheck, you might also try pinging internet site by IP address - try:```
ping -c3 74.125.95.103
```

---

### Post by dimamali on 2009-12-16
Hello,
mikest the fact that your LAN is working means that most probably there is no problem with your installation. So we will fix it!
first of all try to ping the outside world.
```
ping www.ubuntu.com
```If that times out it usually means that your router is blocking you. 
That might be a false router configuration (which has nothing to do with your OS) or an ISP problem (like you didn't pay the bill for example :-) ).
I know i migt sound funny but have you done all the necessary troubleshooting? Like checking cables and internet connection leds on your router? Are you sure your router is connected to the internet?

---

