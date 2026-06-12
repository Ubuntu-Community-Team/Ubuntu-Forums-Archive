---
title: "VPN connection failed"
date: 2010-06-22
forum: Networking &amp; Wireless
---

### Post by huysmki on 2010-06-22
Hi all,

Since yesterday I have some troubles with setting up a VPN connection to my workplace. When I try to open the VPN connection it fails. In my /var/log/messages file I found this :
```

Jun 22 17:10:23 li-huysmki pppd[26032]: pppd 2.4.5 started by huysmki, uid 0
Jun 22 17:10:23 li-huysmki pppd[26032]: Using interface ppp0
Jun 22 17:10:23 li-huysmki pppd[26032]: Connect: ppp0 <--> /dev/pts/2
Jun 22 17:11:00 li-huysmki pppd[26032]: LCP: timeout sending Config-Requests
Jun 22 17:11:00 li-huysmki pppd[26032]: Connection terminated.
Jun 22 17:11:00 li-huysmki pppd[26032]: Modem hangup
Jun 22 17:11:00 li-huysmki pppd[26032]: Exit.
Jun 22 17:11:26 li-huysmki pppd[26489]: pppd 2.4.5 started by huysmki, uid 0
Jun 22 17:11:26 li-huysmki pppd[26489]: Using interface ppp0
Jun 22 17:11:26 li-huysmki pppd[26489]: Connect: ppp0 <--> /dev/pts/2
Jun 22 17:12:00 li-huysmki pppd[26489]: LCP: timeout sending Config-Requests
Jun 22 17:12:00 li-huysmki pppd[26489]: Connection terminated.
Jun 22 17:12:00 li-huysmki pppd[26489]: Modem hangup
Jun 22 17:12:00 li-huysmki pppd[26489]: Exit.

```

After some trial and error, I found that when I start the following manually
```
sudo /usr/sbin/pptp vpn.nameofmycompany.com --nolaunchppp

```

the VPN connection succeeds. Anyone an idea?

Thanks in advance

---

