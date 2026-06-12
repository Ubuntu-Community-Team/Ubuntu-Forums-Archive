---
title: "Ubuntu Connected to wireless but no internet"
date: 2010-11-07
forum: Networking &amp; Wireless
---

### Post by ryan.oflaherty on 2010-11-07
Hey everybody,
 
Im using a laptop with a wireless card inside it is a Realtek RTL8187B network adaptor. I go to wireless connections in the toolbar at the top of the screen and click on my internet modem and it says its connected. So I go to firefox and it brings up google. I try and do a search and it says something and at the bottom of the page it displays a button that says "Try Again". Im booting ubuntu from the cd drive so its not installed on my computer what should i be trying?

---

### Post by dineshs on 2010-11-08
Please post results of
```
ping 4.2.2.1 -c3
```
```
sudo lshw -C network
```and```
iwconfig
```

---

### Post by ryan.oflaherty on 2010-11-08
I figured it out it was that the IPV6 was set to false and it needed to be true. that is what was giving me the problems in firefox thanks though

---

