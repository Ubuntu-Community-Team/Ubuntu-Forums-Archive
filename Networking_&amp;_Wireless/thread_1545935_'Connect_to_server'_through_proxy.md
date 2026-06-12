---
title: "'Connect to server' through proxy"
date: 2010-08-04
forum: Networking &amp; Wireless
---

### Post by azzid on 2010-08-04
Is there a way to connect to a samba share on the other side of a dynamic ssh tunnel?

I like to use **ssh -D 8080 <host>** to access the network on the other side of a ssh session. For applications with their own proxy settings it seem to work really nice.

In this particular case I'd like to use the 'Connect to server' feature in Ubuntu to connect a samba share through the tunnel, but I can't figure out how to make only that connection use proxy settings.

If I enforce system wide proxy settings the ssh tunnel will die, so that is not an option.

Anyone got some good ideas on how to achieve what I want?

---

### Post by tocado on 2010-08-04
There is a free software for tunneling with http headers look this
[Http Tunnel]("http://www.nocrew.org/software/httptunnel/faq.html")

to install in ubuntu
```
sudo apt-get install httptunnel
```
i hope this was useful

See ya !

---

