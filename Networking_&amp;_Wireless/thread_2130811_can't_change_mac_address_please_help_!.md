---
title: "can't change mac address please help !"
date: 2013-03-30
forum: Networking &amp; Wireless
---

### Post by Chairmansaab on 2013-03-30
Hey guys, 

I tried changing mac address by following command 
```
ifconfig br0 down hw ether Aa:bb:cc:dd:ee:ff:ee
```
whenever i type this command it stop responding 
i can't get it up via this command. 
```
ifconfig br0 up
```
please help i will appreciate !
Thanks

---

### Post by haqking on 2013-03-30
```
sudo ifconfig br0 hw ether aa:bb:cc:dd:ee:ff:ee
```

or


```
sudo ip link set br0 address aa:bb:cc:dd:ee:ff:ee
```

---

### Post by Chairmansaab on 2013-03-30
> **haqking said:**
> ```
sudo ifconfig br0 hw ether aa:bb:cc:dd:ee:ff:ee
```

or


```
sudo ip link set br0 address aa:bb:cc:dd:ee:ff:ee
```

i am using telnet on both of my GALAXYS2 (ANDROID) and my windows 7 lappy.
i can't seems to change it
I have broadcom chipset in my modem > model name BCM96338 if that matter
 here is screenie of the error
[IMG]http://i50.tinypic.com/2d1paub.png[/IMG]
and i tried second command too i am getting dev is duplicate and address is garbage :(
thanks for reply

---

