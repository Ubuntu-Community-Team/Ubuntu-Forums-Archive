---
title: "How use socks5 proxy in Ubuntu ?"
date: 2012-01-06
forum: Networking &amp; Wireless
---

### Post by ahadyekta on 2012-01-06
I want to send all connections through Socks5 proxy , when I add proxies in firefox network option , it use http proxy to load websites , but i want to use just socks , beacuse in my country http proxy is ban in some reasons . 
Proxifier in Windows work good , send all connection to socks , bust i want some softwar ein ubuntu . 

Also i installed Proxychain 3.1 and configured it :
```
random_chain
chain_len = 1
tcp_read_time_out 15000
tcp_connect_time_out 10000
[ProxyList]
socks5 	IP 1080 user pass
```

but when i open firefox my Ip Address did not change . 
also in terminal i use proxychain as a prefix to open a website in firefox but also did not change . 

please Help me

---

### Post by groksteady on 2012-01-06
can you open a terminal and ssh to your account?

ssh -ND 1984 user@host.tld

and then you can add that to your network settings in Firefox, or use the FoxyProxy add-on to manage it.

---

### Post by ahadyekta on 2012-01-07
The Server i want to connect to is windows server 2003 and installed CCproxy for creating socks5 proxy accounts . I cant connect via SSH to it . 
I use Proxifier in windows 7 and works good it forwards any connections through socks5 , i want to use something like this here . or just makes firefox to uses socks5 . 

some body offered me to use TOR and enter my dedicated host name and use:pass to connect through TOR to that server . does it work? how can i configure that to use just my server ?

---

