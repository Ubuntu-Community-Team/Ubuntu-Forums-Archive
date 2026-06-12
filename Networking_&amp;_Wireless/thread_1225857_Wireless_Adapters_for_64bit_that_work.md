---
title: "Wireless Adapters for 64bit that work?"
date: 2009-07-29
forum: Networking &amp; Wireless
---

### Post by LeeLgrqst on 2009-07-29
I can not seem to get any of the three wireless adapters to work with my computer.  After checking the list of the compatible wireless adapters, I tried two of them, only to find out that they don't work with the 64 bit version of Ubuntu.  I started searching one by one through the list starting with the more popular brands, but none that I checked mentioned that they work with 64 bit.  I've gone back to the store two times to exchange and just got my money back this last time, but I do not want to give up.

Does anyone know of a wireless adapter,that will work with Ubuntu 9.04, 64bit version?  

Any help is greatly appreciated.

---

### Post by LeeLgrqst on 2009-07-29
So I decided to try the Netgear wg311v3 PCI wireless adapter.

I followed the directions given in this link:
[https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3]("https://help.ubuntu.com/community/WifiDocs/Device/Netgear_WG311_v3")

Everything seemed to go OK until I got to the step where I type in iwconfig.  The results from that are:

lo    no wireless extensions.
eth0  no wireless extensions.
pan0  no wireless extensions.

The directions say I should see a network interface with a whole bunch of details, but I do not.

Then I found this thread:
[http://swiss.ubuntuforums.org/showthread.php?t=179801]("http://swiss.ubuntuforums.org/showthread.php?t=179801")

Which didn't help me either.

Is there anyone who can help me with this problem?

I am running Ubuntu 9.04 64bit.
I just did a fresh install and the only things I have done are from those two links.

---

### Post by superprash2003 on 2009-07-30
post output of **lshw -C network**

---

### Post by Maheriano on 2009-07-30
Mine works, I can check the name on it when I get home if you want. I'm pretty sure it's a D-Link.

But, I know for sure that it wouldn't work until I installed the restricted wireless drivers for it. You have to do a manual hardware scan and it'll give you the drivers you can install. Once you do that it'll work. Let me know if this helps you.

---

### Post by LeeLgrqst on 2009-07-30
I don't know how to get it to be indented like it is on the terminal.
Hopefully this isn't too annoying for you.

lee@lee-desktop:~$ lshw -C network
WARNING: you should run this program as super-user.
**  *-network  **             
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:24:8c:69:66:e9
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=r8169 driverversion=2.3LK-NAPI latency=0 module=r8169 multicast=yes
 ** *-network UNCLAIMED**
       description: Ethernet controller
       product: 88w8335 [Libertas] 802.11b/g Wireless
       vendor: Marvell Technology Group Ltd.
       physical id: 6
       bus info: pci@0000:04:06.0
       version: 03
       width: 32 bits
       clock: 66MHz
       capabilities: bus_master cap_list
       configuration: latency=64
 ** *-network DISABLED**
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 96:66:65:80:6d:c4
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A multicast=yes

---

### Post by LeeLgrqst on 2009-07-30
> **Maheriano said:**
> Mine works, I can check the name on it when I get home if you want. I'm pretty sure it's a D-Link.

But, I know for sure that it wouldn't work until I installed the restricted wireless drivers for it. You have to do a manual hardware scan and it'll give you the drivers you can install. Once you do that it'll work. Let me know if this helps you.

I'd like to get this one to work, because it seems like many other people have had success.  Plus I'll learn more this way.  As frustrating as it is sometimes, I still kind of like the troubleshooting, with some help from people with more experience and knowledge.

But just in case, what is the name of the D-Link you are using?

---

### Post by LeeLgrqst on 2009-07-30
After doing some research on "network UNCLAIMED", I found out I may have not installed the driver correctly.  I am starting again and I will let you know what happens.

---

### Post by LeeLgrqst on 2009-07-31
I finally got it working.  Thank you for getting me going in the right direction.  It took me several hours and lots of frustration, but its working!

So it turned out I needed to download and install the 64 bit drivers, as mentioned in this thread:

[http://ubuntuforums.org/showthread.php?t=320111]("http://ubuntuforums.org/showthread.php?t=320111")

It didn't work at first, so I just set up the network preferences, (SSID, key, and security).

Then I reset, and it worked.

Thanks for the help.

---

