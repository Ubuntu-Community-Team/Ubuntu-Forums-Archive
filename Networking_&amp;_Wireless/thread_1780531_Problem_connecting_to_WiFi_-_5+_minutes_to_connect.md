---
title: "Problem connecting to WiFi - 5+ minutes to connect."
date: 2011-06-12
forum: Networking &amp; Wireless
---

### Post by rayredmond on 2011-06-12
I have been using Ubuntu for about 6 months now.
I have been suffering with my Wifi connection taking five minutes, and many times longer to connect to my wireless router.

My wireless router is a linksys WRT110, without a network security password, latest patch installed. When I was running WIndows 7 ](*,), it was instantly connected to my router. I am currently running Ubuntu 10.10 because v.11.04 was taking almost 10 minutes to connect. My internal computer's 'router' is Atheros [spelling].

Is there a work around so that I can get connected to my WiFi quicker? 

Thanks in advance.

---

### Post by poolet on 2011-06-12
Open up a new terminal and type: 

```
lshw -C network 
``````
lsmod | grep network
```or (if isn't output anything) 

```
lsmod
```and paste the output here!!!

---

