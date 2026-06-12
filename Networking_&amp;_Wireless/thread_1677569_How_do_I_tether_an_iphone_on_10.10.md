---
title: "How do I tether an iphone on 10.10"
date: 2011-01-28
forum: Networking &amp; Wireless
---

### Post by willz06jw on 2011-01-28
Hi and thanks for your help,

I use 10.10 and I am trying to find out how to tether a jailbroken iphone (only source of internet).  I can't seem to find anything in the Software Center...any ideas?

Thanks,
Will

---

### Post by I&#9829;HTML5 on 2011-02-01
Tethering over WiFi should work just like any other WiFi network. Tethering over Bluetooth *might* work using just native Ubuntu features... or it might not. I am not entirely sure.

---

### Post by willz06jw on 2011-02-01
I guess I should have specified: I am trying to tether ising MyWi and the iPhones USB cord.

Thanks again,
Will

---

### Post by I&#9829;HTML5 on 2011-02-02
In that case, try this (from [http://www.srw2d.com/blog/mywi-iphone-tethering-ubuntu-1004](http://www.srw2d.com/blog/mywi-iphone-tethering-ubuntu-1004))
> To get it going, make sure your iPhone is not plugged in.

Open up terminal and Add the repo:
```
sudo add-apt-repository ppa:pmcenery/ppa
```

Next, update:
```
sudo apt-get update
```

Now time to install:
```
sudo apt-get install libimobiledevice-dev libimobiledevice-utils ipheth-utils gvfs
```

After this is done, turn the app MyWi on, and plug it in. It will not seem to work if you have it plugged in, and then turn it on.

---

### Post by srw2d on 2011-02-23
> **I&#9829 said:**
> In that case, try this (from [http://www.srw2d.com/blog/mywi-iphone-tethering-ubuntu-1004](http://www.srw2d.com/blog/mywi-iphone-tethering-ubuntu-1004))

Thanks for the post of my blog, as for running usb in 10.10, I still have not found a way yet.  I keep trying about once a month to see if there is a way.  Right now, it's pretty much using wifi as far as I can find.

---Edit----
iPhone 3G should work as posted in my blog, iphone 4, still a no-go

---

### Post by legend_gibby on 2011-02-27
> **willz06jw said:**
> Hi and thanks for your help,

I use 10.10 and I am trying to find out how to tether a jailbroken iphone (only source of internet).  I can't seem to find anything in the Software Center...any ideas?

Thanks,
Will

try this........[https://help.ubuntu.com/community/PortableDevices/iPhone#iTunnel](https://help.ubuntu.com/community/PortableDevices/iPhone#iTunnel)

im tring it just now!!! so will see what happens!!!

---

### Post by thed0ctor on 2012-03-06
I've tested this on Ubuntu 11.10 x64 with an Iphone 4 (not 4S) and it's working perfectly fine on MyWi 5.0!

--keywords--
iphone 4 tether mywi 5 Ubuntu 11.1

---

