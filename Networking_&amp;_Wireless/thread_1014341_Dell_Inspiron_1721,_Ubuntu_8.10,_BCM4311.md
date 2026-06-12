---
title: "Dell Inspiron 1721, Ubuntu 8.10, BCM4311"
date: 2008-12-17
forum: Networking &amp; Wireless
---

### Post by vouser on 2008-12-17
Hello all Linux friends.
I have a Dell Inspiron 1721 notebook which I bought with VISTA pre-installed.

I have installed Ubuntu 8.10 taking all the disk available.
Now my next step is to connect to the web.
My internet connection is AT&T DSL with wireless router.

Running the following command:

$ lspci | grep Broadcom

tells me that my Network Controller is Broadcom BCM4311 802.11b/g WLAN.

Doing steps described at the following URL:

[http://ubuntuforums.org/archive/index.php/t-337758.html](http://ubuntuforums.org/archive/index.php/t-337758.html) 

did not solve the problem.

If anyone had success achieving this goal, could you please share the knowledge?
Sincerely yours,
Vladimir.
12-17-2008

---

### Post by shane8002 on 2008-12-17
The easiest way is to plug your laptop in to a wired connection and update it. Then after you update it you should be able to turn on third party drivers just by clicking enable. Also you can get third party hardware detection programs and also network manager which is what i use and it works great. All of those programs can be found in your package manager and are easy to use. Also you dont always half to wrap your driver, I have two laptops one with an atheros and one with broadcom and they work great without wrapping the drivers. But if you really want to wrap the drivers just download the three required packages and under adminastration you will see windows wireless drivers, click on it and it will ask you for the .inf file. To get that you will need to download the correct driver for your card, then just click on the .inf file and that should do the trick. I would recommend just plugging in the wired connection and update, then get all the programs you need.

---

### Post by Ayuthia on 2008-12-17
Let's try this first:
```
sudo modprobe -r ndiswrapper
```
Go into System->Administration->Hardware Drivers and activate the Broadcom STA module.  If that works, then do the following:
```
echo blacklist ndiswrapper|sudo tee -a /etc/modprobe.d/blacklist
echo wl | sudo tee -a /etc/modules
```

---

