---
title: "mega noob, having wireless issues. Device not ready"
date: 2011-08-06
forum: Networking &amp; Wireless
---

### Post by Akatzman2 on 2011-08-06
Hi friends,
I apologize for any dumbassery that may come out of my mouth, I don't really know what I am doing, but I need help, PLEASE!

My PC is a lenovo X60, and I have Ubuntu 10.04 on it. Everything was running just fine til two days ago when it decided to pretend the wireless was disabled. When I enabled it, I got a device not ready message. I've already done a pre-cursory search through the forums and tried a few things out to no success. Please, please help!

---

### Post by realzippy on 2011-08-06
Maybe you will get more answers when posting outputs from

```
lspci
```

and

```
iwconfig
```


```
sudo lshw -C network
```

---

### Post by Akatzman2 on 2011-08-08
HI there,
thank you for your help.
attached is pictures of the output from the first and second commands, the third command yielded no output at all. Sorry I had to attach as pictures, but as I've said, my PC won't connect to the net, even if I directly plug in right now.
Advice as to how to proceed?

---

### Post by Akatzman2 on 2011-08-08
I should add in that initially it shows my wireless default as being disabled, but when I enable it, it tells me the device is not ready. Attempting to find my wifi card via administration--> hardware drivers yields nada.

---

### Post by realzippy on 2011-08-09
Does your desktop work ?
So you could open the terminal there,no need for "screenshots",
and have a look at network manager to configure wlan
for your access point..

---

### Post by Akatzman2 on 2011-08-09
Don't have a desktop, just this laptop :(

---

### Post by realzippy on 2011-08-09
With desktop I mean your ubuntu desktop,the GUI. :D

---

### Post by TBABill on 2011-08-09
When you see the Grub screen on restart, do you have an older kernel you can boot into instead of the newest one listed? Sometimes if you receive a kernel update it will bork a piece of hardware but it can be overcome by just booting into the older working kernel.

---

