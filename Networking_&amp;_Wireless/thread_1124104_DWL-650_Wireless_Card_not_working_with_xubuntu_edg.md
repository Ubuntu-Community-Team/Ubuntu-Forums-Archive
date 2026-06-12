---
title: "DWL-650 Wireless Card not working with xubuntu edgy alternate"
date: 2009-04-13
forum: Networking &amp; Wireless
---

### Post by Tr10 on 2009-04-13
Hello,

Long time reader, first time poster :)
I have recently moved over from Windows to Linux for the freedom.

I have been able to install and opperate linux fine... until now.

I have edgy alternate installed on a older laptop.
From there I installed xserver, and a few other packages to get a gui.

I am now struggling to get my D-Link DWL-650 to connect to my DCHP network.
Edgy detects it perfectly, I can see it in iwconfig.

But it struggles to connect to my ssid.

I have double checked everything on my wireless router and it accepts connections from any other wireless device.
Including the same card inside windows.

I have heard of ndiswrapper but I have yet to try it since the card is detected inside edgy.

Has anyone experienced a problem like this before?
Thanks for any and all help.

---

### Post by Tr10 on 2009-04-13
Bump.

I am currently trying the instructions provided in:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCMCIA)

More specifically:
[http://sin613.blogspot.com/2007/02/i-win.html](http://sin613.blogspot.com/2007/02/i-win.html)
[http://sin613.blogspot.com/2007/02/i-win-again.html](http://sin613.blogspot.com/2007/02/i-win-again.html)

Hopefully, this will work :)

---

### Post by Tr10 on 2009-04-13
> **Tr10 said:**
> Bump.

I am currently trying the instructions provided in:
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCMCIA](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsDlink#PCMCIA)

More specifically:
[http://sin613.blogspot.com/2007/02/i-win.html](http://sin613.blogspot.com/2007/02/i-win.html)
[http://sin613.blogspot.com/2007/02/i-win-again.html](http://sin613.blogspot.com/2007/02/i-win-again.html)

Hopefully, this will work :)

This doesn't seem like it would apply to me since xUbuntu is already detecting the card with the orinoco_cs driver.

I'm not really sure what modules are in linux, are they similar to services in windows?

Would the fact that I have hardly any modules loaded affect my ability to connect to a DHCP network?

Any idea's would be helpful, thanks.


EDIT:

I've just confirmed that my DWL-650 works flawlessly in DSL without any tinkering.
My DSL is version: 4.4.10
I am connecting to my router via DHCP

---

### Post by Tr10 on 2009-04-13
Bump.

---

### Post by Tr10 on 2009-04-13
Bump.

---

### Post by Tr10 on 2009-04-14
> **Tr10 said:**
> Bump.

Bump.

---

### Post by Tr10 on 2009-04-14
Bump.

---

### Post by Tr10 on 2009-04-14
Bump.

---

### Post by Tr10 on 2009-04-15
Bump.

---

### Post by Tr10 on 2009-04-15
Bump.

---

### Post by Tr10 on 2009-04-16
Bump.

EDIT:

I somehow managed to fix this problem with the help of these instructions. 
[http://wiki.archlinux.org/index.php/Wireless_Setup#Wireless_Quickstart](http://wiki.archlinux.org/index.php/Wireless_Setup#Wireless_Quickstart)

Just put sudo infront of all the commands and that fixed it for me.

My problem was that in my /etc/network/interfaces files the auto was set to my loopback adapter.

It's always the easiest things that cause us the most trouble.
:)

Good luck to anyone else facing this problem, I've learned alot about linux just trying to fix it lol.

---

