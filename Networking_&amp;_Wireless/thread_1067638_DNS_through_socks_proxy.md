---
title: "DNS through socks proxy"
date: 2009-02-12
forum: Networking &amp; Wireless
---

### Post by Tex-Twil on 2009-02-12
Hello,
I have a ssh tunnel (ssh -D 53 myserver.com) to my homeserver and I'd like that the DNS requests are passed through that tunnel instead of being sent to my current DNS server. I added edited the /etc/resolv.conf and put

```

# cat /etc/resolv.conf
search mydomain.loc
**nameserver 127.0.0.1**
nameserver 192.168.0.1  # current DNS server that I don't want to use

```

I hoped that during a DNS request the 1st server will be tried but all the DNS traffic is still going to the 192.168.0.1 server.

Any ideas how to do that ?


Thanks,
Tex

---

### Post by dmizer on 2009-02-12
SSH and socks are TCP. DNS is UDP. It's possible, but extremely difficult and potentially unstable to forward DNS over SSH.

If you need both proxy and DNS, you're better off with VPN.

Sorry :(

---

### Post by Tex-Twil on 2009-02-12
> **dmizer said:**
> SSH and socks are TCP. DNS is UDP. 


ahhh right :)

ok then I'll leave it like it is.
Thanks

---

### Post by Tex-Twil on 2009-02-23
Hello,
I've just found [this article]("http://www.outflux.net/blog/archives/2006/12/07/paranoid-browsing-with-squid/") which explains how to tunnel DNS via the SOCKS5 proxy in Firefox. It works great ;)

Tex

---

### Post by quequotion on 2009-03-07
> **Tex-Twil said:**
> Hello,
I've just found [this article]("http://www.outflux.net/blog/archives/2006/12/07/paranoid-browsing-with-squid/") which explains how to tunnel DNS via the SOCKS5 proxy in Firefox.

is there a way to do this for any other programs under the sun?

is there a way to do this and make it a system-wide setting?

---

