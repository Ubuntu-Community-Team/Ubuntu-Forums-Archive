---
title: "How to install iwlagn module??"
date: 2012-06-27
forum: Networking &amp; Wireless
---

### Post by fkubt on 2012-06-27
Hi,

I'm new to ubuntu.

Now, i installed 10.10 on the Lenovo T420s which is equipped with Intel Centrino N6205 Wifi adaptor.

But there are no iwlagn module installed, so it is impossible to enable the wifi network.

With a command (sudo lshw -C network), the result was UNCLAIMED.

I need helpful comments from you.....

Thanks,

---

### Post by wildmanne39 on 2012-06-27
Hi, 10.10 is unsupported so I recommend 12.04 because you will not be able to get any update's for 10.10 soon if they have not already been removed from the server.
Thanks

---

### Post by chili555 on 2012-06-27
The driver is already installed in 10.10 but its aliases don't include your relatively newer device. You might install the compat-wireless suite as outlined here: [http://ubuntuforums.org/showthread.php?t=2003669&page=3&highlight=compat](http://ubuntuforums.org/showthread.php?t=2003669&page=3&highlight=compat)

Be sure, before you start that you do:```
sudo apt-get install build-essential linux-headers-generic
```Please post back if you get stuck.

---

### Post by fkubt on 2012-06-28
> **chili555 said:**
> The driver is already installed in 10.10 but its aliases don't include your relatively newer device. You might install the compat-wireless suite as outlined here: [http://ubuntuforums.org/showthread.php?t=2003669&page=3&highlight=compat](http://ubuntuforums.org/showthread.php?t=2003669&page=3&highlight=compat)

Be sure, before you start that you do:```
sudo apt-get install build-essential linux-headers-generic
```Please post back if you get stuck.


Thanks for reply.

Anyway, due to the time requirement, i tried to install 11.04 and fortunately it enables the wireless access automatically.

One of my colleague still uses the 10.10.

I will try your support with his laptop.

Thanks you for all of you.

P.s. It looks like "apt-get" is very important utility for managing Ubuntu. Is there any tutorial or trial manuals about how to use it??

---

### Post by chili555 on 2012-06-28
> It looks like "apt-get" is very important utility for managing Ubuntu. Is there any tutorial or trial manuals about how to use it??Please check here: [https://help.ubuntu.com/community/AptGet/Howto/](https://help.ubuntu.com/community/AptGet/Howto/)

---

