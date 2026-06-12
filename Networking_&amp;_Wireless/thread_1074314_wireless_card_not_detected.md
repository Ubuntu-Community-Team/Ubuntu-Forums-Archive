---
title: "wireless card not detected"
date: 2009-02-19
forum: Networking &amp; Wireless
---

### Post by jepperstone on 2009-02-19
Hi everyone!

I purchased a Dell XPS M1530 and upgraded to Ubuntu 8.10. Initially, it didn't come with a wireless card but I put one in two days ago. I am only able to use wired internet (eth0). I typed ifconfig in the terminal and it returned:
> eth0      Link encap:Ethernet  HWaddr 00:23:ae:0f:12:bc  
          inet addr:192.168.1.108  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::223:aeff:fe0f:12bc/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:59372 errors:0 dropped:0 overruns:0 frame:0
          TX packets:40047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:73673822 (73.6 MB)  TX bytes:5316881 (5.3 MB)
          Interrupt:16 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:88 errors:0 dropped:0 overruns:0 frame:0
          TX packets:88 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4400 (4.4 KB)  TX bytes:4400 (4.4 KB)



iwlist scan returns the following:
> 
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

pan0      Interface doesn't support scanning.


The wireless card I'm using is Dell 1505 Wireless-N Mini Card.

---

### Post by Crafty Kisses on 2009-02-19
Hey there my friend! Let's see if we can't get that wireless card up and running with ndiswrapper, first thing is first you should probably install ndiswrapper, so if you don't already have it installed, you can install ndiswrapper by running the following:
```
sudo apt-get install ndiswrapper-common
``` 
Now that you got ndiswrapper installed you need to get the driver, which you can grab right [here.]("http://support.dell.com/support/downloads/download.aspx?c=us&l=en&s=gen&releaseid=R151519&formatcnt=1&libid=5&fileid=202138") Once you have downloaded the driver, look for the .inf file, once you have located the .inf file, run the following:
```
sudo ndiswrapper -i R151519.inf
```
That will install the driver, so now what you want to do is see if the driver is installed correctly, you can run the following to make sure:
```
ndiswrapper -l
```
If the driver is present and installed correctly, you should get something similar to this:
```
Installed ndis drivers
driver present, hardware present
```
You're not quite done yet though, you want to add the ndiswrapper module, so run the following command:
```
sudo modprobe ndiswrapper
```
Once you have done that, the module is there but you want to make sure the module starts at every boot, so run the following:
```
sudo ndiswrapper -m
```
Once you have done that, reboot from the Terminal by running the following:
```
sudo shutdown -r now
```
Then you should be set and your wireless card should work.

---

### Post by jepperstone on 2009-02-19
Thanks so much for your support!


posting using wireless (finally),
Jepp

---

### Post by Crafty Kisses on 2009-02-19
I'm really glad I could help! Enjoy your wireless. ;)

---

