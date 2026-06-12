---
title: "WIFI does not connect after 10.4 Upgrade"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by dgr8im on 2010-09-10
I have a good connection with 9.04 but when I upgrade it to 10.4 the network keeps looking for wiFI. I have a Linksys USB adapter 2.4HZ.  Please help.

Thanks

---

### Post by shakibv on 2010-09-10
hi , plz give a bit more of information may one can help you

---

### Post by dgr8im on 2010-09-10
OK - First of I'm new to Ubuntu.  It was easy to download and install 9.04.  The wirless connection went without a flaw.  I saw that there is a newer version of Ubuntu (10.4) so I upgraded to a newer version only to find that my wifi does not get connected.  I read that this would be solved if I do a clean install of 10.4 but that failed too.  I have a Linksys USB 2.4 Ghz adapter.

Thanks

---

### Post by Megaptera on 2010-09-10
Hi,
I know this talks about Dell and Karmic but it's quick and safe to try while waiting for more expert help ...
[http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html](http://www.ubuntumini.com/2009/11/broadcom-wireless-driver-fix-in-karmic.html)

don't forget to reboot.

---

### Post by ch13fy on 2010-09-10
Have you tried wicd ?

---

### Post by dgr8im on 2010-09-14
I tried but again the same problem.  WIFI is not detected....

---

### Post by utilitytrack on 2010-09-14
Hello, please post here output of following commands:

```
$ uname -a
$ cat /proc/cmdline
$ lspci -nn
$ lsusb
$ ifconfig -a
$ cat /etc/network/interfaces
# lshw -C network
# iwconfig
```

Also write your PC/Laptop model.

---

### Post by dgr8im on 2010-10-09
Im still very new and do not know where to type this commands.  Sorry. Need help.

---

### Post by utilitytrack on 2010-10-28
**dgr8im**

Please read this: [https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")

---

