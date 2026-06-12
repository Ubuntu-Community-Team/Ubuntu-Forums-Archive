---
title: "TightVNC Server: Authentication failed, too many tries"
date: 2012-07-23
forum: Networking &amp; Wireless
---

### Post by ericinwisconsin on 2012-07-23
I get this error when I try to connect to the TightVNCServer on my Ubuntu box:

         Authentication Failed - Server Reports:
         Authentication failed, too many tries

If I shut down that particular instance:

tightvncserver -kill :1

and restart it, it works fine. Not a problem for me, but some other people connect to the server and they don't know how to fix that or even how to SSH.

Is this something in Tightvncserver? Is there a way to bypass this feature?

Thanks!

---

