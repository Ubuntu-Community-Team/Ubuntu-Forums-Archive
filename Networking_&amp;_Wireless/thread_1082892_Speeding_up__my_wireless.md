---
title: "Speeding up  my wireless"
date: 2009-02-28
forum: Networking &amp; Wireless
---

### Post by wbrokow1 on 2009-02-28
Luckily my WG511 netgear wireless card works on my ancient ibm a22m laptop with 8.10, the only problem is that the speed is usually 1-5 Mbps.  I am right near the dlink dir-655 router and the signal is usually 85-100%.

My question is : Is there a way to tweak  the settings somehow to speed up the connection?

Thanks  for any guidance.

---

### Post by scratman on 2009-02-28
Please can you provide the specifications for your laptop and router? Are you using an built-in wireless adapter on your laptop, or USB.  If it's USB, I'm prepared to bet that it's either only capable of running USB1.1, or it is currently running on that protocol and needs to be changed to 2.0.  If you do not have any USB2.0 ports, there's not a lot you  can do unless you run an Ethernet cable to your router, as 1.5Mbps is the maximum transfer rate of USB 1.1.

---

### Post by wbrokow1 on 2009-02-28
The wireless card is a pcmcia.Net gear WG511 w/prism54 chip
The router is a combination wireless point,wired and router. I have static IP addresses.  THe Router  is a Dlink-655. I believe it's spec'd at 54Mbps, so is the card.

[http://www.dlink.com/products/?pid=530](http://www.dlink.com/products/?pid=530)

Is this the info you need?

---

### Post by darco on 2009-02-28
Run iwconfig in a terminal and it will inform you what your bit rate is...should show 54m.....

darco

---

### Post by wbrokow1 on 2009-02-28
it's showing 6-10 Mb/s max

---

### Post by darco on 2009-02-28
If you do have a "G" wl card the run:

```
sudo /etc/init.d/networking restart
sudo iwconfig wlan0 rate 54M
```

good luck

darco

---

