---
title: "D-Link DWA-140 B2- How?"
date: 2011-08-19
forum: Networking &amp; Wireless
---

### Post by GuiGuy on 2011-08-19
Can anyone help me in getting a D-link DWA-140 B2 USB wireless adapter to work in Natty? I've pretty much exhausted all the "[how tos]("http://ubuntuforums.org/showthread.php?t=1542500")" on the web and threads I have found here have been no help.

I have tried using ndiswrapper with the recommended drivers (as posted by the far more knowledgable experts here) but all that does is lock up the system.

Alternatively, a valid recommendation for a wireless "n" usb adapter that actually works would do. 

I already  have several different devices but unsurprisingly most don't work at all and those that do have an abysmal transfer rate. They certainly don't reflect wireless "n" capabilities.

The devices I have at hand are the D-link DWA-140 B2, TP-LINK TL-WN821N, Netgear WN111 v2, A belkin device that's known not to work and a Netcomm 910n, 
 
I bought the DWA-140 because I [read here]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") that it worked out of the box. It was only after buying it that I realised there were different versions and as is the way the wrong version was delivered :confused:


TIA

---

### Post by praseodym on 2011-08-21
Show the following outputs:

```
lsusb
lsmod
rfkill list
```

---

### Post by tanapon on 2011-09-21
1. Add the following line to /etc/modules (you must be root to do this)

rt2870sta

2. Install ndiswrapper driver

3. Reboot your system

4. Plugin the wireless adapter DWA-140/B2 and GO!

:cool: :cool: :cool: :cool: :cool: :cool: :cool:

Never lose your faith in Ubuntu

---

### Post by GuiGuy on 2011-09-23
> **tanapon said:**
> 1. Add the following line to /etc/modules (you must be root to do this)

rt2870sta

ahhh, thanks tanapon. THat worked a treat. Now have it running rock steady, albeit it's come up at "g" speed. Transfers are near max speed 54mbps. I can live with that for now. 

BTW, I didn't need to install the ndiswrapper. Simply adding the module name worked?!


Thanks again.

---

### Post by GuiGuy on 2011-11-11
The D-link DWA-140 B2 USB now works "out of the box" in 11.10 - it is now working as a wireless n device with good speeds reported, although there is some packet loss.

---

