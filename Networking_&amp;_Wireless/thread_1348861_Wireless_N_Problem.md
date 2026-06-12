---
title: "Wireless N Problem"
date: 2009-12-07
forum: Networking &amp; Wireless
---

### Post by goldleader80 on 2009-12-07
Ok im having a few problems getting wireless N to work on a Dell Inspiron 1200 with a Belkin F5D8013 N Wireless Notebook Card PCMCIA.  I have installed it using ndiswrapper and the driver from the cd, and it is connecting fine to my wireless network the trouble is its only connecting with G at 54Mb/s and i want to get it connected via N.  I know this should work because i have XP also on the laptop dual boot and have installed the same driver in XP and get a connection of 150Mb/s so the card and driver do work.  How in ubuntu can i change the network type from G to N or is this automatic?  Here is the output of lshw -C Network:

description: Wireless interface
       product: RT2760 Wireless 802.11n 1T/2R Cardbus
       vendor: RaLink
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlan3
       version: 00
       serial: 00:1c:df:2f:60:c9
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ndiswrapper+rt2860 driverversion=1.55+Arcadyan Technology Corpora ip=192.168.1.9 latency=64 maxlatency=4 mingnt=2 multicast=yes wireless=IEEE 802.11g
       resources: irq:16 memory:24000000-2400ffff


Also im using Ubuntu 9.10 with all the latest updates.

Thanks

---

### Post by goldleader80 on 2009-12-08
Please someone must be using Wireless N on Ubuntu 9.10?????????

---

### Post by teward on 2009-12-08
You know, there's a huge issue with people continuous-bumping their posts.

I'll let you in on a secret...  N vs. G, not much difference.  'cept N has longer distance and more transfer speeds which don't really impact your download speeds.

First, a networking lesson:

The speed indicated by Mb/s (or Mbps) means megabits per second, which is the connection speed to the router.
The speed indicated by MB/s (or MBps) means megabytes per second, which is your internet connection speeds for downloading, uploading, etc.

Second, my thoughts:

I don't use 9.10, I use 9.04, and 75% of the network I'm on uses N routers/access points.  The good thing about this is that I get wonderful within-network transfer speeds.  The bad thing is that accessing the internet is nowhere near as fast as in-network access.

Now in the case of it not connecting, the computer auto-connects to whatever network it can, on whatever compatible channels it can.  If your computer is not connecting to N, then its because the system does not recognize N power.  Granted, this isn't easy to fix, as the wireless card and network manager auto-connect.

ALso, if you want to try the terminal, you can **manually** configure your wireless to connect to a specific network with the terminal command iwconfig (check the man pages), but (1) you have to provide all the data about the connection and (2) I think if you do that, you're auto-connectivity will cease, and you might have to do this multiple times (whenever you restart).


Sorry if I'm not that much of a help.

---

### Post by Jules1974 on 2009-12-09
A trekky giving humour to a star wars geek. Will the fun never end.

Never mind, maybe someone who has had your problem will actually be able to help.. :-)

May the force be with you, nanoo nanoo.

---

### Post by goldleader80 on 2009-12-09
TrekCaptainUSA

Thanks for the reply.  Love the sarcism its a great help when i ask straight forward question.

You talk as if i don't know what im talking about.  My question was how do i connect to my wireless via N on my wireless card not if N is a worth while connection type.  Replies like yours could put newbies off from using Ubuntu in the future.  You shouldn't assume someone knows less than you, just because this is my first post doesn't mean im a newbie, i just happened to forget my login so created a new account.  These forums are here to help people, just because i don't know how to setup my wireless card correctly doesn't mean i don't know how to use the command line!!!

I need N as my internet connection is 50MBps so wireless G with encrpytion to my router won't give me my full connection speed, at best with G and encrpytion i will be getting half of the stated 54MBps.

But the main reason i want to connect via N is for a faster within-network transfer speeds between the laptop and my file server.

When you talk about configuring the connection with iwconfig can you state if the connection will use N?

---

### Post by Menthu_Rae on 2009-12-10
Hey mate, ignore the wandering people who don't help. There are lots here (and on every forum).

Anyway, for the ralink chipset-based wireless cards (which yours is) - the drivers and config files are a bit flakey.

You have a couple of options:

* Try building the driver yourself from the ralink website and using the make options/etc (detailed in other threads on here, do a search for ralink driver and maybe include your card which is an rt2760)

* Try adding in a config dat file within /etc/Wireless with the correct options to enable N mode. There was a thread here detailing the process for the **rt2860**- I can't say for sure whether it will be the same or similar for the rt2760.

dat setup --> [http://ubuntuforums.org/showthread.php?p=8473382#post8473382](http://ubuntuforums.org/showthread.php?p=8473382#post8473382)

These may/may not work for you. You could also look at going back to 9.04 which some people say has a working driver (though im not sure at N speeds or not).

All the best and if you get stuck come back here, I will try to keep an eye on this thread and help where/when I can. :)

> **goldleader80 said:**
> TrekCaptainUSA

Thanks for the reply.  Love the sarcism its a great help when i ask straight forward question.

You talk as if i don't know what im talking about.  My question was how do i connect to my wireless via N on my wireless card not if N is a worth while connection type.  Replies like yours could put newbies off from using Ubuntu in the future.  You shouldn't assume someone knows less than you, just because this is my first post doesn't mean im a newbie, i just happened to forget my login so created a new account.  These forums are here to help people, just because i don't know how to setup my wireless card correctly doesn't mean i don't know how to use the command line!!!

I need N as my internet connection is 50MBps so wireless G with encrpytion to my router won't give me my full connection speed, at best with G and encrpytion i will be getting half of the stated 54MBps.

But the main reason i want to connect via N is for a faster within-network transfer speeds between the laptop and my file server.

When you talk about configuring the connection with iwconfig can you state if the connection will use N?

---

