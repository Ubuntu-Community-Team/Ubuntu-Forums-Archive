---
title: "Wireless drops after two minutes and won't come back"
date: 2009-01-24
forum: Networking &amp; Wireless
---

### Post by lobralleo on 2009-01-24
Dear all,

I have a HP Pavilion dv6560 laptop with an Intel PRO/Wireless 3945 802.11a/b/g card. Wireless connection has never been a problem with *buntu, under any circumstances and with every kind of encryption (I have used a WPA-encrypted wireless at work on a daily basis for a long time). However, when I try to connect to my home wireless router, I cannot manage to have a stable connection.

The wireless signal only appears in the list of available networks every now and then, and when I can manage to detect and catch it, the connection drops after just a couple of minutes and I have to restart the system, only to get two more minutes of wireless before a new freeze. However, for these two minutes, the connection is fine.

This is true under Ubuntu and Kubuntu (both Hardy and Intrepid), Fedora 10 and Opensuse 11. Oddily enough, only under Ubuntu Intrepid (i.e. using Gnome) the signal is relatively stable, but after about half an hour my PC freezes (touchpad, keyboard and multimedia keys are all stuck) and does not even boot until I remove the battery, unplug the power and discharge the residual static charge. I never had to do that in one and half year since I bought the laptop.

The router is a Cisco/Syslink WRT160N and the signal is WPA-encrypted. I know for sure it is working, since the very same PC running Vista can connect flawlessly, as well as a MacBook running OSX. If I directly plug the PC to the router with an ethernet cable, the connection is perfect. Also, search on the net revealed no apparent conflict with linux for this router.
I must mention that the wireless card can detect about thirty or more WPA-encrypted network signals (basically everyone in the building has a wireless router), thus I am wondering if it could somehow get "lost".

Sorry for the long post and thanks in advance!

---

### Post by sralpert on 2009-02-08
I have the same problem on 8.10.  When my box boots up, the connection works fine (using wireless w/ 128-bit WEP).  After a couple of minutes the connection drops and a get a prompt to reconnected.  The WEP key is correct but a connection can't be established.  If I reboot the computer, it starts up again for another two minutes!   grrrr....

help!

/steveA

---

### Post by apratsunrthd on 2009-05-01
Same situation here.  I've tried wicd and adding disable_hw_scan=1 to about 3 different files.

---

