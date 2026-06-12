---
title: "Do I have a DNS leak in Firefox 3.6?"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by shd68 on 2010-11-07
Hello.  I'm using an SSH tunnel on Firefox 3.6.12 and I believe that DNS queries are being leaked.

I am forwarding my SSH connection using the following command:

```
ssh -vN -D 3000 <user>@<host>
```Under Firefox's connection settings, I have selected "Manual proxy configuration" and I have all of the fields blank except for "SOCKS Host" which is set to "localhost" on port 3000 and "No proxy for" which is set to "localhost, 127.0.0.1".

In about:config, the value of network.proxy.socks_remote_dns is set to "true".  (I have restarted Firefox a few times since I set this.)

I know that my SSH tunnel is working because when I view network traffic using Wireshark, all web traffic is marked as "TCP" and goes between my computer and the remote host.  However, DNS queries are still leaked to the nameserver defined in /etc/resolv.conf.  (The nameserver is my wireless router.)

I have read about this problem happening in Firefox 3.5, but I haven't seen any mention of it in 3.6.  E.g.:

[http://edge.i-hacked.com/firefox-35-dns-leaks-like-a-waterfall](http://edge.i-hacked.com/firefox-35-dns-leaks-like-a-waterfall)

Basically, my problem is the exact same as the person's on that page.

I'm not using FoxyProxy, fwiw.

Thanks for any help.

---

### Post by shd68 on 2010-11-09
Bump.

---

### Post by shd68 on 2010-11-12
I'm going to try bumping one last time.

---

