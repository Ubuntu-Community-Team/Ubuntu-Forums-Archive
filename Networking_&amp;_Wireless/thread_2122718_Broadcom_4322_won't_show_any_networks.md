---
title: "Broadcom 4322 won't show any networks"
date: 2013-03-06
forum: Networking &amp; Wireless
---

### Post by donblumps on 2013-03-06
Hey guys, just today i installed ubuntu 12.10, the problem i found was that my wifi didn't work. I googled for a while and found a few solutions but it didnt seem to work. I do know for a fact that it's BCM4322. Really need help :(

---

### Post by carl4926 on 2013-03-06
We really need to see
```
lspci -nnk | grep -iA2 net
```

---

### Post by donblumps on 2013-03-06
Here is what i got back:
[http://imageshack.us/photo/my-images/268/screenshotfrom201303060.png/](http://imageshack.us/photo/my-images/268/screenshotfrom201303060.png/)

---

### Post by carl4926 on 2013-03-06
Please try

```
sudo apt-get install broadcom-sta-common
```
You need a active wired connection

FYI also see
[http://wireless.kernel.org/en/users/Drivers/b43](http://wireless.kernel.org/en/users/Drivers/b43)

---

### Post by donblumps on 2013-03-06
I'll try this tomorrow, let you know how it goes. I did check the link you added, it shows bcm4322 as not supported...

---

### Post by carl4926 on 2013-03-06
> **donblumps said:**
> I'll try this tomorrow, let you know how it goes. I did check the link you added, it shows bcm4322 as not supported...If what I gave you installs/ is avail for youIt should work

---

### Post by donblumps on 2013-03-06
The command just comes back with: 'unable to locate package broadcom-sta-common'.

---

### Post by carl4926 on 2013-03-06
> **donblumps said:**
> The command just comes back with: 'unable to locate package broadcom-sta-common'.
It's on a OSX correct?
You may have to get the files manually

---

### Post by chili555 on 2013-03-06
> **donblumps said:**
> The command just comes back with: 'unable to locate package broadcom-sta-common'.I think what you want is:```
sudo apt-get install linux-headers-generic
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

---

