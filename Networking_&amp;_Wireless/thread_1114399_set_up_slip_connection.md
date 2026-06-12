---
title: "set up slip connection"
date: 2009-04-02
forum: Networking &amp; Wireless
---

### Post by DeepSeaNautilus on 2009-04-02
Hello, I am using ubuntu 8.04 Hardy Heron. I am using slattach to set up a slip connection but it is not working. 
First I loaded slip module with
```
modprobe slip
```

the output of dmesg | grep -i slip is:
```
[ 1216.020817] SLIP: version 0.8.4-NET3.019-NEWTTY (dynamic channels, max=256) (6 bit encapsulation enabled).
[ 1216.020830] CSLIP: code copyright 1989 Regents of the University of California.
[ 1216.020834] SLIP linefill/keepalive option.
```


Then I configured the ttyS0 terminal with slattach:
```
slattach -p slip -s 19200 /dev/ttyS0 &
```

The problem is that sl0 interface never gets created. When I type ifconfig, only eth0 and lo interfaces are displayed. How can I fix this?

Does the serial line need to be plugged before using slattach?
Any help will be really apreciated, thanks in advance.

---

### Post by TSorcerer on 2011-09-30
Just in case you happen to still have this problem or someone finds this thread in search for a solution to a similar problem: [TCP/IP over null-modem](http://www.ott.net/knowledge/tcpip-nullmodem/)

Regards,
Daniel

---

### Post by lilorox on 2011-10-12
Yep, I tried SLIP too.
Seems more appropriate but I cannot make it work.

On the windows side (it's the client), it does not connect.

I followed the link you gave me for the linux part and for the windows part, I read that: [http://www.sics.se/~bg/telos/slipintro.pdf](http://www.sics.se/~bg/telos/slipintro.pdf)

---

### Post by lilorox on 2011-10-12
OOOoops sory, I thought I was responding to my post: [http://ubuntuforums.org/showthread.php?p=11333277](http://ubuntuforums.org/showthread.php?p=11333277) :oops::oops::oops:

---

