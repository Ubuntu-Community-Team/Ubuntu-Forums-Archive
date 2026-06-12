---
title: "Questions about IPv6 support in dnsmasq"
date: 2010-09-10
forum: Networking &amp; Wireless
---

### Post by polomora on 2010-09-10
Hello,

We are developing a set-top box based on the ubuntu/2.6.14 kernel. We are using dnsmasq v2.32 for serving local dns requests. I know this is a fairly old version. We have a problem that when making DNS requests, client PCs running recent OSs such as Windows 7 first request an IPv6 address, and when that fails, then requests an IPv4 address. The problem is that the IPv6 responses are not cached by dnsmasq.

My questions are:
- Does the latest version of dnsmasq support IPv6 caching for both positive and negative responses?
- Is it possible to configure, and/or build dnsmasq to not handle IPv6? If this is possible, and an IPv6 request arrives, what will happen? Will dnsmasq response with a negative response? I noticed the NO_IPV6 compile-time flag in the dnsmasq code.
- I tried configuring the kernel to not support IPv6, by specifying "alias net-pf-10 off" in /etc/modprobe.conf. This didn't work, because on the set-top box, this file is copied from flash ROM memory after reboot. 

Can anyone help?

Many thanks

---

### Post by regala on 2010-09-10
> **polomora said:**
> Hello,
snip


check here : [http://www.thekelleys.org.uk/dnsmasq/doc.html](http://www.thekelleys.org.uk/dnsmasq/doc.html)

---

