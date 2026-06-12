---
title: "Computer sending ethernet signal after Shut Down"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by DoritosBR on 2010-07-19
It's a really strange problem.

My Hardware: Rampage II Extrame with 2 onboard Marvel Ethernet controllers
       description: Ethernet interface
       product: 88E8056 PCI-E Gigabit Ethernet Controller
       vendor: Marvell Technology Group Ltd.


Case 1:
I boot Windows 7, use. Everything normal.
Shut Down the computer.
The ethernet leds goes off. Everything normal

Case 2:
I Boot Ubuntu Lucid 10.04 2.6.32-23-generic.
I use it. Everything normal.
I Shut Down the computer.
The ethernet leds (both on router and onboard controller) goes on a frenzy blink state indicating traffic.
After a few minutes the router freezes (Tried 2 routers. One Linksys and one TP-Link. Both freezes)
The lights never stop blinking, unless of course, I shut down my PSU, wait, and turn it on again.


I tried using wireshark and connecting the computer directly onto another one (without hubs or routers) to capture the packets.

The other computer indicates that it's receiving constant 192k per second on the Ethernet port. (probably on a lot of packets)
But the wireshark / tcpdump doesn't show anything. Probably bad packets.

Does someone have an idea of what is it?

This guy, has the exact same problem:
[http://superuser.com/questions/136670/computer-sending-data-while-turned-off/165463](http://superuser.com/questions/136670/computer-sending-data-while-turned-off/165463)

---

### Post by staf0048 on 2010-07-19
Hmm...

Is it possible that Ubuntu is downloading updates and for whatever reason when you shut it down that connection never gets closed properly?  

This may help diagnose the problem.

While ubuntu is up you can try running:

```
sudo ifconfig eth0 down
```

to stop the card completely.  This is a gentoo "trick" - not sure if Ubuntu uses ifconfig or not.

To start the card again, add "up" to the command instead of "down".  Also, your card may be eth0, eth1, eth2, etc.  To see the actual names of all the cards, just run "ifconfig" without any options.

---

### Post by DoritosBR on 2010-07-20
Hey, that worked.

As soon as I shut down the interface, the leds gone off, I shut the computer off and the leds stayed off.

When I normally shut off the computer, I'm using the ethernet (Instant Messengers, Torrents, browser)
I don't close them before shutting off.

But that shouldn't prevent Ubuntu from powering off the eth card.

Well, is there an shutdown script where I can put this command?

---

### Post by DoritosBR on 2010-07-20
Crappy workaround:

Create a file at /etc/rc0.d/ named S89"whatever", with the contents

```
#! /bin/sh

ifconfig eth0 down
```

Give executing permissions.

Really crappy, but worked

The system already has a script to shut down the eth interfaces on rc0.d
But looks like it isn't working.

---

### Post by staf0048 on 2010-07-20
Glad to here that solved your problem.  Is the whole process automated now and working?  What I mean is, when you start up the Ethernet card comes up and when you shut down it turns off without any extra commands or configuring?

If so, I'd say thats a pretty nice workaround.  Too bad it didn't work out of the box though.

---

### Post by DoritosBR on 2010-07-21
Yeah
To be almost perfect, I would need to do the same on /etc/rc6.d (runlevel "reboot")
As on reboot it also send the ethernet singal.

But I almost never reboot the system.

Thanks for the help :)

---

