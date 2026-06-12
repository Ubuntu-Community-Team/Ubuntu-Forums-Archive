---
title: "Squid and request from internet"
date: 2010-10-09
forum: Networking &amp; Wireless
---

### Post by Geroz on 2010-10-09
Hi all,

I try use Squid as my proxy server.

When I set my firefox to use my proxy server (squid), all is ok, but when I set firefox on another pc (from internet, not local network), all request returned time out :(

I turn off my router and connect PC to internet (without router), but still don't work.

In iptables is all ok, I think. Where is problem? I think, It isn't problem with squid (because squid don't show error page), but I don't know how fix it :(

Thx for comments. And sorry for my english.

iptables:
```

Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination   


```



Edit: SSH from remote pc work fine.

---

### Post by Geroz on 2010-10-10
Now I tested proxy on local network and work fine. But from internet still no :confused:

---

### Post by BkkBonanza on 2010-10-10
Try ShieldsUp port scan to make sure the port is open to the net. It may be your ISP blocks ports.

[https://www.grc.com/x/ne.dll?bh0bkyd2](https://www.grc.com/x/ne.dll?bh0bkyd2)

---

### Post by Geroz on 2010-10-11
I tested it and all ports are green = stealth, but I don't know what it means.

SSH (port 22) or apache(port 80) server in my pc work fine (from remote pc).

---

### Post by SeijiSensei on 2010-10-11
Is Squid listening on the external interface?  Look at the http_port settings in squid.conf.  If you only have an entry for the internal interface, you won't be able to connect from outside.

That said, running an open proxy is an invitation to be exploited.  Are you sure you really want to do this?  Perhaps you should consider using password authentication in Squid?

---

### Post by Geroz on 2010-10-11
In configure a squid I'm begginer.


All setting is:

```
acl all src all
http_access allow all
http_port 8080
visible_hostname geroz
```I know security risk. Step 1 is run proxy. Step 2 is security.

---

### Post by SeijiSensei on 2010-10-11
When you're connecting from a machine on the Internet, are you using your Squid machine's external IP address?  If you don't have a static address, your address can change from time to time.  Run "ifconfig" on the Squid box to ascertain your current address, then try connecting to the proxy from the outside host.

Try changing the port to something unusual like a value between 20000 and 64000.  Does that help?

Try using telnet from a remote host to check connectivity.  "telnet your.squid.ip.addr your.squid.port" should get a reply from the server.  If it doesn't you're being blocked somewhere along the way.

---

### Post by Geroz on 2010-10-12
Thx all - resolved

I shutdown apache server and set squid to 80 port and ... enjoy - squid is working.

So, I change port to my favorit port 1234 and all is OK.

Special thx SeijiSensei :wink:

PS: port deflaut and 8080 in my PC isn't open (probably)

---

