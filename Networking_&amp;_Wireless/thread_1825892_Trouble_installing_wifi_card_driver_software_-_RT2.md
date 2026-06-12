---
title: "Trouble installing wifi card driver software - RT2800"
date: 2011-08-15
forum: Networking &amp; Wireless
---

### Post by Metalman43 on 2011-08-15
OK i just installed a Rosewill RNX-N300X PCI LAN wireless card and i tried installing the driver software but it keeps giving me the "0x80040707" error and it terminates the download. I am not sure how to fix this, ask me questions if you need to i just need help because i really dont like having my computer on my dining room table plugged into the router lol i would much rather have it in my bedroom :P

---

### Post by Mark Phelps on 2011-08-16
How did you install the card?

Also, if you're trying to install Windows SW for your card -- that will not work.  You can not run Windows drivers in Ubuntu.

There is an option using NDISWrapper that will allow you to utilize Windows .INF files to load the network drivers -- but that is not done by running any Windows .exe files (if that is what you're trying to do).

To find out about NDISWrapper, you should do a search in the Networking forum.  There are lots of threads there dealing with that.

---

### Post by coffeecat on 2011-08-16
> **Metalman43 said:**
> OK i just installed a Rosewill RNX-N300X PCI LAN wireless card 

We need a bit more information. Some manufacturers use different chipsets at different times in the same model number., and it's quite possible that there is a native Linux driver for it.

Open a terminal and post the output of:

```
sudo lshw -C network
```

There will be quite a bit of output which will scroll off the standard size of a terminal window. Highlight it all with the mouse, right-click -> copy, and paste it into your post.

---

### Post by Metalman43 on 2011-08-16
@coffecat:

*-network:0             
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink
       physical id: 2
       bus info: pci@0000:01:02.0
       logical name: wlan0
       version: 00
       serial: 00:1a:ef:1d:a5:61
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2860 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=RT2860 Wireless
       resources: irq:17 memory:fe9f0000-fe9fffff
  *-network:1
       description: Ethernet interface
       product: 82562EZ 10/100 Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@0000:01:08.0
       logical name: eth0
       version: 02
       serial: 00:11:11:22:21:91
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.24-k2-NAPI duplex=full firmware=N/A ip=192.168.1.105 latency=64 link=yes maxlatency=56 mingnt=8 multicast=yes port=MII speed=100MB/s
       resources: irq:20 memory:fe9ef000-fe9effff ioport:df40(size=64)

@Mark Phelps:

I followed the instructions basically, i installed the card and put in the CD and followed the "install wizard" and it seemed to be running fine but then it gave me an error message and said it had to terminate the installation. It didn't give me a reason why, just that error code.

---

### Post by coffeecat on 2011-08-16
> **Metalman43 said:**
> I followed the instructions basically, i installed the card and put in the CD and followed the "install wizard" and it seemed to be running fine but then it gave me an error message and said it had to terminate the installation. It didn't give me a reason why, just that error code.

The reason why is what Mark Phelps has already explained. The driver installer is a Windows executable which won't run in Linux, and the Windows driver won't work in Linux, unless you use ndiswrapper.

However...

> **Metalman43 said:**
> 
       description: Wireless interface
       product: RT2800 802.11n PCI
       vendor: RaLink

<snip>

driver=rt2860

You have a Ralink wireless chipset and the Linux driver for it is already installed. Have you tried clicking on the Network Manager icon to see if your system can see your wireless network?

---

### Post by Metalman43 on 2011-08-16
i tried what you said and it worked but for some reason it connects and than disconnects right away. i made sure all the settings were correct and it should work but it keeps disconnecting for some reason.

---

### Post by coffeecat on 2011-08-16
I don't have experience of that Ralink chipset. You really need someone who does, but the title and location of this thread may not attract the attention of someone who can help.

I suggest you ask a moderator to edit the thread title - only a moderator can do that - to include "RT2800". Also, ask the moderator to move the thread to the wireless subforum, here:

[http://ubuntuforums.org/forumdisplay.php?f=336](http://ubuntuforums.org/forumdisplay.php?f=336)

The way to ask for moderator help is to click on this button - [img]http://ubuntuforums.org/images/buttons/report.gif[/img] - which you can find under your bean count in the left panel of your post. No, honestly! :) It might seem strange to click on something labelled "report abuse" to communicate with staff, but that is OK. Believe me. It's only called "report abuse" because its most common function is to report spam or other forum abuse. I've used it myself to ask a moderator to change the title of one of my own threads.

Good luck!

---

### Post by Metalman43 on 2011-09-11
ok i haven't been on in a while but i have some new details. i thought it was a hardware issue so i got it replaced and that card wouldn't connect either. I also tried another wireless card but it had the same issue. (ie. it identified that there was a wireless network but would not connect, it would just say "disconnected from wireless network" every time i would attempt to connect)

---

