---
title: "Intel Centrino Wireless-N 1030 problem on Ubuntu 12.04"
date: 2012-09-09
forum: Networking &amp; Wireless
---

### Post by Kraaijenzank on 2012-09-09
Hey guys,

I recently got myself a new HP Pavilion dm4-2102eo with a built-in Intel Centrino Wireless-N 1030 WiFi adapter. After messing a bit around with the partitions on the hard drive, I finally got to install the latest version of Ubuntu (12.04), now running a dualboot setup with the pre-installed Windows 7 (using GRUB).

So far everything has been running smoothly. Ubuntu quickly found drivers for almost all of my computer's hardware. That included drivers for the Wireless-N 1030 card -- or so I thought!

After having installed Ubuntu, I connected to my home WLAN (which was visible along with a range of other wireless networks in my neighborhood). I entered my WPA password and connected successfully. I opened up Firefox, typed in gmail.com, hit Enter and... Nothing happened! It kept on loading until it finally gave up and said that the connection could not be established.

I am now back on my Windows partition where the Internet works flawlessly. So does it on my iPhone, my mother's iPad and my brother's MBP. Since a lot of different devices are able to log onto our wireless network, the problem must lie within the Ubuntu installation.

I have taken screenshots of the connection settings ([see here]("http://ge.tt/2ZYvZPN/v/0")) and of the output of running the command  *ifconfig* in Terminal ([see here]("http://ge.tt/2ZYvZPN/v/1")).

I am confident with Terminal and know how to do some basic operations but I have no clue of where to start here. I have been searching for solutions online but it seems that most people have different setups and need different solutions. I hope that you guys will be able to help me out.

Thank you so much!

Best regards,
Sebastian

---

### Post by chili555 on 2012-09-09
Perhaps this will be helpful: [http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable](http://ubuntuforums.org/showthread.php?t=2042332&highlight=11n_disable)

---

### Post by Kraaijenzank on 2012-09-09
It did work! Wow, that easy!

Thanks a lot!

---

### Post by chili555 on 2012-09-09
Please use thread tools at the top to mark Solved. It will help the searchers (John Ford and John Wayne) find the solution.

Glad it's working!

---

