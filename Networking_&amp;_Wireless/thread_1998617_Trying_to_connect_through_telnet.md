---
title: "Trying to connect through telnet"
date: 2012-06-07
forum: Networking &amp; Wireless
---

### Post by japhyr on 2012-06-07
Hello,

I am trying to get the following command to work:
```
telnet rendezvous.heroku.com 5000
```
The command works for me when I have my laptop hooked up to the network at my workplace.  But at home, I get
```
$ telnet rendezvous.heroku.com 5000
Trying 50.19.103.36...
telnet: Unable to connect to remote host: No route to host

```
I am connecting to the internet through a Zhone 1511 Modem,and the ISP is ACS Alaska.  I disabled the firewall in the modem.  I called the ISP this morning, and the technician said they do not block any ports, and it sounded like he verified this for my account. I can ping the rendezvous.heroku.com address without any problems.

Which of my router's settings should I adjust to be able to use port 5000?  I have poked around for a while, and googled, but can't get anything to work.

---

