---
title: "Port mapping question"
date: 2010-01-21
forum: Networking &amp; Wireless
---

### Post by kingbuzzo on 2010-01-21
Hi, so I used [this guide](http://www.ryochan7.com/blog/2009/06/23/pc-dc-server-guide-part-0-introduction/) to have my Dreamcast (yes I know) share an internet connection with my Ubuntu box.

Dreamcast's modem -> usb modem -> ubuntu box -> router -> internet

however I need the ubuntu box (192.168.0.2) to forward or map certain ports overto the Dreamcast (192.168.0.3).

There's a guide on doing this in winroute [here](http://dreamcast.onlineconsoles.com/phpBB2/guides_pcdcwin98.php#7d). But I'm wondering how I might do this in Ubuntu 9.04?

thanks,

King.

---

### Post by puppywhacker on 2010-01-21
```
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dport 1234 -j DNAT --to 192.168.0.3:1234
```

---

### Post by kingbuzzo on 2010-01-21
thanks! so I need ports 40975, 41231, 41487, 4174. Would I do a new iptables command for each one?

---

### Post by puppywhacker on 2010-01-21
nope, multiple entries will work, but you can keep it in one rule. notice that --dports is now has an "s" and the port after the destination address is removed. the ports are comma separated

```
iptables -t nat -A PREROUTING -i ppp0 -p tcp --dports 40975,41231,41487,4174 -j DNAT --to 192.168.0.3
```

---

### Post by kingbuzzo on 2010-01-23
I've received the following output

```
iptables v1.4.0: Unknown arg `--dports'
Try `iptables -h' or 'iptables --help' for more information
```

also, should I be using masquerading?

like in [ this guide?](http://linux.about.com/od/ubusrv_doc/a/ubusg18t03.htm)

---

