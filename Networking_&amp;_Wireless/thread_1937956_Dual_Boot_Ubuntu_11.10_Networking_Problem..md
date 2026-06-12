---
title: "Dual Boot Ubuntu 11.10 Networking Problem."
date: 2012-03-08
forum: Networking &amp; Wireless
---

### Post by BlinkinCat on 2012-03-08
Hi - this will be brief before I am logged off the internet again. I have a dual boot with Windows 7 which has no network problem. However with Ubuntu, I am logged off after about 7-8 minutes. The following may be of assistance.
```

geoff@ABC:~$ lspci -nnk | grep -iA2 net
03:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller [10ec:8168] (rev 06)
    Subsystem: Giga-byte Technology GA-EP45-DS5 Motherboard [1458:e000]
    Kernel driver in use: r8169

```Kindly ask for any further assistance.
Thank you.
 
Edit: I apologize profusely for supplying little information but I wasn't sure what was required. I may add that Internet connection was fine for 8 months when I was only using Ubuntu. It seems that the problem has only arisen after the dual boot made about 4 days ago. I really hope that some kind person can help me out.
 
Cheers - :)

---

### Post by BlinkinCat on 2012-03-09
Hi again,

To add to what computer I have , it has similar specs to this one -
[http://www.expresspcparts.com.au/Items/PC-052-ALT-Gaming-PC?sck=30536651&caSKU=PC-052-ALT-Gaming-PC&caTitle=Gaming%20PC%3a%20Core%20i7%202600%2c%20Z68%2c%208GB%20DDR3-1600%2c%201TB%20HDD%2c%20HD6770-1GB-DDR5%20HDMI#.T1pIXGzJCxR](http://www.expresspcparts.com.au/Items/PC-052-ALT-Gaming-PC?sck=30536651&caSKU=PC-052-ALT-Gaming-PC&caTitle=Gaming%20PC%3a%20Core%20i7%202600%2c%20Z68%2c%208GB%20DDR3-1600%2c%201TB%20HDD%2c%20HD6770-1GB-DDR5%20HDMI#.T1pIXGzJCxR)

I have been doing a bit of searching and came across this rather old bug report.
[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798)

At least now I am able to log onto successful sessions without the Internet dropping out regularly. Can anyone supply a more permanent fix to this problem? In the meantime I will continue searching. It is not ideal to unplug ethernet cable every time I wish to log on.

Thank you and cheers - :)

---

### Post by BlinkinCat on 2012-03-10
Hi all,

A possible Network solution for Dual Booting with a Desktop Computer.

1. June 2011 I removed original Windows Home Premium and installed Ubuntu 10.04

2. October 2011, a fresh install of Ubuntu 11.10

3. Both systems displayed no hint of any driver problem.

4. 4 days ago I removed 11.10 and re-installed Windows 7

5. Installed dual boot with 11.10

6. Immediately there were Network problems as outlined in Post 1 and Post 2

7. Method to rectify as outlined in Bug #86798 not very practical.
   [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/86798)

8. As there was no previous problem, I concluded that there may well be a problem caused by the installation of Windows 7

9. Bug #839393 - [https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393](https://bugs.launchpad.net/ubuntu/+source/linux-backports-modules-3.0.0/+bug/839393) and 

  Bug #573259 - [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/573259)

  provided other solutions particularly concerning installation of a new driver however      I thought I would tackle the problem from the possible Windows viewpoint first. I followed some methods outlined in some of the bug reports plus methods of my own.

10. I made an assumption (correctly or incorrectly) that a problem may occur if the Network Adapter was allowed to enter sleep mode. (For a dual boot anyway)

11. A couple of days ago I tried preventing from sleeping or hibernating as outlined in method three here -  [http://windows.microsoft.com/en-US/windows7/Sleep-and-hibernation-frequently-asked-questions](http://windows.microsoft.com/en-US/windows7/Sleep-and-hibernation-frequently-asked-questions) however it did not appear to make any difference.

12. I then followed the following procedure in Windows - Control Panel > Device Manager > Double Left Click Network Adapters > Right Click Controller > Left Click Properties > Power Management > Uncheck Allow the computer to turn off this device to save power > Advanced > Select Shutdown Wake-On-Lan > Select Value Disabled > Click O.K. > Close Network Adapters > Exit > Exit > Shutdown Windows

13. Then follow the following procedure  - Switch Power Supply off > Remove plugs > Remove Ethernet Cable from router > Switch off computer switch and remove plug. Leave the supply off for 15 minutes > Leave the Ethernet Plug out but reconnect plug in computer and switch on. Connect plugs and switch on supply to the computer and router. Log on to Ubuntu > Re-insert the Ethernet Plug > Issue the following commands, firstly to disconnect and then to reconnect the Network. ( For r8169 Driver )

```

sudo rmmod r8169
sudo modprobe r8169

```The above method has maintained continual supply for seven hours other for a 20 minute off time to test. Rebooted successfully. I have sent numerous emails and logged onto a number of sites to test as well as dual booting with Windows. All with no problem so far. If success continues I will repost in the (several) days ahead. Although the method is via Windows, I consider it is a legitimate option for those who dual boot. If any one considers the method unsound I would be pleased to hear from them.  

All the best and cheers - :)

---

