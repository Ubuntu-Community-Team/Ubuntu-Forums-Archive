---
title: "Share internet through ethernet cable"
date: 2008-12-24
forum: Networking &amp; Wireless
---

### Post by dmillerw on 2008-12-24
I'm trying to set up a shared internet connection between a Windows XP laptop (which has wireless,) and a Ubuntu 8.10 desktop (which just has an Ethernet port.)

Is there anyway I can do this?
I don't have access to either computer right now, (there both my sisters, I'm setting it up for her) but will give some hardware info when I can.

Thanks in advance!

---

### Post by 2hot6ft2 on 2008-12-24
Wireless router that way you can plug the desktop in by Ethernet and the laptop can connect to it via wifi.

---

### Post by dmillerw on 2008-12-24
We have a Wireless Router, but its on the other side of the house and the only long network cable we have is already being used. We only have one USB WiFi adapter, (my computer is using it,) So we have no other way of connecting it to the internet without moving a bunch of stuff around.

---

### Post by dmizer on 2008-12-24
No problem to do this.

You'll probably need to reconfigure the physical network like this:

Modem -> Ubuntu -> wireless router ~> Windows

For the above to work, you'll need to disable NAT on the router, and configure Ubuntu for ICS like this: [http://help.ubuntu.com/community/Internet/ConnectionSharing](http://help.ubuntu.com/community/Internet/ConnectionSharing)

You can also configure the network like this:

Modem -> Windows -> wireless router ~> Ubuntu

For this to work, you'll need to disable NAT on the router, and configure Windows for ICS like this: [s]www.homenethelp.com[/s] (bad site)

Since you indicated that the Ubuntu computer does not have a wireless adapter, you'll probably have to use the first option. Does the Ubuntu computer have more than one ethernet adapter?

---

### Post by dmillerw on 2008-12-24
No, only has one Ethernet port

The problem is that if I did Modem -> Ubuntu -> wireless router ~> Windows, it would mean moving the Modem and Router into my sisters room, or moving the Ubuntu computer into the main room.

She wants the Ubuntu computer in her room, and If we had the modem and router in her room, it would mean we'd have to put my Dads computer in there too.

Is there anyway to set it up so the Ubuntu computer can use a shared WiFi connection through an Ethernet cable?

---

### Post by dmizer on 2008-12-24
You mean like this?

Modem -> wireless router ~> Windows? -> Ubuntu

You can do it, but it's more tricky. You'll have to:
[LIST=1]
[*]Use a [crossover cable](http://en.wikipedia.org/wiki/Ethernet_crossover_cable) or hub between the Windows and Ubuntu computer
[*]Make sure that the two network cards on the Windows computer (wireless and wired) are on different subnets.
[*]Correctly configure the Windows computer for CS across a subnet.
[*]Manually configure [DNS servers](https://www.opendns.com/smb/start/device/ubuntu) on the Ubuntu computer
[/LIST]

Problems with this setup will be that the Ubuntu computer will not be able to share files with any computer on your LAN except for the Windows machine it's directly attached to. That, and you'll have to have at least a basic understanding of subnets and what that means.

Here's a decent article on subnets: [http://www.cit.cornell.edu/computer/support/subsubnetting.html](http://www.cit.cornell.edu/computer/support/subsubnetting.html)

Edit:
The site I linked to earlier for how to do ICS with Windows is apparently compromised and infested with malware. Here is an alternative: [http://www.helpwithwindows.com/WindowsXP/howto-23.html](http://www.helpwithwindows.com/WindowsXP/howto-23.html)

---

### Post by dmillerw on 2008-12-24
OK, I have a crossover cable, and It doesn't matter that it can't share with anything besides the laptop.

I've done this with two Windows computers before, so I should be able to figure it out.

Thanks for the help.

---

