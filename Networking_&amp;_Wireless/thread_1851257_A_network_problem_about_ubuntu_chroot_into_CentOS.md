---
title: "A network problem about ubuntu chroot into CentOS"
date: 2011-09-27
forum: Networking &amp; Wireless
---

### Post by samtai on 2011-09-27
I have create a qemu image and installed CentOS in this img,
then I mount the img in /mnt/centos/ ,and chroot into CentOS successfully.
All the command work fine in CentOS, but I can not ping google.com, so I type "ifconfig", it display like the following:
```
# ifconfig
Warning: cannot open /proc/net/dev (No such file or directory). Limited output.
Warning: cannot open /proc/net/dev (No such file or directory). Limited output.
eth1      Link encap:Ethernet  HWaddr 6C:F0:49:E9:0E:65  
          inet addr:192.168.11.4  Bcast:192.168.11.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:45 Base address:0xe000 

Warning: cannot open /proc/net/dev (No such file or directory). Limited output.
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
```

I cd to /proc , it is empty. Am I mount the root file system incorrect?

Anyone know how to config the chroot network and solve this problem?

---

### Post by samtai on 2011-09-28
I have find a easy way to solve my problem,
I just need to mount my Ubuntu's /proc to the chroot directory.
```
sudo mount --bind /proc /mnt/centos/proc
```
But the network still not working, I need to do one more thing, when chroot into CentOS, type:
```
dhclient eth1
```
Then, I can ping google.com and use the yum command.

For more information, go to [http://geek.co.il/wp/2010/03/14/how-to-build-a-chroot-jail-environment-for-centos](http://geek.co.il/wp/2010/03/14/how-to-build-a-chroot-jail-environment-for-centos)
I found the solution on this website.

---

