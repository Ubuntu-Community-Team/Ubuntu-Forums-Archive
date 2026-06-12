---
title: "My Ubuntu is Bipolar"
date: 2010-04-15
forum: Networking &amp; Wireless
---

### Post by chernobila on 2010-04-15
First of all I want to say thanks to all of you for creating such a great community. This is the reason why I use Ubuntu and not any other distro. 

Now about the problem. (be aware, I am an early stage beginner in Linux) 

I am using usb wireless adapter for internet connection. I had to go through the hell to get the windows drivers working using ndiswrapper but at the end somehow I managed to do it. The problem is that after restarting the machine something happens and it stops working. To get it back up and working again it needs to be restarted multiple times. Then I get lucky during one of the restarts and its is working again. It is torture. I dont have enough knowledge with Linux to play with it so if anybody feels like helping me I will much appreciate it.

here is my lshw -C network

```
 *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 5
       bus info: pci@0000:02:05.0
       logical name: eth0
       version: 10
       serial: 00:1b:b9:75:3a:ed
       size: 10MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=half latency=32 link=no maxlatency=64 mingnt=32 multicast=yes port=MII speed=10MB/s
       resources: irq:20 ioport:ec00(size=256) memory:fdeff000-fdeff0ff
  *-network
       description: Wireless interface
       physical id: 1
       logical name: wlan2
       serial: 00:26:5a:c0:e3:b2
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+net8192su driverversion=1.55+FRYS Corporation,08/05/2009 ip=192.168.1.122 link=yes multicast=yes wireless=IEEE 802.11g 
```



BTW, when I go to System > Administration > Windows Wireless Drivers   it says "Unable to see if hardware is present" even when wireless network is working. And under "Currently installed network drivers it says net8192su.Hardware present:Yes


Thank you again for taking the time even for reading this.


Edit: Using Ubuntu 9.10

---

### Post by chernobila on 2010-04-15
seems like nobody has time for me at this point :(

---

### Post by chernobila on 2010-04-15
please help somebody

---

### Post by Bungler on 2010-04-15
According to the ubuntu hardware support site it matters which windows driver you use. I don't know whether you searched to find which one works the best (win 98-xp driver)?
See:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB)

Furthermore re-check your installation procedure. This problem is apparently more common e.g. check the 3th post of this forum:
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/68847-wifi-problem.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/68847-wifi-problem.html)
It might get you a bit further

---

### Post by chili555 on 2010-04-15
Does it help if you do?```
sudo su
echo ndiswrapper >> /etc/modules
modprobe ndiswrapper
exit
```

---

### Post by chernobila on 2010-04-16
> **Bungler said:**
> According to the ubuntu hardware support site it matters which windows driver you use. I don't know whether you searched to find which one works the best (win 98-xp driver)?
See:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsRealTek#USB)

Furthermore re-check your installation procedure. This problem is apparently more common e.g. check the 3th post of this forum:
[http://www.linuxforums.org/forum/redhat-fedora-linux-help/68847-wifi-problem.html](http://www.linuxforums.org/forum/redhat-fedora-linux-help/68847-wifi-problem.html)
It might get you a bit further


Well the drivers came with the card on the cd. 98 did not work at all. So I kind of had to use XP. 

I also red through the links you provided. Exactly same problems. 
Started out with kernel 2.6.17. wireless did not work. 2.6.18 was on and off. 2.6.19 works most of the time but still same restart problems. 2.6.20 just can not get it working so had to go back to 2.6.19 so no more updates for me. :(

Thank you a lot for the info

---

### Post by chernobila on 2010-04-16
> **chili555 said:**
> Does it help if you do?```
sudo su
echo ndiswrapper >> /etc/modules
modprobe ndiswrapper
exit
```

yes it took me two or three days to get to know and do that.(since I am very new to Linux)

without that network was acting weird. I could access the router at 192.168.1.1 but there was no internet. So card was working but I thought it was DNS problem so I used open DNS like 208.67.222.222 but still nothing. At some point I get to ping google.com etc but browser was not opening it. And after all that I came across ```
modprobe
``` and it works now but like I said after every restart it stops. 

See the thing is that I dont even know where exactly is my problem. Hardware? driver? compatibility? something else?I dont know.

---

### Post by Bungler on 2010-04-16
What happens if you physically remove the the dongle and then re-insert it? Is it recognized? 

Does trying this few times also help instead of rebooting: ```
sudo /etc/init.d/networking restart
```

What I read somewhere else is that if you re-install it every time, it does work. Perhaps you can make a standard script to fix it for every boot? It is not a perfect solution but I think it is better than the current situation ;).

And in the end you are a bit unlucky with your hardware. Since you are a new user I can advise you when you want to buy new hardware to check on forums and the Ubuntu support site whether your desired hardware is supported.

---

### Post by chernobila on 2010-04-16
> **Bungler said:**
> What happens if you physically remove the the dongle and then re-insert it? Is it recognized? 

Does trying this few times also help instead of rebooting: ```
sudo /etc/init.d/networking restart
```

What I read somewhere else is that if you re-install it every time, it does work. Perhaps you can make a standard script to fix it for every boot? It is not a perfect solution but I think it is better than the current situation ;).

And in the end you are a bit unlucky with your hardware. Since you are a new user I can advise you when you want to buy new hardware to check on forums and the Ubuntu support site whether your desired hardware is supported.

that actually helped. See I did not know about network restarting. THANK YOU MILLION.

As for the hardware I think that is best advice. I am going to study everything before I buy.That much I learned. After all I am never going back to windows any more. Linux is what I was looking for. 

So I guess I can change this thread to solved satus

Big thanks to everybody who helped me out or took time reading this. This is great community and see you guys around

---

