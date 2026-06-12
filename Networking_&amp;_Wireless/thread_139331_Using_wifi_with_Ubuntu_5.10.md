---
title: "Using wifi with Ubuntu 5.10"
date: 2006-03-03
forum: Networking &amp; Wireless
---

### Post by racsw on 2006-03-03
Hi,
  (This is a repost, but I could not figure out how to delete it in Desktop support)

   We have to go to a major tradeshow in a couple of weeks, and we were going to take our Dell laptop running Ubuntu and use it for our website work, emails, and other online business activities while we were away.
   I am hoping that this version (5.10 BB) will support a WIFI card and allow me to connect simply to the wifi network at the tradeshow, and with the internal modem in the Dell when we're at the motel.
   I have no experience with wifi, so can you guide me as to advice for purchase and install?   We'll probably go to Staples to pick up a wifi card, which will be PCMCIA obviously, but any suggested make?
   Will Ubuntu react to this as a plug-n-play device to be configured with a wizard?

Any advice, general or specific, would be appreciated.

Regards,
Robert

---

### Post by Mez on 2006-03-03
[http://ubuntuforums.org/showthread.php?t=79883](http://ubuntuforums.org/showthread.php?t=79883)

also install network-manager and run "nm-applet" for quick wifi card changes..

best to install with the wifi card plugged in too.

---

### Post by racsw on 2006-03-04
I installed the network manager, my new Netgear WG511T WIFI card, but I have no idea where the "nm-applet" is located.  Can you tell me where I can find it?

On a secondary note, I have absolutely no wifi experience, so is there a basic setup guide to get it going and test?

Because we will have both modem and wifi access, we will need to switch between them depending where we are located.  Is there a nice GUI for doing this?

Thanks,
Robert

---

### Post by djroadrash on 2006-03-05
hi, i guess u have never used this card on ubuntu before, it sounds that way, so the easy way (if it works and u are lucky) is to go to system/administraton/networking, click on it and the next window that comes up will show u the icons of the networking devices that the machine is recognizing out of the box for u. if you see the ethernet card icon then u are lucky and just have to activate it . so select, go to properties and put your network settings there if any (wep key etc..) and clik ok and activate. check with your browser and see if it works, if any of the steps above fail, then u have to use terminal to get on line. if this is the case, go to applications/systemtools/ terminal and click on it.
 get this code and paste it on the terminal
sudo lspci
sudo dmesg
when u get this then you will know what modules (drivers) and what chips u have in your card, and modem in the computer start there. 
good luck
:KS

---

