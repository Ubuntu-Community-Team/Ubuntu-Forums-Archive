---
title: "Ralink Device 539b - Can't connect to wireless"
date: 2012-11-11
forum: Networking &amp; Wireless
---

### Post by davewhelchel on 2012-11-11
I just installed ubuntu 12.04 on a new computer and now I can't connect to my wireless network. I can connect with a wired connection and on my laptop with a wireless connection so I know my internet is working. I have a ralink 539b controller. I have tried to install the driver for this controller by following some of the other threads but haven't been able to get it to work. Can someone please help?

david@Desktop:~$ lspci | grep Network
04:00.0 Network controller: Ralink corp. Device 539b
david@Desktop:~$ iwconfig
lo        no wireless extensions.
eth0      no wireless extensions.

---

### Post by ahallubuntu on 2012-11-11
Can you explain exactly what you have tried in as far as installing another driver and where it failed?  The more specific you can be, the better.

---

### Post by davewhelchel on 2012-11-11
Here's what I did.

downloaded 3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz
ran the following commands:

sudo apt-get install --reinstall linux-headers-$(uname -r) build-essential dkms
sudo tar xvf 3473742-Ralink_5390sta-2.5.0.3_dkms.tar.gz -C /usr/src
sudo dkms add -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3
sudo modprobe -v rt5390sta
uname -a
iwconfig
sudo iwlist scan
sudo depmod -a
sudo update-initramfs -u

---

### Post by davewhelchel on 2012-11-11
Not sure where it failed, it just didn't help me connect. I'm not sure what to look for...

---

### Post by ahallubuntu on 2012-11-11
I found some instructions very similar to what you posted, here:

[http://forumubuntusoftware.info/viewtopic.php?f=72&t=8459](http://forumubuntusoftware.info/viewtopic.php?f=72&t=8459)

but that thread includes an extra step you left out (or you left it out of the posting here):

```
sudo dkms build -m Ralink_5390sta -v 2.5.0.3
```

after the "add" and before the "install."  Can you confirm you did the build step too?  If not, go back and do that now, then re-do everything after that.

---

### Post by davewhelchel on 2012-11-11
Nope, I missed that line. I entered the line that I missed plus the others as shown below. Still no luck.

sudo dkms build -m Ralink_5390sta -v 2.5.0.3
sudo dkms install -m Ralink_5390sta -v 2.5.0.3
sudo modprobe -v rt5390sta
uname -a
iwconfig
sudo iwlist scan
sudo depmod -a
sudo update-initramfs -u

---

### Post by mabelzunce on 2012-12-26
Hi
I am having the same issue with 539b. In ubuntu 12.10 works fine with the rt2800pci that is built-in in the kernel. I had to downgrade to 12.04 because in ubuntu 12.10 my filesystem goes read-only all the time. So now I am without wireless again.
Could you solve it?

---

### Post by mcwescott on 2012-12-27
use one of the wireless backport metapackages

I used 

    linux-backports-modules-cw-3.6-precise-generic

to good effect on my HP laptop with Network controller: Ralink corp. Device 539b.

---

