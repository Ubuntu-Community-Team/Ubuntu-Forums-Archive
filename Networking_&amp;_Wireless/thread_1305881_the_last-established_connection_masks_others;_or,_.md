---
title: "the last-established connection masks others; or, strange networking issues!"
date: 2009-10-30
forum: Networking &amp; Wireless
---

### Post by inportb on 2009-10-30
My Ubuntu laptop has a wired interface and a wireless interface. Upon booting, Ubuntu automatically activates the wired interface; as soon as I login, the wireless interface is enabled as well. This is good: I want to simultaneously use both interfaces. However, when I try to ssh, ping, whatnot from my Android phone, I could only reach the laptop over the wireless interface. So I use the tray applet to reconnect to the wired interface, and now my phone could reach the laptop over the wired interface but not over the wireless interface. Unplugging/replugging the wire causes NM to reconnect on the wired interface, but does not switch availability from the wireless interface to the wired interface. Can't I have both?

Incidentally, when connecting using another client computer on the [wired] network, the opposite problem occurs: the laptop is accessible over the wired interface but not the wireless interface. If I unplug the wire so that only the wireless interface is available, I can ssh to said client and ssh back over the wireless interface; once I replug the wire, the connection to the client instantly dies. On the other hand, disabling/enabling the wireless interface does not similarly disrupt the wired connection.

The wired and wireless networks are on different subnets, but I have publicly accessible IP's on both. My phone connects to the same wireless network. I currently have port 22 open on my laptop. With the wire unplugged, a [portscan]("http://www.yougetsignal.com/tools/open-ports/") of the wireless IP confirms that the port is open. As soon as I replug the wire and activate the interface, the same scan shows that the port is closed, but a scan of the wired IP shows that the port is open. Meanwhile, my phone happily connects on the wireless interface. I have a feeling this is related to conflicting subnets. What gives? Thanks for any tips...

---

### Post by inportb on 2009-11-02
So... I kinda didn't expect anyone to respond to this thread. Oh well, I guess I'll keep tinkering and ask for help from time to time. Thanks guys.

---

### Post by ST3ALTHPSYCH0 on 2009-11-02
Hey, I had a couple of important questions on here that didn't get answered. Part of the issue is the sheer number oof posts on here.... any post is quickly buried to the third, fourth, or even further down page. I don't know if you've tried other forums or Googling, but I highly recommend it. Why? two reasons: 1. You get your answer faster. 2. You can then post the answer here for anyone else having the same or similar issue. 
Good luck, BTW, I'll ask in the Linux subforum on The Win Forums for ya!

EDIT
I found a possible _[in the archives]("http://ubuntuforums.org/archive/index.php/t-931599.html")_.

[This](http://ubuntuforums.org/showthread.php?t=622549&page=2) solution seems to address and totally solve your dilemma. I'd say stick to page 2 here, page one's solution seeded dubious.

---

