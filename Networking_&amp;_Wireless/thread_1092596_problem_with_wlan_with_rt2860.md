---
title: "problem with wlan with rt2860"
date: 2009-03-10
forum: Networking &amp; Wireless
---

### Post by gpnet on 2009-03-10
Hi to all,

I have an Akoya e1210, and as you know , has some problem with his ralink 2790 (2860) chipset.
I had an ubuntu 8.04 installed with wlan not running, so i downloaded the rigth driver from the constructor ( 2008-0918_rt2860_linux_sta_V1.8.0.0.tar.bz2 ) and installed it with command make and make install.
After that i rebooted and the wlan magically begin to work.

I recently installed the suggested update to 8.10 and all has gone well until I rebooted the system because the wlan stopped to work. I thought the update override the drive i compiled , so I recompile the drive and reboot the system.
Now the system tell me is right connected to the wlan but if i try to use to browser I got the message " Address not found".
The same story if I try to connect as wired cable.  

What is happen? can anyone help me.
I read that with the new 9.04 release the driver has been officially supported but if I can't connect I can't update.

---

### Post by gpnet on 2009-03-10
I solved the problem by myself this way:

In a terminal I execute the command ifconfig and I saw I had two connection active simultaneously :
eth1 (wired), lo (loopback) , rao (wireless)

so I typed :
sudo ifconfig eth1 down

after that the wireless connections signals begin to work and I get connected to the network.

So, It was not a drive problem, but in this case I can prevent the system active two connection at the same time.

Could anyone help me ?

---

