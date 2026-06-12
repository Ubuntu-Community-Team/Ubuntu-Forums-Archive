---
title: "Server &gt; PS3 Network Bridge"
date: 2012-05-20
forum: Networking &amp; Wireless
---

### Post by Hwest on 2012-05-20
Hey guys,

I want to bridge my wlan0(Connected to internet via router) to my eth0(Connected to PS3). Some requirements:
I need to access the internet on both server and PS3.

PS3 Net speed needs to be as fast as possible, I know wifi will bottleneck but I need the speed to be the same as a direct router connection.

LAN from server to PS3 with the cable needs to be faster than wifi when streaming from server to PS3.

A bit of a "map"

Internet>router>----WIFI---->Server>----ETHERNET---->PS3

My hardware:
PS3 Slim edition with latest firmware.
Ubuntu server 12.04, 2.8Ghz Single core sempron, 2gb ram, Onboard ethernet and D-Link wifi PCI card.
Billion BiPAC 6404VGPR3 Router.

Any help with this would be great.
Thanks in advance

---

### Post by Hwest on 2012-05-21
Anyone? Please, I need some help with this

---

### Post by Hwest on 2012-05-22
Bump?

---

### Post by lukeiamyourfather on 2012-05-22
Try this guide.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

There are various other guides if you search.

---

### Post by Hwest on 2012-05-22
I have found many guides with google, but they are either written for people with 1000000 years experience or are missing bits, I cant find anything thats written simple that actually works

---

### Post by lukeiamyourfather on 2012-05-22
> **Hwest said:**
> I have found many guides with google, but they are either written for people with 1000000 years experience or are missing bits, I cant find anything thats written simple that actually works

There are many guides out there with less detail like this one.

[http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/](http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/)

---

### Post by Hwest on 2012-05-22
> **lukeiamyourfather said:**
> There are many guides out there with less detail like this one.

[http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/](http://www.makeuseof.com/tag/how-to-easily-share-your-wireless-connection-in-ubuntu-9-10/)

Thanks, But im running server, Not desktop.
How can I do this in terminal?

---

### Post by Hwest on 2012-05-23
Anyone?

---

### Post by lukeiamyourfather on 2012-05-23
> **Hwest said:**
> Thanks, But im running server, Not desktop.
How can I do this in terminal?

That's covered in the first link I posted. Here it is again.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

There's no single command to just make it work. If that's what you're looking for then just buy a network bridge like this one.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156307](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156307)

---

### Post by Hwest on 2012-05-23
> **lukeiamyourfather said:**
> That's covered in the first link I posted. Here it is again.

[https://help.ubuntu.com/community/Internet/ConnectionSharing](https://help.ubuntu.com/community/Internet/ConnectionSharing)

There's no single command to just make it work. If that's what you're looking for then just buy a network bridge like this one.

[http://www.newegg.com/Product/Product.aspx?Item=N82E16833156307](http://www.newegg.com/Product/Product.aspx?Item=N82E16833156307)

Will I be able to use internet on the server though?

---

### Post by lukeiamyourfather on 2012-05-23
> **Hwest said:**
> Will I be able to use internet on the server though?

If configured properly, yes, either should allow the server to access the internet.

---

### Post by Hwest on 2012-05-23
> **lukeiamyourfather said:**
> If configured properly, yes, either should allow the server to access the internet.

If I just follow the guide will that work, Or do I need to make extra changes?

---

### Post by lukeiamyourfather on 2012-05-23
> **Hwest said:**
> If I just follow the guide will that work, Or do I need to make extra changes?

Follow the guide and you'll find out. :-k

---

### Post by Hwest on 2012-05-24
I am configing my PS3 with these settings but I keep getting DNS erorrs.

IP: 192.168.0.50
Subnet: 255.255.255.0
Router: 192.168.0.1
1st DNS: 122.49.191.252
2nd DNS: 122.49.191.253

I have an old router with DNS and DHCP turned off acting as a switch because I dont have a crossover cable.

Anyone know how I can fix this?

---

