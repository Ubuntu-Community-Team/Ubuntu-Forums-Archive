---
title: "Which process is using the network?"
date: 2006-01-29
forum: Networking &amp; Wireless
---

### Post by spiregrain on 2006-01-29
Using the System Monitor applet, I notice that *something* is using a lot of network capacity- but I'm not sure what.

Is there a tool like "ps"  (displaying cpu utilisation), but for network utilisation process-by-process?

---

### Post by cwaldbieser on 2006-01-29
[QUOTE=spiregrain]Using the System Monitor applet, I notice that *something* is using a lot of network capacity- but I'm not sure what.

Is there a tool like "ps"  (displaying cpu utilisation), but for network utilisation process-by-process?[/QUOTE]
Try (in the terminal)
```

$ netstat --tcp -p

```

---

### Post by spiregrain on 2006-01-29
Well, that helps- but it doesn't show which of the connections is actually putting a lot of traffic on the network.

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.0.100:58421     vicar:netbios-ssn       ESTABLISHED-
tcp        0      0 192.168.0.100:41415     imap.plus.net:imap2     TIME_WAIT  -
tcp        0      0 192.168.0.100:58179     athena.jabb:xmpp-client ESTABLISHED8399/gaim
tcp        0      0 192.168.0.100:43704     64.12.24.128:5190       ESTABLISHED8399/gaim
tcp        0      0 192.168.0.100:56167     mail.messagingeng:imap2 ESTABLISHED8405/mail-notificat
tcp        0      0 192.168.0.100:56169     mail.messagingeng:imap2 ESTABLISHED8405/mail-notificat
tcp        0      0 192.168.0.100:56170     mail.messagingeng:imap2 ESTABLISHED8405/mail-notificat
tcp        0      0 192.168.0.100:56596     baym-cs27.msgr.hot:1863 ESTABLISHED8399/gaim
tcp        0     20 192.168.0.100:51141     pinky.slashnet.org:ircd ESTABLISHED8395/xchat
```

Any thoughts on what the top two entries, which don't have process information displayed might be?

---

### Post by cwaldbieser on 2006-01-31
[QUOTE=spiregrain]Well, that helps- but it doesn't show which of the connections is actually putting a lot of traffic on the network.

```
Active Internet connections (w/o servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 192.168.0.100:58421     vicar:netbios-ssn       ESTABLISHED-
tcp        0      0 192.168.0.100:41415     imap.plus.net:imap2     TIME_WAIT  -
tcp        0      0 192.168.0.100:58179     athena.jabb:xmpp-client ESTABLISHED8399/gaim
tcp        0      0 192.168.0.100:43704     64.12.24.128:5190       ESTABLISHED8399/gaim
tcp        0      0 192.168.0.100:56167     mail.messagingeng:imap2 ESTABLISHED8405/mail-notificat
tcp        0      0 192.168.0.100:56169     mail.messagingeng:imap2 ESTABLISHED8405/mail-notificat
tcp        0      0 192.168.0.100:56170     mail.messagingeng:imap2 ESTABLISHED8405/mail-notificat
tcp        0      0 192.168.0.100:56596     baym-cs27.msgr.hot:1863 ESTABLISHED8399/gaim
tcp        0     20 192.168.0.100:51141     pinky.slashnet.org:ircd ESTABLISHED8395/xchat
```

Any thoughts on what the top two entries, which don't have process information displayed might be?[/QUOTE]

Well, imap is some sort of mail protocol.  Not 100% sure about netbios-ssn.  I think it has something to do with file shares.

---

### Post by breno leitao on 2008-05-03
> **cwaldbieser said:**
> Well, imap is some sort of mail protocol.  Not 100% sure about netbios-ssn.  I think it has something to do with file shares.
Sure, it's related to file sharing mostly used by windows network. Be aware if this problem happens even if don't have any Windows machine on your network.

Breno

---

