---
title: "Content filtering with squid and ufw"
date: 2010-05-10
forum: Networking &amp; Wireless
---

### Post by qforce on 2010-05-10
Hi all,

I'm trying to set up a content filter on a single machine using ufw and squid 2.7.

First, I set up Squid: In /etc/squid/squid.conf, I have my ACLs and the line "http_port 8080 transparent". This is working fine so far.

However, since it's possible to bypass the squid proxy by setting "no proxy" in the Firefox network settings, I tried to block all traffic that doesn't go through port 8080 using the following ufw rules:

ufw enable
ufw default reject incoming
ufw default reject outgoing
ufw allow 8080

Unfortunately, this does not work: All traffic is blocked. I tried a couple of other things as well, but basically I'm at my wit's end here. Any idea what could be wrong with my setup? Thanks in advance!

---

