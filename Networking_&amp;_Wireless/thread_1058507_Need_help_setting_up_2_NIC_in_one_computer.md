---
title: "Need help setting up 2 NIC in one computer"
date: 2009-02-02
forum: Networking &amp; Wireless
---

### Post by paleo on 2009-02-02
Ok I am a newb when it comes to linux. What I am wanting to do is I have a Vista business box and an Ubuntu 8.10 running Gnome and they are both on a wireless home network of 192.168.1.x  I have Samba set up but the transfer rate is only around 200k because I am sending and receiving both wireless because the router is downstairs and my computers are upstairs. I have a crossover cable and each box has a second on board gb nic. I want to set up the two nics on a 10.0.0.x and beable to transfer at higher speeds. please help me and step by step instructions please.

---

### Post by nixscripter on 2009-02-03
Windows, it's been a long time, I forget. Something under the Networking control panel, but you give the wired card a "manual" address.

Linux, it's easy. Open a terminal and type: ```
sudo ifconfig eth0 10.0.0.2 up
```

To give it the IP address. Give windows another one on the same 10.0.0.x network, and it should just work.

Hope this helps.

---

