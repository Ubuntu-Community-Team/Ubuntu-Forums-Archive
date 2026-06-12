---
title: "Monitor network traffic on server"
date: 2009-06-26
forum: Networking &amp; Wireless
---

### Post by R.Bucky on 2009-06-26
I host my sites at home and want a method of viewing live network traffic usage from another Linux box on the network. Can conky be installed and configured so that I can display stats from anther machine on the network? Thinking out loud... What options do I have?

---

### Post by superprash2003 on 2009-06-27
you could try a software called woopra.. another service called feedjit

---

### Post by mhgsys on 2009-06-27
apt-cache search iptraf

iptraf - Interactive Colorful IP LAN Monitor
ethstatus - console-based ethernet statistics monitor

Does that perhaps answers your question?

---

### Post by R.Bucky on 2009-06-27
i tried out ntraf on my local machine. it is similar to what I am looking at implementing. However, it only shows the traffic to and from the local machine. Perhaps, there is a config option that I missed that pulls traffic from the entire network. My server is not gui, and I do not want to ssh into the box to see traffic stats. 

ethstatus is simple, but only show the local machine.

I tried Woopra when it first came out. It is too heavy on system resources for my taste.

What else is available?

---

