---
title: "eth1 should be changed to wlan0"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by asmolinski on 2012-05-09
When I do an ifconfig, I do not have a wlan0 interface. I am connected wirelessly. The info showing up in eth1 should be the wlan0. How do I fix this issue?

---

### Post by 2F4U on 2012-05-09
May I ask why this is an issue? Is wireless working? I am also connected wireless at the moment and the alias is also eth1, but it works without problems.

---

### Post by arubislander on 2012-05-09
I agree with the previous poster. This should not be categorized as an issue. I think it depends on the driver and hence the wireless network device which interface is created: eth1, wlan0 or ath0.

---

### Post by asmolinski on 2012-05-09
I am using wireshark and my eth1 or eth0 are not even showing up as an interface. I know wlan0 will show up.

---

### Post by asmolinski on 2012-05-09
I should have mentioned this. I am using ubuntu 12.04 LTS. This did not happen in 11.10

---

### Post by arubislander on 2012-05-21
OK. And you're sure that it is your wireless interface that is erroneously being labelled eth1?

---

### Post by asmolinski on 2012-05-29
Yes, I am only connected wirelessly. I have yet to try to connect wired.

---

### Post by hawkmage on 2012-05-29
Here is a link to the FAQ for Wireshark that list a few reasons that an interface won't show up: [http://www.wireshark.org/faq.html#q9.1](http://www.wireshark.org/faq.html#q9.1)

Also you may want to take a look at: /usr/share/doc/wireshark-common/README.Debian

It talks about getting wireshare to run with Debian types of linux.  

Basicall you should run:
```
sudo dpkg-reconfigure wireshark-common
```
Then add your user ID to the wireshark group.

---

### Post by wildmanne39 on 2012-05-29
Hi, wireless showing as eth1 or wlan0 depends on the driver being used and that can change from one release to the next but as long as your wireless is working it makes no difference unless there is a reason it has to be named a certain way but for ubuntu there is not.
Thanks

---

### Post by asmolinski on 2012-05-30
Thank you everyone, I have figured it out.

---

### Post by t3ch on 2012-12-16
> **asmolinski said:**
> Thank you everyone, I have figured it out.

helo, can you tell us how u fix that eth1 back to wlan0 because some programs are not working as iwlist or aircrack..

tnx

---

