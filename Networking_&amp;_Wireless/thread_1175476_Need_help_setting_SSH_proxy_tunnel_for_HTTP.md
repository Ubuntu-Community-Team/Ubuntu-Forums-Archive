---
title: "Need help setting SSH proxy tunnel for HTTP"
date: 2009-06-01
forum: Networking &amp; Wireless
---

### Post by diablo75 on 2009-06-01
I've found several guides that say you use a command similar to this one:

```
ssh -D 9999 username@ip-address-of-ssh-server
```

When I run this command, it appears to connect correctly to my remote PC at home, and I end up at a command prompt for my remote username and PC.  For the sake of the example above, lets say I actually specified port 9999 in the command.  When I set firefox to use a manual proxy with the address of "localhost" and port number "9999", I go to test it out.  If I typed [www.google.com](www.google.com) in, Firefox loads a completely blank page, and the status at the bottom says Done.

So I'm not sure what I'm not doing or have done wrong.  Was I suppose to run the above command with sudo?

---

### Post by puppywhacker on 2009-06-01
ports higher than 1024 do not require sudo privileges. "Only root can forward privileged ports".

As for the -D. this will act as a socks-server, not as an http-proxy. What I usually do is create a tunnel using port forwarding with "-L 8080:localhost:8080" as option to the ssh command and on port 8080 I run a squid proxyserver that is only allowed to proxy for everything from localhost.

---

### Post by ktrnka on 2009-06-01
You need to change the SOCKS Host line to localhost not the HTTP Proxy.

---

