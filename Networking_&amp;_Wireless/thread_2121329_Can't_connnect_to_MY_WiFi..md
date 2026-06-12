---
title: "Can't connnect to MY WiFi."
date: 2013-03-01
forum: Networking &amp; Wireless
---

### Post by TheMophead on 2013-03-01
I recently purchased a new Laptop, (The Dreaded Lenovo G580 that is causing so many problems on here..) and like every one else, I had internet related issues.

The first problem I encountered was WiFi access in general. The only router I could see was my own and even when I was less than 15cm away from the router, my connection was still on 1 bar. When I connected to the router at this point, I was able to connect for arround 10 - 20 Seconds then I was disconnected. I did some searching and I found some packages to install, (I downloaded the neccesary .deb files on Windows and put them on a USB Stick) My WiFi was then working properly.. BUT.. I had another issue, I was unable to connect to my Router at all, (Other routers in my area where visible now so the Wireless was definitely working). I was able to connect to my neighbours Wireless and the Wireless we have at work which confirms the drivers where working properly..

Oh, and my 10/100 Ethernet port doesn't work either.

I'll do a reboot, go back into Ubuntu and use iwconfig, then post the results.

---

### Post by praseodym on 2013-03-02
Please show the outputs of:
```

uname -a
lspci -nnk | grep -iA2 net
lsmod
iwconfig
rfkill list
cat /etc/resolv.conf
```

---

