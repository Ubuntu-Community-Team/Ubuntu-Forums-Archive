---
title: "/etc/hosts 127.0.1.1 performance"
date: 2010-04-02
forum: Networking &amp; Wireless
---

### Post by runtim23 on 2010-04-02
Hello,

    I've been developing a java application and had some difficulties getting jconsole to connect locally on Ubuntu 2.6.24 with java 6. I discovered if I comment out the computer_name 127.0.1.1 jconsole will connect fine. Howerver, when I do this performance drops on Ubuntu causing it to take 20 seconds for typing and applications to respond. I then discovered if I enable my networking it works fine. I then disable networking and it goes back to a crawl. My question is, why does Ubuntu behave this way? What's the significance of having networking disabled and commenting that line out? This seems to be very Ubuntu specific not including other distros so searching on the web didn't reap anything too insightful. Or maybe I didn't do a very thorough search. If anybody could take time to explain I'd appreciate it. TIA

---

