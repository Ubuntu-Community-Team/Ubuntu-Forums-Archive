---
title: "vnstat won't play with new usb dongle"
date: 2013-04-05
forum: Networking &amp; Wireless
---

### Post by t0p on 2013-04-05
I use vnstat to keep track of my data transfer usage.  I recently started to use a usb 3G dongle (which ubuntu likes to call "eth1"), and vnstat refuses to play with it.

```

t0p@mars:~$ vnstat -d -i eth1
Error: Unable to read database "/var/lib/vnstat/eth1".

```

I thought maybe the /var/lib/vnstat/eth1 directory is missing because I started using the dongle *after* installing vnstat.  So I went through *this* palaver:

```

t0p@mars:~$ sudo mkdir /var/lib/vnstat/eth1
t0p@mars:~$ vnstat -d -i eth1
Error: Unable to open backup database "/var/lib/vnstat/.eth1".
t0p@mars:~$ sudo mkdir /var/lib/vnstat/.eth1
t0p@mars:~$ vnstat -d -i eth1
Error: Database load failed even when using backup. Aborting.

```

Anyone know where I'm going wrong? Cheers.

---

