---
title: "One NIC gateway?"
date: 2011-03-31
forum: Networking &amp; Wireless
---

### Post by mosestruong on 2011-03-31
Just wondering, is it possible to set up a "gateway" with just one network interface? Basically, I have a cable wireless router which is connected to the internet. I want to have my network use a transparent proxy, however, the transparent proxy is on an ARM computer with only one network interface.
So the proxy will act as the "gateway", which then forwards all external request to the Cable modem.

```
      Cable Modem            Proxy
           |                   |
      +----+----+---------+----+----+
      |         |         |         |
    Comp1     Comp2     Comp3     Comp4
```

Now, I need the cable modem to be in the same network, because I want to use it's wireless access point...

Do I need to have two subnets? one between the Cable modem and the proxy, and then a second subnet as a virtual interface on the proxy to communicate with all the computers?

---

### Post by Grenage on 2011-03-31
From a network point of view, it shouldn't be a problem.  A proxy doesn't 'need' to be a gateway, nor does it need to have a separate subnet between it and a router.

We use a caching proxy server (ISA), which is on the same subnet as the workstations and gateway's network interface.

---

### Post by mosestruong on 2011-03-31
But I want the proxy to be transparent, so doesn't that make it necessary for it to be the gateway too?

---

### Post by Grenage on 2011-03-31
Ah yes; sorry.

In which case you are correct, you simply need to create a second connection on the same nic, using a second subnet which will match the internet router.  As long as the proxy is configured to route the data, it should be fine.

---

### Post by Grenage on 2011-03-31
I quick search revealed [this]("http://teladan98.wordpress.com/2007/12/05/transparent-proxy-server-with-one-nic/"), which you may find useful.

---

