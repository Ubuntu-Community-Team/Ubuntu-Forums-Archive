---
title: "no wireless (way out of my depth)"
date: 2009-02-23
forum: Networking &amp; Wireless
---

### Post by JoeTheNihilist on 2009-02-23
Hi there,

I've just installed ubuntu 8.04 (first time using ubuntu) on my old thinkpad T23 and I'm having predictable trouble setting up my cheapie wireless card.

So, here goes;

The computer will connect to the router fine using a cable. No problems there.

The card did not work after the install, so I installed ndisgtk and the windows driver, all appeared to go smoothly

*iwconfig* shows the card to be wlan1, so I right click on the taskbar icon, go to properties and set the connection name to wlan1. It says status: Disconnected. If I click configure, I get a message saying the interface does not exist. 

Trying *lshw -C network* tells me that the windows driver appears to be working (driver=ndiswrapper+netmw125). It also confirms the logical name is wlan1.

Trying *iwlist scan* actually detects my router. This makes me think there is no problem with the card or the driver. 

So, why does it still say that the interface does not exist? I'm running out of things to try...

The card is a 88w8335 [Libertas] made by Marvell Technology, apparently. It also says sweex on it, along with "Connect to a wireless network!" and a picture of a smiling girl, which isn't hugely reassuring right now...

Any help appreciated

---

### Post by kmacphail on 2009-02-23
This may seem to be a bit pointless, but when I installed Ubuntu first and had to use ndiswrapper I had the same problem.

A simple restart of the PC and then on loading up it asked me do I want to continue with the altered network settings.  Click yes and then all you need to do is find your router and enter the WPA key.  

This worked for me when I had a similar problem and I hope that it is as easy for you.

---

### Post by JoeTheNihilist on 2009-02-23
ok, false alarm people, I've fixed it :D

Tried a different (borrowed) wireless card (edimax I think), same problem although the system loaded up a different driver. Did *iwlist scan* again, once again it found my router. I then just loaded up Network settings, typed the name of the router in by hand (I used to have a gNewSense system that scanned for networks at this point, which threw me slightly) and it connected fine. Making me feel like a right ****. Ah well, spent almost all afternoon figuring that one out.

---

### Post by wstout on 2009-02-23
Do you know what type of chip set your wireless card has? Try typing lspci from a terminal and you should get that info. But first if you haven't tried this go to  System -> Administration -> Hardware Drivers, many times Ubuntu will detect your card and download the proprietary drivers automatically for you. Just click enable install and reboot if that is the case.

---

