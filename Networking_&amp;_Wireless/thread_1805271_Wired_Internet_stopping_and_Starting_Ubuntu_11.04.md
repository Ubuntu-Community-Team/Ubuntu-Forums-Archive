---
title: "Wired Internet stopping and Starting Ubuntu 11.04"
date: 2011-07-15
forum: Networking &amp; Wireless
---

### Post by Rocky1980 on 2011-07-15
Hi all,


I have a bit off a strange one here, my internet stops and starts. One minute it is fine and the next it will not connect to any  web pages or even to the router then its fine again. My machine is a new build Pc were I installed 11.04 as a fresh install, everything was fine till a few days ago when this all started up. I connect to my router via a wired network, the new PC also has a second HD with windows 7 on it and that is fine with the net so I know it must be some sort off software issue but I have not idea what. 

Machine setup 
Intel 3.3GHz i5 core
4 gig RAM 
GeForce GT 220
1 TB main with ubuntu 11.04
250gb with Win7 
Blu ray writer 


Ifcofig output 

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:6d:2e:ee  

          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0

          inet6 addr: fe80::beae:c5ff:fe6d:2eee/64 Scope:Link

          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1

          RX packets:3968 errors:0 dropped:3969 overruns:0 frame:3969

          TX packets:3394 errors:0 dropped:25 overruns:0 carrier:0

          collisions:0 txqueuelen:1000 

          RX bytes:5190471 (5.1 MB)  TX bytes:380596 (380.5 KB)

          Interrupt:46 Base address:0xc000 



lo        Link encap:Local Loopback  

          inet addr:127.0.0.1  Mask:255.0.0.0

          inet6 addr: ::1/128 Scope:Host

          UP LOOPBACK RUNNING  MTU:16436  Metric:1

          RX packets:264 errors:0 dropped:0 overruns:0 frame:0

          TX packets:264 errors:0 dropped:0 overruns:0 carrier:0

          collisions:0 txqueuelen:0 

          RX bytes:23809 (23.8 KB)  TX bytes:23809 (23.8 KB)



Any help would be great 


Thanks

---

### Post by steinerd on 2011-07-15
I had a similar problem before when I was trying to configure my IPV6 LAN.  During troubleshooting I disabled IPV6 and all stabilized.  I had bugged my dns for IPV6 so unless I had the hosts cached at the time they could not be reached.  Just a suggestion to try and disable or ignore IPV6 and run straight IPV4 to see if that straightens it out.  at least then you will know what protocol is causing the issue.

also make sure your hardware is not set for some type of auto-sleep or wake-on-lan setting.  I have had problems with these before also.  I just enable them one at a time to see which is causing my stress.

I hope these tips get you going on the right track.  Sorry that they are not out and out answers.  BTW my IPV6 problem was rooted in my router, once I had it set correctly my problems went away.

Eliminate all it could be and all that is left is what it is, no matter how unlikely lol.

---

### Post by Rocky1980 on 2011-07-15
Thanks for the ideas, not only after I posted a tried disabling IPv6 using this great link

[http://www.upubuntu.com/2011/05/how-to-disable-ipv6-under-ubuntu.html](http://www.upubuntu.com/2011/05/how-to-disable-ipv6-under-ubuntu.html) 

but that has had no effect at all. Also when I run a speed test at speedtest.net on ubuntu I am now only getting 1.14mbs but if I reboot into win7 and do the same thing its more like 4.75mbs !!

---

### Post by varunendra on 2011-07-16
Apart from IPv6, this problem also occurs due to buggy drivers. To see the model of your network adapters and which drivers they are using, please post the outputs of:
```
sudo lshw -C network
```To make sure IPv6 is disabled, re-check output of ifconfig command, there should be no "inet6...." line in the output this time.


**EDIT:**
Also try setting MTU value to 1492.

---

### Post by Rocky1980 on 2011-07-16
Output from sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:04:00.0
       logical name: eth0
       version: 06
       serial: bc:ae:c5:6d:2e:ee
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full ip=192.168.1.2 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:46 ioport:d000(size=256) memory:d2104000-d2104fff memory:d2100000-d2103fff



New output from ifconfig after ivp6 disable

eth0      Link encap:Ethernet  HWaddr bc:ae:c5:6d:2e:ee  
          inet addr:192.168.1.2  Bcast:192.168.1.255  Mask:255.255.255.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3037568 errors:0 dropped:3037568 overruns:0 frame:3037568
          TX packets:2999878 errors:0 dropped:1738 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2542279303 (2.5 GB)  TX bytes:880239676 (880.2 MB)
          Interrupt:46 Base address:0xc000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1047 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1047 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66344 (66.3 KB)  TX bytes:66344 (66.3 KB)
EDIT

How do I set the MTU value to 1492. ??

I used sudo ifconfig eth0 mtu 1492 and it had no effect :(


Many thanks again

---

### Post by varunendra on 2011-07-16
> **Rocky1980 said:**
> Output from sudo lshw -C network

 *-network               
       description: Ethernet interface
       product: **RTL8111/8168B** PCI Express Gigabit Ethernet controller
....
....
       configuration: autonegotiation=on broadcast=yes **driver=r8169** driverversion=2.3LK-NAPI ....
....
Looks like you don't need to bother about the MTU value at all! :)

You are one of the many suffering with this same hardware-driver combination.
> Many motherboards nowadays have integrated gigabit ethernet that use the Realtek NIC chipset.
 The Realtek r8168B network card does not work out of the box in  Redhat, Centos, Fedora, or Ubuntu: instead of loading the r8168 driver,  modprobe loads the r8169 driver, which is broken as can be seen with  ifconfig which shows large amounts of dropped packets.
 One solution found by Barry Mavin is to remove the r8169 driver and install the latest r8168 driver.
(source: [http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora](http://www.foxhop.net/realtek-dropping-packets-on-linux-ubuntu-and-fedora))

Just follow these steps:

[LIST]
[*]Download r8168B driver:
[/LIST]
```
wget http://www.foxhop.net/attachment/r8168-8.023.00.tar.bz2
tar vjxf r8168-8.023.00.tar.bz2
```
[LIST]
[*] Remove r8169 driver:
[/LIST]
```
sudo rmmod r8169
```
[LIST]
[*]Now install the downloaded r8168B driver:
[/LIST]
```
cd r8168-8.023.00
sudo ./autorun.sh
```
[LIST]
[*]load the r8168 driver:
[/LIST]
```
sudo modprobe r8168
```
[LIST]
[*]Blacklist the r8169 driver to prevent it from loading again. You can do so easily by becoming 'root' for next step (Be cautious! Do not to perform unnecessary commands when in root mode):
[/LIST]
```
sudo su
echo "blacklist r8169" >> /etc/modprobe.d/blacklist.conf
exit
```
[LIST]
[*]Now verify that the r8168B driver has been loaded and is in use now:
[/LIST]
```
lsmod | grep r8168
```(it should return one line as output)

And, just for your info, you can change MTU value in network manager settings. I don't know where it is placed in natty (I haven't used it yet), but in earlier versions, it is found at the right corner of the upper panel. But as I already said, you don't need to mess with it now.



**_EDIT 1_:**
Please also see post #10 by rarsa below. He has put some updated info on this issue, especially regarding kernel 3 onwards.

**_EDIT 2_:** The latest driver can be downloaded from [here]("http://www.realtek.com.tw/downloads/downloadsView.aspx?Langid=1&PNid=5&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#RTL8111B/RTL8168B/RTL8111/RTL8168%3Cbr%3ERTL8111C/RTL8111CP/RTL8111D%28L%29%3Cbr%3ERTL8168C/RTL8111DP/RTL8111E%3Cbr%3ERTL8105E"). Accordingly, the 'cd <..>' command will change as per the name of the directory created.

**_EDIT 3_:** A much more detailed approach to the same solution is given here (thanks to zxkelxz): [http://ubuntuforums.org/showthread.php?t=1661489](http://ubuntuforums.org/showthread.php?t=1661489)

---

### Post by Rocky1980 on 2011-07-16
SORTED, many many thanks to everyone it looks like it was the driver issue everything works great now 

Thanks again

---

### Post by u-slayer on 2011-08-16
> **varunendra said:**
> 

Just follow these steps:


My server had been working fine for months until it started randomly dropping off the network yesterday. Thanks for the guide! This fixed my problem.

---

### Post by varunendra on 2011-08-16
> **u-slayer said:**
> My server had been working fine for months until it started randomly dropping off the network yesterday. Thanks for the guide! This fixed my problem.
You're welcome! Wasn't my original effort by the way, I just got lucky to find the guide. :)

Good to know that it is proving to be a definite solution for the problem, too bad it still seems unfixed in original releases/updates. Hope it gets fixed soon.



**EDIT:**
At least one user has reported that r8168 wasn't loading automatically even after blacklisting r8169. In that case, "r8168" can be added to /etc/modules file as an entry to tell the kernel to load it everytime it boots. ([see here]("http://ubuntuforums.org/showthread.php?p=11149879&postcount=6"))

---

### Post by rarsa on 2011-09-05
Thank you for these instructions.

I will just point the following:
- It is advisable to download the latest version directly from the realtek site
- With Kernel 3.0 there are some aditional steps due to a bug on the Makefile

I refreshed the instructions here:
[http://forums.linuxmint.com/viewtopic.php?f=49&t=80757#p469071](http://forums.linuxmint.com/viewtopic.php?f=49&t=80757#p469071)

Thank you again for your post. It set me in the right direction!

---

### Post by gefalu2008 on 2011-10-14
Thank You, Varunendra! These tips helped me to solve a difficult situation.

---

### Post by varunendra on 2011-10-14
> **gefalu2008 said:**
> Thank You, Varunendra! These tips helped me to solve a difficult situation.
You're welcome, and thanks for the confirmation. It's good to get more and more of them as it is getting too common with newer kernel. Hope it helps others too.

---

