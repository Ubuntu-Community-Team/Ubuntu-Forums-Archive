---
title: "Copying one network configuration to another..."
date: 2006-03-04
forum: Networking &amp; Wireless
---

### Post by Domie on 2006-03-04
I just bought a D-Link wireless LAN PCI adapter. Plugged it in, nothig happens.

The device manager says it recognises the hardware, thank God. So back to the network manager, opened the help page (for a change ;-) ) and noticed the programs do not match: in the help file, you have to click on "add" but in real life, there is no such button.

Tried the Live CD and guess what? I just had to enter the network SSID and WEP key, and that was it. It all detected right away.

My plan is to copy the network config from the Live CD to my installed version, but how do I do this?

Or is there another solution?

---

### Post by bscbrit on 2006-03-04
Are you asking which files to copy, or simply what method to use to copy the files?

The least high-tech method is to write down the working configuration from the live disk installation and then make sure that the same settings are present on your non-working config.

Secondly, you could copy the relevant files onto a floppy or usb drive, and then import them onto your working system. (This assumes you know which files to copy - hence my question at the start of my response!)

Thirdly, you can provide the results of 'ifconfig' from your working system in your next response, and I can try to help you duplicate them on your non-working system.  :-D

---

### Post by Domie on 2006-03-04
I want to know which files I have to copy, thanks.

PS: isn't it strange you cannot add a network connection as mentioned in the help file? That would solve the problem too, since the device is detected. And completely reïnstalling my Breezy is no option.

---

### Post by bscbrit on 2006-03-04
The usual files that require copying are:

/etc/network/interfaces (this file defines which interfaces are activated, their settings etc)

/etc/resolv.conf (this provides the DNS configuration)


But I am not sure why you cannot set up your wifi card - have you followed the wireless card troubleshooting guide? - [https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by Domie on 2006-03-29
Yep... I even reïnstalled Mandriva (which worked with ndiswrapper, but I prefer Ubuntu). 

Isn't it strange that the live version recognises the card and the install version not?

---

