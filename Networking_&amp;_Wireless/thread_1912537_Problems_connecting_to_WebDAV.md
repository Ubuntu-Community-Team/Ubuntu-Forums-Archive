---
title: "Problems connecting to WebDAV"
date: 2012-01-20
forum: Networking &amp; Wireless
---

### Post by 5circles on 2012-01-20
I'm trying to establish a connection to my external server from my LAN based Ubuntu server.  I've been able to do this manually in the past, but it isn't working properly anymore.  I've made some changes, but can't figure out what is happening.

There are two WebDAV shares on my external server.

If I connect to either of them through Nautilus using ```
davs://server:port
``` it works fine.

I added my user to the davfs2 group, and made /usr/sbin/mount.davfs2 suid.

For the new share, I set up an entry in /etc/davfs2/secrets like this:
/media/directory	username	password

and in /etc/fstab like this:
```
https://server:port/username /media/directory davfs rw,user,noauto 0 0
```

then entered
```
sudo mount -t davfs https://server:port /media/directory
```

**1st problem.**  Warnings about the server certificate not matching the server name and not being trusted. My server doesn't have a certificate, so can I override without manually entering anything?

Why do I need sudo to so this?

The other problem is that the second share (actually the main one) won't connect at all.

I'm hoping that I'm just doing a couple of stupid things wrong.

Thanks!

---

