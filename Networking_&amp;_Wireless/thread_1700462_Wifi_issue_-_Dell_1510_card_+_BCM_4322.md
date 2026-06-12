---
title: "Wifi issue - Dell 1510 card + BCM 4322"
date: 2011-03-05
forum: Networking &amp; Wireless
---

### Post by luckiestryke on 2011-03-05
Hey all. This is my first thread and I'm a total newbie to Ubuntu (and Linux) so please bear with me. 
I have a Dell Studio XPS 13 with a Dell 1510n which is based on Broadcom 4322 I believe? I am running 64bit Ubuntu 10.10 from my internal hard drive which also has Windows 7 (hopefully not for too long). Wireless works fine on Windows. Ethernet works on both which is what I'm using right now. Ubuntu doesn't even detect a wireless connection or card... it just shows empty bars with an annoying exclamation mark. before this, I did download Linux STA driver from Broadcom, but I'm not sure if I actually installed it. Also when I opened Additional Drivers, Linux STA driver showed up and I installed it although it says activated but not in use. I've also used Update Manager and everything seems to be up to date. Before writing this, I went through other forums so I ran (sudo lshw -C network) which will hopefully help you help me. 

 *-network               
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:26:b9:1a:fe:0f
       size: 100MB/s
       capacity: 1GB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.64 duplex=full ip=192.168.1.113 latency=0 link=yes maxlatency=20 mingnt=1 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:f0888000-f0888fff ioport:30d0(size=8) memory:f0889c00-f0889cff memory:f0889800-f088980f
  *-network UNCLAIMED
       description: Network controller
       product: BCM4322 802.11a/b/g/n Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0400000-f0403fff

I'm a totally new to all this so if you can reply in idiot-proof, it would be great. Thanks in advance for your help... I really do want to get out of Windows. If there is anything else you need to know, please let me know. Appreciate it.

---

### Post by luckiestryke on 2011-03-07
hello..?

---

### Post by bkratz on 2011-03-07
> **luckiestryke said:**
> hello..?



Please see this thread--look familiar?

[http://ubuntuforums.org/showthread.php?t=1701070](http://ubuntuforums.org/showthread.php?t=1701070)

---

### Post by luckiestryke on 2011-03-09
@bkratz It worked perfect, although it feels like the internet is slow (signal is full) but I'll try it out for a while and then get back. Hopefully it's an issue from the service provider. 

Thanks a lot!

---

### Post by bkratz on 2011-03-09
> **luckiestryke said:**
> @bkratz It worked perfect, although it feels like the internet is slow (signal is full) but I'll try it out for a while and then get back. Hopefully it's an issue from the service provider. 

Thanks a lot!



Sure am glad to hear that you at least got it running. Let us know the results of your testing, but in the meantime please go to the thread tools and select [mark as solved} just in case it helps someone else (makes it easier to find).

---

### Post by luckiestryke on 2011-03-09
> **bkratz said:**
> Sure am glad to hear that you at least got it running. Let us know the results of your testing, but in the meantime please go to the thread tools and select [mark as solved} just in case it helps someone else (makes it easier to find).

Yep, it's running. It seems that there was a problem, but it seems to have fixed itself (I hope!). Will look further into it if the problem continues. 
Also, I will mark this thread as solved. I didn't think of it. 

Thanks for yer help!

---

### Post by pratikkhemka on 2011-04-17
Hello, I am using Dell XPS Studio 13. I have installed Ubuntu 10.10 on Virtual machine and I have the same problem. I do not think it is a problem of the virtual machine. The ifconfig command shows only 2 interfaces : eth0 and lo. Also I made the change to /etc/modules file as said in this forum and it showed only lp so I added wl as well but it still does not detect any wireless interface.
Dell Wireless -1510 Wireless-N WLAN MiniCard is the n/w adapter Broadcom company
I had faced a similar problem on ubuntu 9.10 too
Please help with this. Please let me know if you require any particular command outputs..

---

