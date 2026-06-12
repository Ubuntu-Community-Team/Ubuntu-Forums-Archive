---
title: "HTB trafic shaping and iptables"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by freddark on 2009-01-21
Hello everyone,

This is my first post and it's not a very basic question, but if anyone here can help me i would really appreciate it.

I need to do this more as a "homework" and i really don't know where to start :

I have the following ip class : 172.19.1.0/24. I need to split the IPs by the last octet like : 4k, 4k+1, 4k+2, 4k+3.
Then, using HTB, i need to ensure guaranteed bandwidth and maximum traffic, like this :
IP -> speed -> maximum traffic
4k ->1mbit ->1GB
4k+1 -> 2mbit ->2GB
4k+2 -> 3mbit -> 3GB
4k+3 -> 4mbit -> 4GB

Then, i need to make accounting using IPTABLES, and when the maximum traffic limit is reached, cut the bandwidth to half :
4k -> 512kbit
4k+1 -> 1mbit
4k+2 -> 1536kbit
4k+3 -> 2mbit

I know this might be too much but i'm afraid i only have a vague idea on how to do the guaranteed bandwidth part, and no clue on how to do the accounting.

Thank you in advance.

---

