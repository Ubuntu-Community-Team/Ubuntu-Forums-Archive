---
title: "Atheros AR9285 Driver problems"
date: 2009-08-19
forum: Networking &amp; Wireless
---

### Post by robintu on 2009-08-19
Hi,

I've recently decided to go back to having a dual boot system with both linux and windows after using vista for a while. I installed ubuntu 9.04 but the wireless net just does not work. I have no option to connect to internet while on linux, I am not in my windows system, so sudo apt-get stuff is not available.

I am sitting on a hp pavilion dv6 1299 eo. 

**$ lspci** gives me

Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)

And if of any relevance
Ethernet controller: Realtek semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)

$ ifconfig gives a lot of numvers and stuff mostly 0s, if it's of relevance to solving the problem I can write it here but it's slightly much to write.

**$ iwconfig gives**

lo no wireless extensions.
eth0 no wireless extensions.
pan0 no wireless extensions.

**$ lsmod**

I fail to find something which seems relevant.

**$ dmesg**

Gives pages of text which to me makes no sense.

**$ iwlist scan**
lo
eth0
pan0

all with "interface doesn't support scanning"

**$ sudo /etc/init.d/networking restart**

* Reconfiguring network interfaces... [ ok ]

I've tried ndiswrapper with a driver I found in the windows installation, I've tried with 3 drivers from atheros.cz and I also tried searching the forums where I found some information but nothing which I was able to make it work with.

Thank you for reading, and hopefully answering :)

---

### Post by robintu on 2009-08-20
Still haven't been able to figure out a solution.

---

### Post by kfries6 on 2009-08-20
NP, I actually have the AR9285 working in Ubuntu, but it does not work out of the box unfortunately.

There are two solutions to this.  First of all, let me state that the solution is already on the way, and this will very shortly work out of the box... its just not there today.

Also, unfortunately, both solutions require a network connection of some sort.  What I did was use a cheap, Linksys Wired Ethernet to USB adapter.  It got me over my initial problem, and provides a fast and cheap failover.

[http://www.partstore.com/Part/Cisco+Systems+Inc/Linksys/USB100M/New.aspx](http://www.partstore.com/Part/Cisco+Systems+Inc/Linksys/USB100M/New.aspx)

Once you have network, connectivity you can either install the drivers in JJ by issuing the following command:

# apt-get install linux-backports-modules-$(uname -r)

or do an early upgrade to Karmic Koala by issuing this command:

# do-release-upgrade -d

(or in a graphic environment, press CTRL-ALT-F2, and type "gksudo update-manager -c -d" in the run box)

Both of these solutions will add the appropriate drivers.  Restart network or reboot.  The device will be added to your system... look in /etc/udev/rules.d/70-persistent-net.rules to see what interface name the system created for your device.  It will be the one using the ath9k driver.

HTH
Kevin Fries

---

### Post by chilimac02 on 2009-08-22
Having same issue here.

My machine came with windoze XP. Any way I can download the drivers while running in XP put them on USB stick then install them after I reboot in JJ?

better ideas?

---

### Post by GreanTee on 2009-09-04
The backports solutions works great, thanks!

Greetz, 
GreanTee

---

### Post by jeroenvrp on 2009-09-12
Unfortunately the driver in Karmic is not working very well (yet?). After a while the strength of the signal is weakening. No problem when I'm at home, but at school I always loose the signal after approximately 1/2 to 1 hour. Is there also an native driver for Linux?

---

### Post by pi4r0n on 2009-09-15
Hello ALL

I have managed to fix an issue with no WIFI on my **Atheros AR9285** card by doing

> apt-get install linux-backports-modules-$(uname -r)Unfortunately :( yesterday I have noticed that it does not support WPA2 PSK encription :(

Any one who can help ?? if yes I can provide more details

Cheers

pi4r0n

---

### Post by Cerox Rex on 2009-12-17
Hello.

I'm also running into trouble with the AR9285 Chip. My problem have to do with Instability and conection errors when connecting to a 802.11g-n AP. When AP is running in b mode i have no issues.

The driver used is the ath9k, and I'm running Ubuntu 9.10.

My lspci returns same info as in the first post.

---

### Post by drpjkurian on 2009-12-19
Hi Guys
Please do give a try for my thread it might help you out.
The URL [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Best of luck
Dr Kurian

---

### Post by Cerox Rex on 2009-12-21
> **drpjkurian said:**
> Hi Guys
Please do give a try for my thread it might help you out.
The URL [http://ubuntuforums.org/showthread.php?t=1309072](http://ubuntuforums.org/showthread.php?t=1309072)

Best of luck
Dr Kurian

No luck for me :(
Madwifi seemed to diable my wierless interface completly, as none was found with wicd or iwconfig.

when reverting to compact-wierless Wicd got stuck on obtaining IP address, now i reverted back to network-manager-gnome, and seems to have a stable connection.

Maybe the latest compact wireless drivers did the trick for me!

---

