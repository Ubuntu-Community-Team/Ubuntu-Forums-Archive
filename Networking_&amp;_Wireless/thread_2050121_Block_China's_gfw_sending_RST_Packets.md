---
title: "Block China's gfw sending RST Packets"
date: 2012-08-30
forum: Networking &amp; Wireless
---

### Post by steviematt on 2012-08-30
Hi,

I'm living and working in China right now and apart from the  shockingly slow internet speeds here I have found the gfw to be somewhat  problematic.

I have a VPN setup and it works fine...  it's much  slower in China than it was in the UK but this is simply because China  likes to monitor and throttle any connections that are not to trusted  (chinese) ip's but it works.

However, i noticed China's gfw does  not simply block ip's of certain websites, it also likes to send RST  packets for websites that are not blocked but may contain certain  sensitive words. A good example of this is google news, sometimes it  works and sometimes it doesn't. When it doesn't work i get "The  connection has been reset while the page is loading" error. 

Basically I just want someone who is savvy with iptables to show me a rule that would allow me and possibly all other Chinese users using linux distros to block the RST packets sent by China's gfw.

---

