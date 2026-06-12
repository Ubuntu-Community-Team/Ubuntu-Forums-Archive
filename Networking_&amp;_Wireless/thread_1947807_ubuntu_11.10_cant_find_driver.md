---
title: "ubuntu 11.10 cant find driver"
date: 2012-03-27
forum: Networking &amp; Wireless
---

### Post by oldkatz on 2012-03-27
new install of ubuntu 11.10, wifi has no driver.
i downloaded the driver, but the scan will not pick it up. 
is there a special directory for the network scan to find the driver. its ralink rt 3090 built in new lenovo.

---

### Post by 2F4U on 2012-03-27
This seems to be an interesting thread:

[http://ubuntuforums.org/showthread.php?t=1849602](http://ubuntuforums.org/showthread.php?t=1849602)

And here is the driver mentioned in the post:

[https://launchpad.net/~markus-tisoft/+archive/rt3090]("https://launchpad.net/%7Emarkus-tisoft/+archive/rt3090")

---

### Post by Bucky Ball on 2012-03-27
Have you plugged in an ether net cable, gotten online, got updates and checked 'Additional Drivers' (or 'Hardware Drivers' depending on release)?

Please post the result of this:

```
sudo lshw -C network
```

Thanks.

What driver did you install???

---

### Post by moteprime on 2012-04-09
Hi.
As 2F4U mentions the thread has some solutions, the one i posted in post #20, and the one in post #71 -They both work in 11.10
I have had both of then working in 12.04 but for some unknown reason the easy one in #20 did not work after i upgraded til 12.04 for good. I get the bug [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/896582)
So now i use the solutin #20, it works fine.

---

