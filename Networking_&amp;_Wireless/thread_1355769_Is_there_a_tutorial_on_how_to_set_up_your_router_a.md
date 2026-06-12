---
title: "Is there a tutorial on how to set up your router and install for torrents?"
date: 2009-12-15
forum: Networking &amp; Wireless
---

### Post by mdmarmer on 2009-12-15
I'm working on a homegrown distro and I want to upload torrents to linuxtracker.  I think I understand how to do that but I could use help on setting my install for a static ip address (I have AT&T DSL), setting up my Linksys router to open the correct ports for UDP and TCP, and setting up my firewall (I use guarddog).  I'll probably use ktorrent for the upload.  Thanks in advance.

Mike

---

### Post by mdmarmer on 2009-12-15
OK -- I've done some searching and I found some tips

I'll get this figured out sooner or later.

[http://ubuntuforums.org/showthread.php?t=1259923](http://ubuntuforums.org/showthread.php?t=1259923)
[http://portforward.com](http://portforward.com)
[http://www.pcflank.com/scanner1.htm](http://www.pcflank.com/scanner1.htm)
To simply clear the firewall rules:
iptables -F
[http://trac.transmissionbt.com/wiki](http://trac.transmissionbt.com/wiki)
[http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html](http://www.cyberciti.biz/tips/linux-iptables-open-bittorrent-tcp-ports-6881-to-6889.html)

Mike

---

### Post by doas777 on 2009-12-15
portforward is your best resource on the router end.

other than that, you just need to install a firewall front-end like gufw, and allow the port you desire to receive incoming connections on.

I would also suggest looking into a blocklist app like iplist or moblock, and encrypting your torrent traffic. those of course are optional.

---

