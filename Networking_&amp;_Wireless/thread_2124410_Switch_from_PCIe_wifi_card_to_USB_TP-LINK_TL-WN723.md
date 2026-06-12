---
title: "Switch from PCIe wifi card to USB TP-LINK TL-WN723N causing huge throughput loss"
date: 2013-03-10
forum: Networking &amp; Wireless
---

### Post by MrAureliusR on 2013-03-10
As my title says, up until a few days ago I was using a Gigabyte GC-WB3000 PCIe x4 wifi/bluetooth combo card. It's a great card that I had no problems with in Ubuntu or Vista. My ISP delivers 25Mbps download and 10Mbps upload (though I typically get more like 23/15). I recently had to free up that slot so I switched back to a USB wireless N dongle, namely a [TP-LINK TL-WN723N]("http://www.tp-link.dk/products/details/?model=TL-WN723N").

Since that switch, all network throughput in Ubuntu has slowed to a crawl. When using apt-get install, for example, I'm getting downloads of 20-30 KB/s instead of between 2-3 MB/s as I was before (depending on the server, of course). Even surfing the internet is painfully slow. 

I'm using Ubuntu Server 12.10 x86_64 with kubuntu-desktop package installed (I don't know if that offically makes it 'kubuntu' or not -- I just prefer KDE and that's how I was told to get it). It's dual-booted with Windows Vista Ultimate 64-bit, which has had no problems whatsoever with both the Gigabyte and the TP-Link cards. A speedtest.net result in Windows shows the speeds I listed above as typical from my ISP, whereas in Ubuntu the connection is so slow it can barely even load the test.

The TL-WN723N is using the rtl8192cu module as far as I can tell. I've included links to my pastebin of the following commands:

[lsmod]("http://aurelius.pastebay.net/1188300")
[sudo iwlist scan]("http://aurelius.pastebay.net/1188301")
[iwconfig]("http://aurelius.pastebay.net/1188302")
[lsusb -v]("http://aurelius.pastebay.net/1188303")

I know the last one is very long, but I'm only familiar with | grep which seems to only give one line at a time, not a whole section. If someone can guide me on how to do that I can shorten it. By the way, I'm still a relatively new user of Linux but I'm a fast learner and I've been using command line interfaces for a long time. I'm happy to add any more pastes if needed. I like to learn what I'm doing as I'm doing it so an explanation of what commands are being used is appreciated too.

I've looked around but nobody seems to have had the exact same problem... mostly people unable to connect at all or very slow speeds with PCI cards because of a PCI driver issue etc... any and all help is very much appreciated!!

Thanks.

**EDIT: **After a bit more research ([this page]("http://community.linuxmint.com/hardware/view/5413")) it seems that someone else had success using rtl8192su instead of cu. I have another PC in my bedroom that was using this USB wifi stick with rtl8192cu -- I had to make the driver using the install.sh. That seemed to work fine with that computer (which is running ubuntu 12.10) but the same driver on this computer is giving me trouble. Granted, that link is for Linux Mint, but that distro is based off of ubuntu isn't it?

Also, [this thread]("http://ubuntuforums.org/showthread.php?t=1885991") mentions another driver being installed to solve a different problem with the same stick. Sorry for the info overload, I'm just eager to troubleshoot. :) Thanks again anyone.

---

### Post by MrAureliusR on 2013-03-11
Nobody? :(

---

### Post by QIII on 2013-03-12
&#65279;Everyone's issues are very important to them and we certainly understand that. Some things are terribly frustrating!

Let me assure you that you are not being ignored.
 
This is a volunteer community of users from all around the world. Not everyone here can answer every question. The person with just the right answer may live in Kolkata and be asleep at the time you post, or in Geneva having dinner with his/her family or Des Moines at work. Sometimes it takes a bit for us to get to the forums and answer questions.
 
So please do not take it as a snub if your question has not been answered already.
 
You gave it 24 hours to make the rounds before bumping, which is good. Sometimes an odd bump at 36 hours or something might catch other people in a different time zone at their computers.  I don't think anyone would growl too much if we saw another bump about 12 hours from now if you don't get a response.  But don't do that every time.

---

### Post by MrAureliusR on 2013-03-12
I'm sorry, I didn't mean to imply I felt snubbed. At other forums I've been a part of, once your post falls off the front page it usually doesn't get answered. Forgive me for jumping the gun on bumping.

My original question is moot as I've switched to ethernet again -- however I DO still have a question. The ethernet card that I installed has Linux drivers available on their website, but the driver download is the same for all OS's. The archive it comes in, though, seems to only have exe's and .cab files. Am I missing something or is there a way to make drivers from that? Here's a link to the page, if anyone can help I'd much appreciate it! [http://www.dlink.com/us/en/home-solutions/connect/adapters/dfe-530txplus-10-100-fast-ethernet-desktop-pci-adapter](http://www.dlink.com/us/en/home-solutions/connect/adapters/dfe-530txplus-10-100-fast-ethernet-desktop-pci-adapter)

Also, lshw reports the card like this:
```

*-network
description: Ethernet interface                
[I][B]product: VT6105/VT6106S [Rhine-III]                
vendor: VIA Technologies, Inc.[/B][/I]                
physical id: 7                
bus info: pci@0000:03:07.0                
logical name: eth0                
version: 86                
serial: 34:08:04:2d:89:90                
size: 100Mbit/s               
capacity: 100Mbit/s                
width: 32 bits                
clock: 33MHz                
capabilities: pm bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation                
configuration: autonegotiation=on broadcast=yes driver=via-rhine driverversion=1.5.0 duplex=full ip=192.168.2.12 latency=64 link=yes maxlatency=8 mingnt=3 multicast=yes port=MII speed=100Mbit/s [FONT=monospace]                
resources: irq:21 ioport:ce00(size=256) memory:fddff000-fddff0ff memory:fdc00000-fdc0ffff[/FONT]
```

So does that mean I should look for a linux driver for that VIA chipset instead? The card is working, but not as optimally as it should. In Windows I'm getting my regular ISP speeds but in Ubuntu 12.10 I'm still getting less than %30 of that speed.

Thanks again everyone for your support! I know these forums are great and I have huge respect for anyone who takes time out to help on a forum like this. I spent many hours on xda-developers writing guides for phones and I know how much time it really takes to help out!

---

