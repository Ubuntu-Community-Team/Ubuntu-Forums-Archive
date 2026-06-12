---
title: "Slow internet/speedtest/Teamviewer 12.04"
date: 2012-05-09
forum: Networking &amp; Wireless
---

### Post by TheUnaligned on 2012-05-09
Greetings,
 
I have been having very slow internet connections with my (mostly) headless Ubuntu HTPC. I use Teamviewer to manage it, as well as my Mac Mini, from a Windows 7 laptop. I have so far been unable to determine why it is so slow on the Ubunutu PC.
 
Also, results from speedtest.net wildly fluctuate (seemingly only) on the Ubuntu PC, but for the most part they are slower than the MM or the notebook - around 6-7 Mbps where the laptop and MM get 11-14 Mbps.
 
Here is my network setup:
12 or 15 Mbps cable internet 
Linksys WRT54G2 router
Dell Optiplex 745 running Ubuntu 12.04 - Broadcom 5754 (wired into router)
Mac Mini (wireless)
HP DV6TQE running W7 Professional (wireless)
 
- If I use the Ubuntu PC or the DV6 to remote control the MM, the speed is fine and I can easily control the MM.
- If I use the DV6 or the MM to remote control the Ubuntu PC, the speed is VERY slow, and takes a few seconds for commands to register. It makes managing the server very troublesome.
- The server is running a Samba file share and Subsonic for media streaming, but I when I experience the slowness I am not moving files around on the network or streaming media. 
- File transfers across computers is much slower than it was when the server was running Windows Server 08 R2. They were around 3Mb/s then, compared to about 1.7Mb/s now. Media streaming seems fine, but it doesn't require more than about 100Kb/s for music.
 
Here are some network diagnostics from Ubuntu that I found here:
[http://ubuntuforums.org/showthread.php?t=1928025](http://ubuntuforums.org/showthread.php?t=1928025)
 
ifconfig -a
eth0 Link encap:Ethernet HWaddr 00:1a:a0:bf:e0:b5
inet addr:192.168.1.200 Bcast:192.168.1.255 Mask:255.255.255.0
inet6 addr: fe80::21a:a0ff:febf:e0b5/64 Scope:Link
UP BROADCAST RUNNING MULTICAST MTU:1500 Metric:1
RX packets:12623366 errors:0 dropped:0 overruns:0 frame:0
TX packets:7506165 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:1000
RX bytes:18085406851 (18.0 GB) TX bytes:2141581271 (2.1 GB)
Interrupt:16
 
lo Link encap:Local Loopback
inet addr:127.0.0.1 Mask:255.0.0.0
inet6 addr: ::1/128 Scope:Host
UP LOOPBACK RUNNING MTU:16436 Metric:1
RX packets:105620 errors:0 dropped:0 overruns:0 frame:0
TX packets:105620 errors:0 dropped:0 overruns:0 carrier:0
collisions:0 txqueuelen:0
RX bytes:21412817 (21.4 MB) TX bytes:21412817 (21.4 MB)
----------------------------------------------------
 
cat /etc/network/interfaces
auto lo
iface lo inet loopback
----------------------------------------------------
 
uname -a
Linux <COMPUTER-NAME> 3.2.0-24-generic-pae #37-Ubuntu SMP Wed Apr 25 10:47:59 UTC 2012 i686 i686 i386 GNU/Linux
----------------------------------------------------
 
cat /etc/resolv.conf
nameserver 127.0.0.1
----------------------------------------------------
 
sudo lshw -C network
[sudo] password for <USER>:
*-network
description: Ethernet interface
product: NetXtreme BCM5754 Gigabit Ethernet PCI Express
vendor: Broadcom Corporation
physical id: 0
bus info: pci@0000:03:00.0
logical name: eth0
version: 02
serial: 00:1a:a0:bf:e0:b5
size: 100Mbit/s
capacity: 1Gbit/s
width: 64 bits
clock: 33MHz
capabilities: pm vpd msi pciexpress bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.121 duplex=full firmware=5754-v3.15 ip=192.168.1.200 latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
resources: irq:45 memory:fe7f0000-fe7fffff
----------------------------------------------------
 
Does anyone have any ideas? Any help would be great. Thanks.

---

### Post by TheUnaligned on 2012-05-10
Are there any more diagnostics I can run to try to figure out more about what's going on? Any general troubleshooting?

---

### Post by dry crust on 2012-05-14
Don't forget that what is happening in your neighbourhood also affects the speed of your connection. For example, every morning around 7.30 am all the local school kids leap out of bed and jump onto the internet and my broadband slows to a pathetic crawl, then once they go off to school it gets back to its normal racy speed.

---

### Post by TheUnaligned on 2012-05-14
> **dry crust said:**
> Don't forget that what is happening in your neighbourhood also affects the speed of your connection. For example, every morning around 7.30 am all the local school kids leap out of bed and jump onto the internet and my broadband slows to a pathetic crawl, then once they go off to school it gets back to its normal racy speed.

Good idea, but it is constant, as in* always* slow. And none of my other PCs have issues with speed - they are all significantly faster. Nor does that explain why it would be slow to use Teamviewer on that PC from within the network. No, I rather think it's something with the server itself.

---

### Post by dry crust on 2012-05-15
Have you checked to see how busy the CPU (inside System Monitor) is and what it spends most of its time doing? 
Start the System Monitor (I use Gnome-Classic as my desktop so it is found at Applications - System Tools), then select the "Resources" tab. This will bring up several graphs, one being the speed of your network, another being the business of the CPU, and the third being the use of memory. 
Starting with the easy one, the memory, check the amount of Swap memory and real memory. The general consensus seems to be to use as little swap as you can, especially if you have ample amounts of real memory spare. With Ubuntu you can change the priority given to swap memory, so if your computer is using lots of swap unnecessarily, then that could be slowing your computer down unnecessarily. By changing the priority given to swap memory the CPU will then only move stuff to the HDD if it has to. You will need to use Google to find out how to do this, but it isn't hard. It requires adding a line of text to a file. 
Next, look at the CPU. My guess is this is pretty busy, which will mean we will have to find out what is causing this using the Processes tab. 
If we look at the Network graph that will tell you what's going in and out. 
Going to the Processes tab, click on the CPU% heading of the table, then do this again. The first time you do this it puts the most idle items at the top of the table and the busiest ones at the bottom, then when you click again it will put the busiest items (the ones you are interest in) at the top of the table and the most idle at the bottom.
Lastly, just take a quick look at the File System tab and check your Hard drives have plenty of spare space on them.

---

### Post by dry crust on 2012-05-15
With regards to the use of the swap file for virtual memory, the priority that Ubuntu gives to this is called "Swappiness". As I said above, you can change the amount of swappiness in Ubuntu (and probably in most Linux distributions). Ubuntu comes with a default setting of 60. If you increased it to 100 then Ubuntu would use lots of Swap file and very little real RAM, alternatively, if you reduced swappiness to 0, then Ubuntu would wait until all the RAM was used before the swap file was utilised. Most of the instructions telling you how to change the swappiness rating suggest using a swappiness of around 10. 
Here is one website that tells you how to change the swappiness, but there are plenty of others:
[http://ubuntuguide.net/optimize-the-usage-of-swap-to-speed-up-response-for-ubuntu](http://ubuntuguide.net/optimize-the-usage-of-swap-to-speed-up-response-for-ubuntu)
One thing to note is you can do the change temporarily, which may be of interest to you. For example, you could do a broadband speed test on the Ubuntu computer, then change the swappiness temporarily, wait a few minutes to allow the computer to get used to the new setting, then do another broadband speed test to see if there is a difference.
One factor which I guess is obvious to you, but may have accidentally overlooked, is the HP computer is a 64 bit one, while the Dell is a 32 bit one. This means, amongst other things, that the HP can move data around at twice the rate of the Dell (assuming the data bus speeds are the same). Also, Hard Drives have improved over the last 5 years, so one would expect the write times of the Dell to be slower than for the other two computers. 
Again, the swappiness of the Dell comes into play because if the Dell is storing data in virtual RAM (i.e writing it onto the swap file), then trying to move it onto the HDD for permanent storage (i.e. reading from the swap file and placing into RAM, then reading from the RAM and writing that data to your dowload folder), that is quadruple handling of the data, which will definitely slow you down. 
One thing I don't see in the information you have provided is the amount of RAM on the computer. If you have some spare memory of the right sort, maybe you could install it in the Dell and then do another speed check.

---

### Post by TheUnaligned on 2012-05-16
> **dry crust said:**
> Have you checked to see how busy the CPU (inside System Monitor) is and what it spends most of its time doing?  

I guess I should have said that the PC is not completely headless. It is also a HTPC connected to my TV, but for obvious reasons I only use it that way if I'm watching a movie on it. However, when I do so I have no issues with the actual performance of the PC. The slowness seems to be network-related. I'll continue on, however, just to cover my bases.

> **dry crust said:**
> 
Starting with the easy one, the memory, check the amount of Swap memory and real memory. The general consensus seems to be to use as little swap as you can, especially if you have ample amounts of real memory spare.


I have a 4GB swap space and 4GB of physical memory on the PC. Again, I do not have performance issues if I use the PC with my TV as a monitor.

> **dry crust said:**
> 
Next, look at the CPU. My guess is this is pretty busy, which will mean we will have to find out what is causing this using the Processes tab. 


There is something anomalous here because the two cores of the CPU seem to fluctuate with what I would consider to be above-normal usage when the PC is sitting idle, but it doesn't show up in the processes tab that anything is taking as much CPU as is indicated by the graph (the system monitor is using the most, at 3%). Also, as noted, there seems to be no noticeable performance issues if I use the CPU with the TV as the monitor. The

> **dry crust said:**
> 
If we look at the Network graph that will tell you what's going in and out. 


Not much seems to be going in or out in terms of the network connections. In the time that I looked at it, it spiked at 80Kb/s, but most of the time it was well below half of that. There seems to be nothing going extraordinary happening here.

> **dry crust said:**
> 
Going to the Processes tab, click on the CPU% heading of the table, then do this again. The first time you do this it puts the most idle items at the top of the table and the busiest ones at the bottom, then when you click again it will put the busiest items (the ones you are interest in) at the top of the table and the most idle at the bottom.


Again, there seems to be nothing taking a large percentage of the CPU in this menu.

> **dry crust said:**
> 
Lastly, just take a quick look at the File System tab and check your Hard drives have plenty of spare space on them.


I have 46GB of 60GB free on the boot partition, and 291GB of 533GB free on my data partition. The disk is a newer replacement (2ish years old) than the PC had orignally, and is a 7200 RPM Western Digital OEM HDD. The HDD on the DV6 is 5400 RPM. I would expect the Dell to be faster. And as I noted before, I had Windows Server 2008 R2 on this Dell at one point with the exact same hardware and had none of these issues. It was also a Hackintosh before I put Ubuntu on it. Again - no performance issues.

---

### Post by dry crust on 2012-05-16
Well, I am afraid I'm almost at my limit. Here are a number of thoughts:
1) Did you check the "swappiness" setting? As I said before, the default setting is 60 (I just checked on my computer). This has been the default setting since I started using Ubuntu. What this means is that even though you have a huge amount of RAM the OS will start to use the swap drive for buffering the downloaded data even though that is unnecessary. By lowering the swappiness setting, Ubuntu will keep the buffered data in RAM until it is ready to write it to the HDD. 
Here is a website which tells you how to check the swappiness and to change it:
[http://www.ubuntuvibes.com/2010/08/ubuntu-why-my-netbook-is-so-damn-slow.html](http://www.ubuntuvibes.com/2010/08/ubuntu-why-my-netbook-is-so-damn-slow.html)


2) Check the System Monitor while downloading a file to see if anything stands out as not being right, e.g. how much swap drive is used when a file is being downloaded. 

3) Is it possible to use the new HDD as the main drive and use the old one as a slave drive / secondary drive? This new one is a much faster drive, so ideally reading and writing to it should also be faster. Remember to be careful and gentle if physically handling the drives so as to not create damaged sectors. Use the old drive for things that aren't essential or where you can tolerate the slower read - write times. 

My apologies in advance for not being of more assistance.

---

