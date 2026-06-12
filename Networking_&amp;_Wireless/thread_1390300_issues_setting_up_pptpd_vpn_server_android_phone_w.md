---
title: "issues setting up pptpd vpn server android phone won't connect"
date: 2010-01-25
forum: Networking &amp; Wireless
---

### Post by omega52390 on 2010-01-25
so iv'e been trying to set up a pptp server using pptpd on my desktop. what im trying to get it to do is have my nexus one connect to it so that i can pull files off and remote desktop. i know that i have gotten somewhere with this because i get a response in /var/log/messages saying ```
Jan 25 12:13:42 ************ pppd[24508]: Plugin /usr/lib/pptpd/pptpd-logwtmp.so loaded.
Jan 25 12:13:42 ************ pppd[24508]: pppd 2.4.5 started by root, uid 0
Jan 25 12:13:42 ************ pppd[24508]: Using interface ppp0
Jan 25 12:13:42 ************ pppd[24508]: Connect: ppp0 <--> /dev/pts/1
Jan 25 12:14:13 ************ pppd[24508]: Modem hangup
Jan 25 12:14:13 ************ pppd[24508]: Connection terminated.
Jan 25 12:14:13 ************ pppd[24508]: Exit.
```
so i know the connections are trying to happen but im guessing something is failing in the handshake becuase my phone will give my one of two errors saying either it failed to connect from an improper username or password, or it will tell me it might not be working because i am behind a firewall. does anyone have any ideas as to what is going wrong. apparently i can access it locally if im connected to the same router on wifi with both my laptop(another linuxbox haven't tested it over-ip yet) and my phone.

---

### Post by TyTiger on 2010-01-25
Yea join the club.. 

pptpd seems very lacking and even after googling all day there seems to be very little on actually getting it to work. 

pptp vpn worked fine between 2 windoez machines, just not with a linux server runnin pptpd seemingly.

---

### Post by kaziem on 2010-06-06
bump.. any new news on this ?

---

### Post by kaziem on 2010-06-06
This might be related.. Apparently vpn client in android 2.1 was compiled without mmpe encryption capabilities.. Anyone can shine some light into this issue?

[http://androidforums.com/htc-desire/70997-unable-connect-pptp-vpn-server-bug-found-android-2-1-a.html](http://androidforums.com/htc-desire/70997-unable-connect-pptp-vpn-server-bug-found-android-2-1-a.html)

---

