---
title: "DNS rndc help needed please assist"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by dspit1664 on 2009-03-24
Hi all,
new to forum and relatively new to DNS and rndc.

I want to setup a master/slave dns server setup.

Initially I tried to configure it using rndc however I could not get it working.

I am now wanting to try a basic config where:
On my Master I state type = master
On my Slave I state type = slave

When I restart bind eg /etc/init.d/bind9 on both my master and slave I get back the following:
neither /etc/bind/rndc.conf nor /etc/bind/rndc.key were found. failed.
In my /etc/bind/named.conf I removed any mention of rndc so wondered why when I tried to restart did it error.

How do I stop rndc and stop bind relying on it so I can start my master / slave setup running?

---

### Post by BkkBonanza on 2009-03-24
I've always felt sorry for Bind users. I think you should try posting on webhostingtalk.com - they have a lot of talented server people there. 

Myself I avoid Bind and use TinyDns - much lighter resource usage and not so complicated. You can just rsync your dns file from one server to another to update.

---

