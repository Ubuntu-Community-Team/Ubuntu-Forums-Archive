---
title: "/proc/sys/net/ipv4/conf question..."
date: 2012-07-25
forum: Networking &amp; Wireless
---

### Post by beradero on 2012-07-25
Hello,
I reading about Linux hardening, but when it comes to kernel parameters  configuration
I have a small doubt.

Some tutorials tell you to change network options this way:
echo 1 > /proc/sys/net/ipv4/conf /[COLOR=Red]all[/COLOR]/rp_filter

other, this way:
echo 1 > /proc/sys/net/ipv4/conf /[COLOR=Red]default[/COLOR]/rp_filter

and others, tell you to to change both ways:
echo 1 > /proc/sys/net/ipv4/conf /[COLOR=Red]all[/COLOR]/rp_filter
echo 1 > /proc/sys/net/ipv4/conf /[COLOR=Red]default[/COLOR]/rp_filter

What is the difference, and what is the correct way to change network options?

---

