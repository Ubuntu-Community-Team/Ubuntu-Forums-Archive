---
title: "proxytunnel socket read error 12.04"
date: 2013-03-20
forum: Networking &amp; Wireless
---

### Post by timrichardson on 2013-03-20
I have an ubuntu 12.04 LTS server. I've set up proxy server on apache2, on port 443.
The server serves SSL web pages, and I can ssh to the server from a remote shell. I can connect to ssh with a password.
I've set up proxytunnel so I can ssh to it from anywhere.

I get this Socket read error. Why? 
(churchill is my latpop, accessing the system. )

```
churchill:~ tim$ proxytunnel -E -p ec2.growthpath.com.au:443  -d 127.0.0.1:22 -N -P tim -v
Enter local proxy password for user tim: 
Build Type 1 NTLM Message : TlRMTVNTUAABAAAAAAAAAAeCCKIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==
Local proxy ec2.growthpath.com.au resolves to 54.243.214.78
Connected to ec2.growthpath.com.au:443 (local proxy)

Tunneling to 127.0.0.1:22 (destination)
Communication with local proxy:
 -> CONNECT 127.0.0.1:22 HTTP/1.0
 -> Proxy-Authorization: NTLM TlRMTVNTUAABAAAAAAAAAAeCCKIAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA==
 -> Proxy-Connection: Keep-Alive
error: Socket read error.
```

On the server, I have defined 

```
ProxyRequests On
AllowCONNECT 22
ProxyVia        On
<Proxy *>
        Order deny,allow
        Deny from all
</Proxy>
<Proxy 127.0.0.1>
        Order deny,allow
        Allow from all
</Proxy>
```

---

### Post by impedator on 2013-09-16
Hello,

anyone can help with this error? My situation is the same, except my proxy don't need authentication.

---

### Post by gustave-pate on 2013-12-11
Same problem here does anyone has a clue ?

Server side response is 200 thne proxytunnel crashes...

---

