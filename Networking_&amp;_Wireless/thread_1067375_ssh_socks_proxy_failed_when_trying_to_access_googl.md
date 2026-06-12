---
title: "ssh socks proxy failed when trying to access google using firefox web browser"
date: 2009-02-11
forum: Networking &amp; Wireless
---

### Post by ddmdllt on 2009-02-11
Hi,

I am using a socks proxy (not all the time, since I'm experimenting the problem) and I fail to see google pages (google.*,gmail.com) under firefox.

I launch the proxy by using one of the following commands :

```
screen ssh -ND 3333 david@localhost
```
*or*
```
screen ssh -ND 3333 david@my_private_ovh_rps_server.example.net
```

Then I configure firefox to use localhost:3333 as a socks proxy with the appropriate settings.

I'm then able to see nearly all the pages, but neither google.com/fr nor gmail.com are able to be displayed (if the previous state of the tab is blank, it stays blank, else it doesn't change).

The fact that it fails even when I use the first variant shows me that it is not a problem of blacklisting made by google.

The second variant shows me that i'm really using a socks proxy (IP verified with whatismyipaddress.com).

If it does matter, my firefox version is "Firefox/3.0.5" and i'm running kubuntu 8.04. When connecting to a remote server using ssh, it was a debian one.

I've tried to do some googling about the problem, as well as some internal search on this forum, playing with the words "ssh", "socks", "firefox" and "google", but I didn't noticed anything relevant.

If anyone has an idea of what I need to do in order to solve the problem or just to have a better diagnostic ;)

---

### Post by ddmdllt on 2009-02-12
Hi again,

Some news : I'm able to get it working with [the network.proxy.socks_remote_dns=true setting]("http://kb.mozillazine.org/Network.proxy.socks_remote_dns") in firefox.

It solved the problem when using the socks proxy either when connecting to localhost via ssh or when connecting to a remote server (see the two previous examples).

However I still have some questions :
[LIST=1][*]Why are google.* and gmail affected by this trick and not other sites ? (although this may not be the ideal forum for this question)
[*]How the things may be different with the new settings when ssh-ing to localhost to create the "socks proxy"?
[/LIST]

Since the second question is really about a problem that is not clearly identified yet, I prefer to avoid marking the topic as resolved now.

Thanks to all visitors that have read the topic with the hope to be able to answer. One thing you may easily do to help me a little is just making a socks proxy on localhost and tell if you experiment the same problem or not.

---

### Post by myha on 2009-05-15
> **ddmdllt said:**
> I'm able to get it working with [the network.proxy.socks_remote_dns=true setting]("http://kb.mozillazine.org/Network.proxy.socks_remote_dns") in firefox.

ah, thanks for this, saved my day. :) I dont understand why this is not on by default.

---

