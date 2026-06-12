---
title: "Bind problem"
date: 2013-08-27
forum: Networking &amp; Wireless
---

### Post by kovitlv on 2013-08-27
Hello everyone.
I have problem to resolve one address. Everything else works perfectly.
I will give you my dig output :
```
dig +trace www.smfg.co.jp

; <<>> DiG 9.4.2-P2.1 <<>> +trace www.smfg.co.jp
;; global options:  printcmd
.                       506689  IN      NS      b.root-servers.net.
.                       506689  IN      NS      k.root-servers.net.
.                       506689  IN      NS      m.root-servers.net.
.                       506689  IN      NS      i.root-servers.net.
.                       506689  IN      NS      l.root-servers.net.
.                       506689  IN      NS      j.root-servers.net.
.                       506689  IN      NS      g.root-servers.net.
.                       506689  IN      NS      c.root-servers.net.
.                       506689  IN      NS      d.root-servers.net.
.                       506689  IN      NS      f.root-servers.net.
.                       506689  IN      NS      a.root-servers.net.
.                       506689  IN      NS      e.root-servers.net.
.                       506689  IN      NS      h.root-servers.net.
;; Received 372 bytes from 127.0.0.1#53(127.0.0.1) in 1 ms


jp.                     172800  IN      NS      e.dns.jp.
jp.                     172800  IN      NS      b.dns.jp.
jp.                     172800  IN      NS      f.dns.jp.
jp.                     172800  IN      NS      c.dns.jp.
jp.                     172800  IN      NS      a.dns.jp.
jp.                     172800  IN      NS      d.dns.jp.
jp.                     172800  IN      NS      g.dns.jp.
;; Received 428 bytes from 192.112.36.4#53(g.root-servers.net) in 54 ms


smfg.co.jp.             86400   IN      NS      sec.smbc.co.jp.
smfg.co.jp.             86400   IN      NS      pri.smbc.co.jp.
;; Received 105 bytes from 150.100.6.8#53(f.dns.jp) in 316 ms


dig: couldn't get address for 'pri.smbc.co.jp': not found



```

Trying this on another server in different network, everything works perfectly.
For example. :
[http://]("http://digwebinterface.com/?hostnames=dig+www.smbc.co.jp&type=&showcommand=on&trace=on&ns=resolver&useresolver=8.8.8.8&nameservers=")[digwebinterface.com/?hostnames=dig+www.smfg.co.jp&type=&showcommand=on&trace=on&useresolver=8.8.8.8&ns=self&nameservers=127.0.0.1]("http://digwebinterface.com/?hostnames=dig+www.smbc.co.jp&type=&showcommand=on&trace=on&useresolver=8.8.8.8&ns=self&nameservers=127.0.0.1")


Trying to get info from pri.smbc.co.jp uzing it IP address : 


```


dig smfg.co.jp. @202.221.2.96


; <<>> DiG 9.4.2-P2.1 <<>> smfg.co.jp. @202.221.2.96
;; global options:  printcmd
;; connection timed out; no servers could be reached


```
But trying telnet to :
```


telnet 202.221.2.96 53
Trying 202.221.2.96...
Connected to 202.221.2.96.
Escape character is '^]'.
Connection closed by foreign host.


```

---

### Post by SeijiSensei on 2013-08-27
That's not a DNS problem.  The server is refusing connections from your IP.  You need to look at the logs on the server, probably either /var/log/syslog or /var/log/messages depending on the server's OS.

Of course, you shouldn't be using telnet at all since it is insecure.  Use ssh instead.

---

