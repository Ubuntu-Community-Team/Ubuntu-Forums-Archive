---
title: "SSH giving &quot;&quot;"
date: 2012-07-21
forum: Networking &amp; Wireless
---

### Post by East Asia Student on 2012-07-21
I'm trying to SSH to my webhost but get this error when I run ssh:

```
ssh xxxxx@xxxxx.net
ssh: connect to host xxxxx.net port 22: Network is unreachable
```I can connect to the internet without issue and ping the same server, just not SSH to it for some reason. That error message means there's a local problem, right? SSH is unable to connect to the Internet. If it's not a local problem then I'll take it up with my webhost.

This is similar to the issue at [http://ubuntuforums.org/showthread.php?t=1529943](http://ubuntuforums.org/showthread.php?t=1529943) but I have normal Internet access, and the files described there are all at default values.

Any ideas what could be causing this?

---

### Post by bakegoodz on 2012-07-21
It could be caused by a few different things. When I see this message it useally means that I forgot to install the ssh server package. Nearly all VPS hosts have web terminal access in the mangament console. the're often show and clunky, but are nice you when you can't ssh. If this isn't a VPS, then you will have to carefully read the web hosts docs on how to do shell access (If they even allow you)

---

