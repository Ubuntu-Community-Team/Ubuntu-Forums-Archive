---
title: "UFW failing to log all connection attempts"
date: 2011-02-17
forum: Networking &amp; Wireless
---

### Post by jobo3208 on 2011-02-17
Hi,

I am trying to write a little [[COLOR="Blue"]port knocking[/COLOR]]("http://en.wikipedia.org/wiki/Port_knocking") daemon that needs to see every failed connection attempt on every port on the system. The primary way to do this (as the Wikipedia page points out) is to monitor the firewall log file.

I am using UFW and reading its output in /var/log/kern.log. Typically, when UFW blocks something, it prints a little line like this:

> Feb 17 10:42:42 serin kernel: [323588.279588] [UFW BLOCK INPUT]: IN=eth0 OUT= MAC=00:0b:e6:00:85:96:00:09:5b:9f:41:a4:08:00 SRC=192.168.0.4 DST=192.168.0.8 LEN=60 TOS=0x00 PREC=0x20 TTL=49 ID=46945 PROTO=TCP SPT=56849 DPT=1723 WINDOW=5840 RES=0x00 SYN URGP=0 

But it seems that whenever UFW experiences a significant "load" (my client sends eight packets over the span of about 25 seconds, not too significant if you ask me), it just kind of "gives up" after 10 or so attempts. Log messages stop appearing in kern.log.

I know the packets are coming; wireshark confirms this.

It seems to me that a buffer of some sort is filling up, because if I give the system a breather and try sending my sequence again in, say, three minutes, it prints log messages for 10-12 straight attempts before giving up again.

I've tried sending packets at longer intervals and reading from other logs like /var/log/messages, but none of this has helped.

Does anyone have any idea why UFW would fail to log all blocked connection attempts?

Thanks in advance.

Joe

---

### Post by jobo3208 on 2011-02-18
Figured it out, in case anyone's interested.

/etc/ufw/after.rules has the line:

```
-A ufw-after-input -m limit --limit 3/min --limit-burst 10 -j LOG --log-prefix "[UFW BLOCK INPUT]: "
```

All I had to do was adjust the iptables log limits. Didn't know such a thing existed. I guess it's a pretty good idea to prevent flooding.

---

