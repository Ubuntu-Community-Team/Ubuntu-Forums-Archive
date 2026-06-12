---
title: "Virtual Network adapter?"
date: 2009-11-01
forum: Networking &amp; Wireless
---

### Post by kartal on 2009-11-01
Hi

Under windows I was using this loopback network adapter  trick to divert certain ports to other ones via my SSH on another Linux laptop. So for example I have created a loopback adapter that was 10.0.0.5 on my windows pc and my ssh session would forward linux 192.168.2.110:8118 to 10.0.0.5:8118 (which is privoxy proxy default port). Then I would put 10.0.0.5:8118 into my FF proxy page. I end up channelling all my internet through my Linux privoxy server. 

I am wondering  if there is a way to create a virtual fake network adapter in similar fashion in Ubuntu? I know I can forward 192.168.2.10:8118 to localhost:8118. I just want to be able to use a loopback style network ip table because I can then create different masks not just local host


thanks

---

