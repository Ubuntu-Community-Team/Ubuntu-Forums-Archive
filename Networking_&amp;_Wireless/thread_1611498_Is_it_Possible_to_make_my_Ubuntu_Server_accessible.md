---
title: "Is it Possible to make my Ubuntu Server accessible with a DHCP address?"
date: 2010-11-01
forum: Networking &amp; Wireless
---

### Post by smoh on 2010-11-01
Hi all,

The cable internet I'm using runs on Dynamic DHCP IP addresses. I changed it to a static IP address in my router settings, but it keeps changing.  This means that I can't connect to my home server from a remote location.

Is there anyway to run my ubuntu server on a DHCP IP address without connecting through my router 192.168.1.xxx?

---

### Post by Barriehie on 2010-11-02
> **smoh said:**
> Hi all,

The cable internet I'm using runs on Dynamic DHCP IP addresses. I changed it to a static IP address in my router settings, but it keeps changing.  This means that I can't connect to my home server from a remote location.

Is there anyway to run my ubuntu server on a DHCP IP address without connecting through my router 192.168.1.xxx?

You can use a service like no-ip.com that will point requests to your IP.  You run a daemon on your machine that updates their server when your IP changes.

---

