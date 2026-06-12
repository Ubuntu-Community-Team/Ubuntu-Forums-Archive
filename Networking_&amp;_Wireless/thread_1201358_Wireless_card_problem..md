---
title: "Wireless card problem."
date: 2009-07-01
forum: Networking &amp; Wireless
---

### Post by jackalpup1282 on 2009-07-01
Hi there folks! 

I think my problem is the same as many people here: i can't install my wireless card. : (

The fact is that i read a lot of stuff here, and NONE help me to install ndiswrapper to then install my wireless card driver. 

I have downloaded the ndiswrapper.deb because i think that would be easier than the tar.gz file. But when i try to install the file, it just start loading and does NOTHING. :(

Then i try to install the ndiswrapper.tar.gz version. using that code:

> cd ~/Desktop
sudo -s
apt-get install build-essential
tar -xzvf ndiswrapper*
cd ndiswrapper*
make
make install

I put the file on the desktop (ndiswrapper-1.55.tar.gz), and when i use the command "apt-get install build-essential" i got this answer "E: Couldn't find package build-essential". 

So then i try to install the build-essential(.deb) and got "Error: Dependency is not satisfiable: g++ (>= 4:4.3.1)" 

The problem is that i don't have a connection to the internet with the linux. I can get files with other computer and put there using a pendrive. 

Thank You

---

### Post by The Toxic Mite on 2009-07-01
Go to Applications > Accessories > Terminal, and type in the following code please:

```
lshw -c network
```

Post the results of that when you are done. :)

---

### Post by jackalpup1282 on 2009-07-01
*-network               
        description: Ethernet interface  
        product: RTL-8139/8139C/8139C+  
        vendor: Realtek Semiconductor Co., Ltd.  
        physical id: 0  
        bus info: pci@0000:02:00.0  
        logical name: eth0  
        version: 10  
        serial: 00:0b:cd:ec:88:40  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical  
        configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes  
   *-network  
        description: Wireless interface  
        product: ACX 111 54Mbps Wireless Interface  
        vendor: Texas Instruments  
        physical id: 0  
        bus info: pci@0000:03:00.0  
        logical name: wlan0  
        version: 00  
        serial: 00:11:95:48:bd:46  
        width: 32 bits  
        clock: 33MHz  
        capabilities: bus_master cap_list ethernet physical wireless  
        configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+  
   *-network DISABLED  
        description: Ethernet interface  
        physical id: 1  
        logical name: pan0  
        serial: 62:06:4f:3d:c5:25  
        capabilities: ethernet physical  
        configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by The Toxic Mite on 2009-07-01
> **jackalpup1282 said:**
> ```
*-network 
description: Ethernet interface 
product: RTL-8139/8139C/8139C+ 
vendor: Realtek Semiconductor Co., Ltd. 
physical id: 0 
bus info: pci@0000:02:00.0 
logical name: eth0 
version: 10 
serial: 00:0b:cd:ec:88:40 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical 
configuration: broadcast=yes driver=8139too driverversion=0.9.28 latency=64 maxlatency=64 mingnt=32 module=8139too multicast=yes 
*-network 
description: Wireless interface 
product: ACX 111 54Mbps Wireless Interface 
vendor: Texas Instruments 
physical id: 0 
bus info: pci@0000:03:00.0 
logical name: wlan0 
version: 00 
serial: 00:11:95:48:bd:46 
width: 32 bits 
clock: 33MHz 
capabilities: bus_master cap_list ethernet physical wireless 
configuration: broadcast=yes driver=acx_pci latency=64 module=acx multicast=yes wireless=IEEE 802.11b+/g+ 
*-network DISABLED 
description: Ethernet interface 
physical id: 1 
logical name: pan0 
serial: 62:06:4f:3d:c5:25 
capabilities: ethernet physical 
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes
```

 
Do a forum search with the term "texas instruments", and if you find something interesting, please do tell me about it :)

---

### Post by jackalpup1282 on 2009-07-03
Sorry, but i look at the entire forum. Try a thousand times and i still couldn't make it work. I'm installing windows again right now. 

It´s very difficult to make things work in linux. I spend about 3 days to make my wireless card work, and nothing. : (

This can be the greatest operating system of all time, but you still have to spend a LOT OF TIME just to make it work. 

Thanks for trying to help me. I will look out for a new version of Ubuntu where will be easier to make it work. I hope that next version of Ubuntu already come with ndiswrapper installed. 

Thanks for all help again.

---

### Post by Idefix82 on 2009-07-03
To install ndiwsrapper is actually very easy. You open the terminal (Applications->Accessories->Terminal) and type in
```
sudo apt-get update
sudo apt-get install ndiswrapper-utils-1.9
```

---

### Post by jackalpup1282 on 2009-07-03
How can someone install a wireless card acessing the internet if you are trying to install your wireless because you don't have a internet?

See the problem, why this is not easy?

---

### Post by Idefix82 on 2009-07-03
I'm sorry, I was assuming that you have got a wired connection.

In that case, download ndiswrapper-common.deb and ndiswrapper-utils-1.9.deb, save them on your desktop, install the common first, then the utils. That should be all the dependencies you need.

You tried to compile from source and for that you needed a C++ compiler, that's why you had so many dependencies unsatisfied.

---

### Post by jackalpup1282 on 2009-07-04
i have try this before and didn't work. : (

I try a lot of stuff. I installed it on my girlfriend computer, no great problems. Except that i tried to install the flash a milions times, and then i discovered that the problem is not the way i installed but the flash player of linux. 

I think that Linux has many cool stuff, but a lot of problems. One of then is the amount of distros. If the linux community uses the same version, i think that today it could be unquestionable better than Windows or any other OS.

Sorry, but i thinking i should tryi Ubuntu another time. I think this OS is not ready yet. 

Thanks for you help.

---

### Post by Idefix82 on 2009-07-04
> **jackalpup1282 said:**
> I think that Linux has many cool stuff, but a lot of problems. One of then is the amount of distros. If the linux community uses the same version, i think that today it could be unquestionable better than Windows or any other OS.


Of course, you are entitled to your own opinion but consider this: one of the major points in the open source philosophy is that people should have a choice. The reason for there being so many distros is that there are people who think that the distros around don't perfectly satisfy their - possibly very specific - needs, so they create a new one. That's also why there are usually several open source programs for the same task, several desktop environments, several window managers and so on. This is usually regarded as a strength and not a weakness of Linux. Besides, many people, including myself, think that Linux is already far superior to Windows.

> **jackalpup1282 said:**
> Sorry, but i thinking i should tryi Ubuntu another time. I think this OS is not ready yet. 


That's a pity but it's your decision (isn't it great that you can make one rather than being forced to use Windows because there is nothing else around). If you change your mind then come back here and people will sort you out. You haven't given us much of a chance to help you and there are very few people who didn't get their system to run with the help of the forums.

> **jackalpup1282 said:**
> 
Thanks for you help.
You are welcome.

---

