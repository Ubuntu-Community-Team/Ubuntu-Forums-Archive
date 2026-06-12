---
title: "SSH tunneling help?"
date: 2013-04-08
forum: Networking &amp; Wireless
---

### Post by roseysdaddy on 2013-04-08
Im trying to port forward 10000 for webmin/no-ip.org following the directions in this post:

[http://ubuntuforums.org/showthread.php?t=902762](http://ubuntuforums.org/showthread.php?t=902762)

i get to the point of the ssh command "ssh [email]user@myserver.no-ip.org[/email] -L 10000:localhost:10000" but i get the error:

bind: Address already in use
channel_setup_fwd_listener: cannot listen to port: 10000
Could not request local forwarding.

then it acts like it logs me back into ubuntu (shows the initial login info).

I think i have everything else setup correctly, if i could get this port forwarded correctly i should be in business.

---

### Post by wildmanne39 on 2013-04-08
Moved to networking and wireless.

---

### Post by bswilson on 2013-04-08
It seems you're trying to use the same source port and destination port (10000). Maybe you should try the command "[FONT=Courier New]ssh [email]user@myserver.no-ip.org[/email] -L 10000:localhost:22[/FONT]". This [article]("http://www.debianadmin.com/howto-use-ssh-local-and-remote-port-forwarding.html") has some more/different details and instructions that may help you.

---

