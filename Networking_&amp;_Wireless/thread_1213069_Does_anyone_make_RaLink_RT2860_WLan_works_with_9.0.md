---
title: "Does anyone make RaLink RT2860 WLan works with 9.04?"
date: 2009-07-14
forum: Networking &amp; Wireless
---

### Post by Nw01f on 2009-07-14
Hi all,

    I just installed ubuntu 9.04 on my MSI CR400 notebook. I have followed [https://bugs.launchpad.net/linux/+bug/210725/comments/152](https://bugs.launchpad.net/linux/+bug/210725/comments/152) to install driver for my RaLink RT2860 Wireless Lan Card but with no luck. Is there anyone success? Please Help!

---

### Post by Nw01f on 2009-07-14
I have also tried the method suggested here [http://ubuntuforums.org/showthread.php?t=683085&page=4](http://ubuntuforums.org/showthread.php?t=683085&page=4) . The driver I used  is [http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz](http://www.ralinktech.com.tw/data/drivers/2009_0521_RT2860_Linux_STA_V2.1.2.0.tgz) released on 05/21/2009. However, 9.04 cannot recognize the RaLink device. Any Suggestion?

---

### Post by zeronothing on 2009-07-15
that is really interesting because I have a Asus Eee PC 901 which has the Ralink rt2860 wireless chipset in it. The Wireless works right out of the box in ubuntu 9.04. Let me say it works right out of the box in the 9.04 netbook remix. I have not tried just regular ubuntu 9.04 on the netbook. I would imagine its the same, the only difference is the kernel in netbook remix is built specifically around the mobile processors like intels atom.

---

### Post by Nw01f on 2009-07-15
Hi, zeronothing

Do you mean that 9.04 remix can identify and install the RaLink rt2860 driver by itself?

Or, you used the methods I mentioned above?

Thanks

---

### Post by Ed934 on 2009-07-16
[B]I also have a RaLink RT2860 WLan, on an Asus eeePC 1000HEB. I used Wubi to install Ubuntu 9.04 but the wireless is not working. What good is a Netbook without wireless?

The Ubuntu Remix doesn't seem to have a Wubi installer. Is it actually set up for wiping the entire hard drive and replacing it with Ubuntu. I have to hold on too windows for work applications, etc.
[http://www.canonical.com/projects/ubuntu/unr](http://www.canonical.com/projects/ubuntu/unr)

Anyone know of a way to install it?

Ed
[/B]

---

### Post by cariboo on 2009-07-16
@Nw01f

Are you sure your wirless device isn't being detected?

Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network
```

and paste the output into your next post. The above command will print on screen a listing of your network devices abd whetther they are detected and the drivers are being loaded.

---

### Post by zeronothing on 2009-07-16
In order to install the netbook remix edition you will need a usb drive, external HDD, or a SD card to install it. If you have ubuntu installed on another machine, you can install it to one of the devices I mentioned above using the "USB Startup Disk Creator."

---

### Post by Ed934 on 2009-07-17
Thanks for the suggestion. Here are the results:
 

sudo lshw -C network

  *-network               
       description: Ethernet interface
       product: L1e Gigabit Ethernet Adapter
       vendor: Attansic Technology Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: b0
       serial: 00:24:8c:a7:ba:13
       size: 100MB/s
       capacity: 100MB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=ATL1E driverversion=1.0.0.7-NAPI duplex=full firmware=L1e ip=192.168.1.109 latency=0 link=yes module=atl1e multicast=yes port=twisted pair speed=100MB/s
  *-network
       description: Wireless interface
       product: RT2860
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:01:00.0
       logical name: ra0
       version: 00
       serial: 00:22:43:96:46:9b
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=0 module=rt2860sta multicast=yes wireless=RT2860 Wireless
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 1a:df:c0:76:d3:58
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

---

I don't really know how to read or understand any of this. Does the wireless DISABLED mean the card is being detected but somehow uninstalled? I am able to jump onto my neighbor's unsecured wireless network, so I do think my card must be working, but I can't logon to my SSID hidden network.

Any thoughts on the problem?

Ed

---

### Post by Nw01f on 2009-07-18
Result from lshw:

*-network
       description: Ethernet interface
       product: MCP79 Ethernet
       vendor: nVidia Corporation
       physical id: a
       bus info: pci@0000:00:0a.0
       logical name: eth0
       version: b1
       serial: 00:24:21:6f:44:74
       capacity: 100MB/s
       width: 32 bits
       clock: 66MHz
       capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=forcedeth driverversion=0.61 latency=0 link=no maxlatency=20 mingnt=1 module=forcedeth multicast=yes port=MII

  *-network UNCLAIMED
       description: Network controller
       product: RaLink
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:07:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0

  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: pan0
       serial: 62:79:91:2c:c9:7f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

I tried to install the driver but the result is the same. It shows : *-network UNCLAIMED.

---

### Post by Nw01f on 2009-07-20
Finally, I figured it out why rt2860 driver cannot be installed successfully in ubuntu. 

When I am in Windows, I can install the driver indicated as rt2860 successfully and worked perfectly. 

However, in ubuntu, the device is reported as [COLOR=Red]**rt3090**[/COLOR]!!

Now, I can install the rt3090 driver successfully but when I do "*sudo ifconfig ra0 up*", I received the following error: "*SIOCSIFFLAGS*: *Operation not permitted*"

What is this error mean? How can I solve it?

Any ideas? Please help!

---

### Post by Nw01f on 2009-07-20
Solved!

I have to rename /etc/Wireless/RT3090STA => /etc/Wireless/RT2860STA

Although it is a rt3090 driver, it uses rt2860 as it internal reference.

So, strange...

Anyway, the problem is solved now.:popcorn:

---

### Post by zrandyc on 2009-07-24
My EeePC 1000 has the RT2860. I have tried both the full version and the netbook remix of 9.04. Both come with the driver pre-installed. I cannot connect using WPA, but WEP seems to work fine. I have been advised to install the 2.6.30 kernel to try to get this to work, but I am more inclined to restore the version of Linux that came with the netbook. This is crazy.

---

### Post by mojobo on 2009-09-12
Struggling AGAIN with my eeePC 901 and wireless. Have yet to get it to work with ANY Ubuntu flavor, back to Hardy. Now the issues is WPA2 related. It will connect to my wireless without authentication, but just spins for awhile and comes back with password requests again and again with WPA (any flavor) enabled. I tried all the listed ideas in this and other forums.

What hasn't works
A) recompiled and installed various version of rt2860STA, the latest 2.1.2 included. B}Used Network mgr, command line iwconfig and wicd. 
    yes I put my essid on the command line.
C) configured RT2860STA.dat
D)  MD5'ed my versions and have updated to the max (Linux eeepc 2.6.28-15-generic)
E) I also tried easy peasy. But that one doesn't even install, drops me to the busybox.   Not willing to go any further there.

I have been working with Ubu on and off for years now and, each flavor, although improved, puts me into a dizzying spin of trying to fix some issue or another till I just give up and wait for the next release. Sure want this thing to work someday. The eeePC has been around long enough now I, think.

The Xandros and XP both work fine....guess I am still stuck back on the bench again, unless someone can come with with a stable wireless setup, of course then I will need the rt kernel. I can't waste my whole life chasing gremlins.

---

### Post by amouravski on 2009-09-13
Hello,

I have the same exact problem as zrandyc.
I bought the EeePC 1000 nine months ago and was able to get WEP working just fine all of the time. Unsecured networks also work. However, everyone is switching to WPA and that doesn't work.

I used the RaLink 2860 card for awhile and tried every single method mojobo used, to no avail. Seriously, all of those options failed.

It was suggested on another site to get a different wireless card, so I bought the Intel WiFi Link 5300 and just installed the drivers for that card and finally was able to get wireless working, but only unsecured and WEP. WPA still fails to work.

I am inclined to believe that there is some incompatibility between Ubuntu Netbook Remix 9.04 (maybe other versions) and the EeePC of models older and including 1000. Not sure if it is a kernel issue or what.
I've explored this issue and found that 900 models work with WPA with few problems (aside from installing drivers, etc.) Further, 1000HE models work out of the box, so it seems as though there is something wrong the 901 and 1000 models.

Help?
Thanks.

---

### Post by mojobo on 2009-09-14
Referring back to my last post about all the things that didn't work, after a night on the town and a bit hung over, I came back at this problem by following all the instructions in [http://www.array.org/ubuntu/setup-jaunty.html](http://www.array.org/ubuntu/setup-jaunty.html). Adam and his crew have been working very hard since the last time I visited their site, a year or so ago. I thought I had done some specific things that would have put ONLY their old wireless module in the system. Not sure what I might have screwed up, but this time I went solely by his setup instructions and lo and behold my wireless WPA is working FINALLY. Not sure which version he is using, since I have not found the proper magic to coax the version of a module out of the system yet. Using the easy peasy image which is supposedly built off Adam's work proved fruitless, but just installing his kernel and related modules, headers etc on top of a generic remix install did the trick. Of course now I am downgraded to rev 12 from rev 15....ah well and I still will have to find some compromise to get the real-time stuff going as I want a highly portable lightwieght, long battery life music station to accompany me when I play my guitar out about town. On to the next hurdle.

---

### Post by tm2383 on 2009-09-16
Think I'll just go back to Windows:confused:


T

---

### Post by tm2383 on 2009-09-18
I actually got the driver to work eventually. My Belkin USB uses version 3, but it is ther version 1 driver that worked.

---

### Post by bearman1 on 2009-10-08
We had a massive struggle on a Shuttle X50 to connect the RT2860.  After combing numerous threads we tried the following and it worked.  Good luck.
 
Check out the following link: [https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html](https://help.ubuntu.com/8.04/internet/C/ndiswrapper.html)
 
This explains how to use windows-based drivers and convert them to Linux.
 
Find the rt2860.inf windows driver and follow the instructions in the above link.
 
We followed some of the thoughts presented here:
[http://tuxtweaks.com/2009/01/ubuntu-on-the-msi-wind/](http://tuxtweaks.com/2009/01/ubuntu-on-the-msi-wind/)

---

### Post by copycat on 2009-10-10
My msi U100 works fine with the RT2860 an Jaunty.  There is only a problem with connecting to my WAG325N router. There seems to be an new driver on Ralink. (2.2.2.0)  The problem is that you need to buil/install the driver.  My question is.... when this procedure works... why doesn't anyone create a *.deb package for it? I don't have the skills to build the driver... a *.deb would solve this. :-)

---

