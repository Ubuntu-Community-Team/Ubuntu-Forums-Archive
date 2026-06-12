---
title: "Wireless not working after installation of unrelated packages"
date: 2011-08-03
forum: Networking &amp; Wireless
---

### Post by pbasil on 2011-08-03
Hi guys,

I recently installed 10.04 from CD and everything was working perfectly.
Yesterday I followed the instructions on a website to install some packages in order to manage my iPhone more effectively from Ubuntu. 
Unfortunately this caused a lot of problems, mainly with the graphics (a nightmare I finally was able to solve).

However now I am not able to connect via wireless to my network.
It connects and I get the IP but I can not browse and I am forced to turn to wired network :(

I wonder whether there is a way to reinstall all original wireless related package so I can go back to previous configuration.

Hoping for a solution, thanks in advance,
Peter

---

### Post by pbasil on 2011-08-04
There is really no way to reinstall all network related packages again from scratch :(

---

### Post by lkjoel on 2011-08-05
Could you give me the output of these Terminal commands:
```
ifconfig
uname -a
lsb_release -a
iwconfig
lsmod
nm-tool
sudo /etc/init.d/networking restart

```

---

### Post by pbasil on 2011-08-06
> **lkjoel said:**
> Could you give me the output of these Terminal commands:
```
ifconfig
uname -a
lsb_release -a
iwconfig
lsmod
nm-tool
sudo /etc/init.d/networking restart

```

I already reinstalled Ubuntu. However I have found that it is possible to reinstall from the Live CD and keep my /home data intact.
This solved the problem whatever it was as I format and install the root directory from scratch. Thanks anyway.

---

### Post by pbasil on 2011-08-06
Although that might not be the most elegant solution, this is what I did to solve the issue out of desperation:

My disk's partition is as follows:

/dev/sda1 Boot partition
/dev/sda2 Swap partition
/dev/sda3 File system partition mounted at /
/dev/sda4 File system partition mounted at /home

I insert the Live CD and proceed to reinstall. When asked for the partition I decided to define the partitions manually. 
Once there you see the partition definition of your current system.

Select only the mount points as before and DO NOT CHECK THE FORMAT option for your /home directory.
All the data in /home will be available after installation.

Obviously, software installed by you after previous installation will be removed. But you can proceed to install them by hand yourself.

That was my approach to fix the tricky network-manager issue. 
However I knew it would work because it was working perfectly after a clean install of 10.04.

Best regards,
Peter

---

