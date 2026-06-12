---
title: "Getting connected with a wireless USB adapter."
date: 2009-07-30
forum: Networking &amp; Wireless
---

### Post by StevenD on 2009-07-30
I have a Linksys wireless USB adapter and need some help figuring out how to get it connected. I posted something about this in the beginners section and it was suggested that post here for more help. The following was the last reply I received there about what I am trying to do. I typed in lsusb in the Terminal and got the following info.

steven@steven-laptop:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 003 Device 002: ID 066b:2212 Linksys, Inc. WUSB11v2.5 802.11b Adapter
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 2222:3080 MacAlly 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
steven@steven-laptop:~$

When I asked about what I am looking for I got the following in a reply.

It tells you that it is a Linksys WUSB11v2.5. The important part is the 066b:2212.

So what do I do with the this info. I am a real beginner with Linux and Ubuntu. I sure hope someone can help me understand and learn how to work with this operating system.:D

---

### Post by StevenD on 2009-07-30
[FONT=Verdana][SIZE=2]I found an article on how to set up a WUSB11 USB adapter but nothing in the article I try is working. Here is the address to the article. I know it says the information there may not be totally accurate.
[/SIZE][/FONT][FONT=Verdana][SIZE=2]
[https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11](https://help.ubuntu.com/community/WifiDocs/Device/LinksysWUSB11)[/SIZE][/FONT]

I'm getting no where fast. Maybe I should just get a PCI card instead of fiddling with this Linksys USB adapter. Unless someone can help. :(

---

### Post by bkratz on 2009-07-30
StephenD

Since I sent you to this forum I thought I would "bump" you back up from page 3!  Anyway, have a look at this thread

[http://ubuntuforums.org/showthread.php?t=946105&highlight=066b:2212](http://ubuntuforums.org/showthread.php?t=946105&highlight=066b:2212)

It seems that your device uses the Prism2 drivers inherrent in Ubuntu, but I am not an expert so please look here. Your device is listed in the bottom section.

[https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb)

---

