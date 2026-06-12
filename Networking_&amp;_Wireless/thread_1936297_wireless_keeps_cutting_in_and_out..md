---
title: "wireless keeps cutting in and out."
date: 2012-03-05
forum: Networking &amp; Wireless
---

### Post by yamaha83 on 2012-03-05
So on ubuntu 10.10 my wireless would cut in and out. I have a switch on my laptop that when off is red and in is blue and randomly the light just flashes back and forth. Sometimes the web page loads sometimes not. No matter what it's slow. Well just updated to 11.10 hoping it would fix it with no change. Windows 7 has no wireless issue so not hardware related. New to ubuntu so have no idea where to start? Any help appreciated!

---

### Post by westie457 on 2012-03-05
Hi,

Can you run the following commands in a terminal please and then highlight all of the output and paste between ```
 tags by clicking the # at the top of the text window

[CODE]cat /etc/lsb-release; uname -a

lspci -nnk | grep -iA2 net

iwconfig

lshw -C network

lsmod

rfkill list all
```

Thank you

---

