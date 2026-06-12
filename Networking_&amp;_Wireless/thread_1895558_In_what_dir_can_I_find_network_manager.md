---
title: "In what dir can I find network manager"
date: 2011-12-15
forum: Networking &amp; Wireless
---

### Post by Fertech on 2011-12-15
I'm using ubuntu 10.04LTS and i'm looking to see in what dir is my network manager

---

### Post by SlugSlug on 2011-12-15
not sure about net manager, but if its configs your after; disable / remove network-manager

and edit

/etc/network/interfaces


you'd want to make sure you know what your doing before removing network manager as you'll be without the net

---

### Post by matt_symes on 2011-12-15
Hi

Configuration files are in

```
ls /etc/NetworkManager/
```The executable is in

```
/usr/sbin/NetworkManager
```Keys and things (for wireless) are kept in Seahourse.

nm-applet is in

```
/usr/bin/nm-applet
```NetworkManager uses the networking scripts of networking.

```
/etc/network
```

State information is kept in

```
/var/lib/NetworkManager
```

What exactly are you looking for ?

Kind regards

---

### Post by Fertech on 2011-12-15
I'm looking for the Configuration files

---

