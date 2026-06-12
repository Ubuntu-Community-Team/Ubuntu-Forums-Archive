---
title: "Commas (,) between search domains when on DHCP"
date: 2009-05-05
forum: Networking &amp; Wireless
---

### Post by haraldmilz on 2009-05-05
Hi all,

Our MSDHCP is configured to deliver 3 search domains:
- home.dom
- server.server.dom
- systems.dom

The /etc/resolv.conf file looks like this:

search home.dom, server.server.dom, systems.dom

This will not do and I have to edit the resolv.conf file every time I boot so it looks like this:

search home.dom server.server.dom systems.dom

Why is this happening? Has anyone had an issue like this?

I have posted a bug report but haven't received any answer yet (sad):

[https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/288052](https://bugs.launchpad.net/ubuntu/+source/gnome-system-tools/+bug/288052)

Any help is appreciated.

---

