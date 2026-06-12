---
title: "Corkscrew tunneling with multiple proxy"
date: 2009-03-31
forum: Networking &amp; Wireless
---

### Post by junke1990 on 2009-03-31
Hey guys

This is my case: I'm at school behind a big pain in the *** proxy and a friend of mine has a fedora server i want to connect to. 

I tried the following but it aint working,

```

host rubik-proxy
  hostname rubik.cluenet.org
  port 22
  user [my username]
  ProxyCommand corkscrew 172.26.20.2 8080 %h %p

```

the 172.26.20.2 is the proxy of school and is only accepting connections on port 8080 but when I try this I get the following:

```

Proxy could not open connnection to rubik.cluenet.org:  Proxy Error ( The specified Secure Sockets Layer (SSL) port is not allowed. ISA Server is not configured to allow SSL requests from this port. Most Web browsers use port 443 for SSL requests.  )
ssh_exchange_identification: Connection closed by remote host

```

so I'm guessing that the proxy doesnt forward anything else then port 80 aka http traffic and as far as i know it doesnt look at content.

Rubik, which I'm trying to connect to has a local proxy build in at port 80 so if port 22 is closed we can connect through port 80 which is usually open. 

I cant seem to figure out how to build up the config to try this is...

---

### Post by netztier on 2009-03-31
> **junke1990 said:**
> 
I cant seem to figure out how to build up the config to try this is...

Try this: run the SSH server on the remote site on 443. HTTPS or SSL commonly run on 443, and when used with a proxy, the CONNECT proxy method is used (as opposed to the GET method for the common accessing-a-web-page-with-HTTP).

A lot of proxies deny the CONNECT method for anything else than remote port 443, so that tunneling through the proxy becomes difficult. Yet, to make HTTPS/SSL work properly, they have to allow CONNECT if the remote destination port is 443. So, running SSH on 443 or making it available on 443 (with port forwarding/port translation on the firewall or NAT router) at the remote site helps quite a bit.

regards

Marc

---

### Post by junke1990 on 2009-03-31
thanks :) gonna try that as soon as i get home 

thanks!!!

---

### Post by burstmode on 2009-07-29
One other thing to watch out for - you might have to use the ip address when doing the ssh command like this (DNS lookup will happen <from> the proxy server, so it won't know about any locally defined host entries).

---

