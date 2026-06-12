---
title: "Wireless issues"
date: 2010-04-10
forum: Networking &amp; Wireless
---

### Post by mett demon on 2010-04-10
Hi everyone, new laptop and thought I would leave the world of microsoft and join the ubuntu community. The problem I am faced with is that I can detect my wireless router(BTHomeHub2) and even connect to it. But then when I open up my browser nothing happens. I have a Compaq 615 and am running ubuntu10.04 beta 2 which is the first ubuntu distro that detects my wireless network as I have tried netbook remix, ubuntu9.10 and kubuntu9.10 which all wouldn't even detect my router. Am I as a noob not aware of something here? Any help would be appreciated as I have posted the same issue twice already.:confused:

---

### Post by Kyluke on 2010-04-10
The reason your Wireless wasn't being picked up by 9.10 is because you haven't "activated"/downloaded the drivers yet.

I too have a compaq 615 and needed to go to system --> Administration --> hardware drivers.

You should see your driver listed there. (there might be two) select the STA driver.

Select activate in the bottom right hand corner of the window.
You will need a connection to the internet present, either through LAN cable or however you might want to connect...

once they are installed it is required to restart and there we go they should work perfectly now.
They now work flawlessly on my compaq 615 and even better in many cases than in windows.

Good luck hope this helps

---

### Post by mett demon on 2010-04-10
Hi there,
thank you very much for your reply, unfortunately the only driver listed is for ati/amd grapics card which I have already installed. 
What baffles me is that a colleague at work has had a play about and suggested it works fine on an unsecure network but as soon as it is secured it doesn't work????? I have been in to my user account and have given wireless privileges as well.
You are right ubuntu looks and feels fantastic and I am glad to have made the change but wish I could get this working fully.....

---

### Post by mett demon on 2010-04-10
FYI

ben@ben-laptop:~$ sudo aptitude install wpasupplicant
[sudo] password for ben: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initialising package states... Done
Writing extended state information... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
Reading package lists... Done             
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done

ben@ben-laptop:~$ lshw -C network
WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network               
       description: Ethernet interface
       product: Marvell Technology Group Ltd.
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 10
       serial: d8:d3:85:09:74:1e
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.25 firmware=N/A ip=192.168.1.65 latency=0 multicast=yes
       resources: irq:28 memory:93100000-93103fff ioport:4000(size=256)
  *-network
       description: Wireless interface
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: wlan0
       version: 10
       serial: 70:1a:04:c1:cf:19
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 multicast=yes wireless=802.11bgn
       resources: irq:17 ioport:2000(size=256) memory:92000000-92003fff
ben@ben-laptop:~$ 
ben@ben-laptop:~$ 

I thought this may be of use

---

### Post by Kyluke on 2010-04-11
The broadcomm website will have the drivers for you as well.

---

### Post by mett demon on 2010-04-12
product: Realtek Semiconductor Co., Ltd.
vendor: Realtek Semiconductor Co., Ltd.
physical id: 0
bus info: pci@0000:06:00.0
logical name: wlan0
version: 10
serial: 70:1a:04:c1:cf:19
width: 32 bits
clock: 33MHz
capabilities: bus_master cap_list ethernet physical wireless
configuration: broadcast=yes driver=rtl819xSE driverversion=0014.0115.2010 firmware=62 latency=0 multicast=yes wireless=802.11bgn
resources: irq:17 ioport:2000(size=256) memory:92000000-92003fff

as you can see for some reason it comes up as a realtek wireless card

---

