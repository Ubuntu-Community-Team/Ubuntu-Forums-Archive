---
title: "How do you turn on Explicit Congestion Notification (ECN)"
date: 2009-08-30
forum: Networking &amp; Wireless
---

### Post by MechaMechanism on 2009-08-30
[SOLVED]

Edit: Monday August 31.
I solved this by using the below.
```
echo 1 > /proc/sys/net/ipv4/tcp_ecn
```Just so you know you may need a root terminal so in my case I just did ```
sudo -i
```The nifty thing is the command echo 1 > allow you to turn off and on various networking features.  Take a look in /proc/sys/.



Original post below.

Hi, I would like to try out Explicit Congestion Notification and see what happens.  I would like to know how to turn it on and off.  I am connected directly to the Internet and not through some router.  I am inspired to try it out by this blog post.  [Trying to understand TCP performance (long)]("http://blog.sesse.net/blog/tech/2009-08-30-11-33_trying_to_understand_tcp_performance.html").

Seems the blog post author also created an awesome TCP check site here: [http://tcpmeasure.sesse.net:8008/](http://tcpmeasure.sesse.net:8008/)

---

