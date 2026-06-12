---
title: "2 interfaces - 1 static, 1 dhcp. How?"
date: 2009-04-30
forum: Networking &amp; Wireless
---

### Post by Roasted on 2009-04-30
I have an Ubuntu laptop with 9.04 that I run at work for imaging purposes with FOG that runs within Ubuntu. FOG uses a web based frontend, so I need to have a static IP set so I can manage FOG itself and so the clients know where to connect each time.

When I edit the interfaces file and give myself and IP of 192.168.1.100, I have the IP whether or not I'm connected to anything. So I can be disconnected and when I hit the icon to launch FOG's web based frontend, I can see it just fine.

When I set my static IP through network manager, I have to be plugged into a switch of some sort before it activated that static IP. So ultimately I need to be plugged into a switch just to run FOG. This isn't a possibility.

But, to get newer kernels and such for FOG, along with Ubuntu updates, it was nice having my wireless as DHCP, which is what I did in 8.10.

However, now I can't get them both to co-exist. At least, not completely. When I set my interfaces file to control eth0 (the main wired port for FOG), but let Network Manager control eth1 (wireless) with DHCP, it works fine. I can hit FOG and get out to the network and all.

BUT - I cannot connect to my router @ 192.168.1.1. And I have no clue why. How is it I can get to cnet.com and ubuntu.com yet I can't get to my own router's IP address? But this is only true if I have interfaces file with eth0 and eth1 with Network Manager. 

Does this make sense??

---

### Post by iiiears on 2009-05-01
Hello,

I wonder if this was what you are looking for?

[http://en.kioskea.net/faq/sujet-1089-sharing-internet-connection-using-bridge-mode](http://en.kioskea.net/faq/sujet-1089-sharing-internet-connection-using-bridge-mode)
Your /etc/network/interfaces file must look like this:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
address 10.0.0.1
netmask 255.255.255.0

Best Wishes.

---

### Post by Roasted on 2009-05-01
But with the DHCP interface being my wireless, how do I scan for wireless networks if the interfaCES file is taking control of everything?

---

### Post by chili555 on 2009-05-01
```
sudo iwlist eth1 scan
```

---

