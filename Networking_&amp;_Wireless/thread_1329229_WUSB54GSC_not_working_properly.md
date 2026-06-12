---
title: "WUSB54GSC not working properly"
date: 2009-11-17
forum: Networking &amp; Wireless
---

### Post by gzipper on 2009-11-17
Hello
I installed 9.10 DE x64. Using the 2.6.31-14-generic kernel and WUSB54GSC v1 wifi. If i try using the rndis_wlan driver it repeatedly tries to connect do the device but fails. Using atm the ndiswrapper and vista 64 drivers to run the card (mostly since I cant find the XP64 ones) but it behaves erratically and it doesnt detect my Linksys router. Though it finds other networks fast but it can take an hour to find my own "compatible" network. I blacklisted the rndis_wlan driver to make ndiswrapper to work.
If the device is connected to the machine during boot it wont boot at all and generally its a very slow booting, there is a long delay even before the splash screen.

Is there anything I can do to make rndis_wlan to work instead of using the ndiswrapper and make it boot without having to disconnect the device each time I boot into Ubuntu. And is there a difference between using Xp or Vista drivers (cant extract the XP ones from the driver package from Linksys). I figured that maybe a rebuild of the kernel would maybe solve the boot problem but id rather not atm.

TIA

---

### Post by gzipper on 2009-11-22
As I had upgraded from 9.04 to 9.10 I got fed up with the problem and reinstalled from scratch. Turned out the update was somehow currupt so now it works with rndis_wlan module. Also fixed a numeros of problems, and introduced a few new ones. I guess one cant get it all.

---

