---
title: "Lost wlan0 and wireless hardware not listed with lspci"
date: 2009-01-09
forum: Networking &amp; Wireless
---

### Post by keplerspeed on 2009-01-09
I have a broadcom BCM4311 wireless card. It has always worked fine with the b43 driver or ndiswrapper.

HOWEVER I updated my system last night (2.6.27-7-generic ubuntu 8.10)

Then rebooted.

iwconfig would not show wlan0, but it did show pan0, which I have gathered is a bluetooth extension.

lspci shows only my ethernet and NOT my wireless hardware.

I have now removed all the bluetooth packages as I dont need them. pan0 has now disapeared. But my wireless card and wlan0 are still missing.

I booted into 3 different live cd's and the same issue exists. Can i assume I have a hardware issue? It seems like the wireless card is not connected. But it should be, my laptop hasnt moved at all, why would it just 'disconnect' itself??

cheers.

---

### Post by cwbar_1 on 2009-01-09
Your card will work with the Broadcom STA Wireless driver.  Is this driver showing up in your restricted drivers list? System> Administration> Hardware Drivers.  If it is, activate it.  Reboot, give it a couple of minutes, and it should tell you "wireless networks available."  Left click on the network "steps" and choose and configure your  network.

---

### Post by keplerspeed on 2009-01-09
I was using the STA driver. I have no issues setting up drivers are firmware. My issue is that it appears like my wireless card is not detected at all, I mean hardware detection, as though its not connected. The kenel thinks it doesnt exist. However it is connected. Agh!

---

### Post by cwbar_1 on 2009-01-09
I must have misunderstood.  As long as the wireless works, I'm not sure I would be concerned.  My iwconfig shows 
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11  Nickname:""
          Access Point: Not-Associated   
          
pan0      no wireless extensions.

However, my wireless works!  

Does your card show up under lshw?

---

### Post by keplerspeed on 2009-01-10
No, i have no wireless, it doesnt work as there is no wlan0 and wireless card doesnt appear under lspci and lshw.

---

### Post by keplerspeed on 2009-05-28
Ok it was a hardware issue with compaq laptop: [http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01480071](http://h10025.www1.hp.com/ewfrf/wc/document?lc=en&dlc=en&cc=us&docname=c01480071)

"The following symptoms apply to Compaq Presario F500 notebooks:

    *
      The notebook does not detect wireless networks and the wireless adapter is not detected in the Device Manager."

---

### Post by farleonhart on 2009-10-23
did u manage to work this out? or did u just let HP repair your laptop? cos im now having d same problem wit u.. the network card just suddenly got "disconnected" from my laptop.. n dis occured after i messed around with wammu..(i forced it to quit while it was searchin for k810 driver) at first i thought ubuntu caused the problem, so i uninstall ubuntu and install windows.. No luck though, windows also doesnt detect my Atheros ar5007eg.. so if u have solution to dis prob, pls share wit me.. thanks in advance

---

### Post by bkratz on 2009-10-23
> **farleonhart said:**
> did u manage to work this out? or did u just let HP repair your laptop? cos im now having d same problem wit u.. the network card just suddenly got "disconnected" from my laptop.. n dis occured after i messed around with wammu..(i forced it to quit while it was searchin for k810 driver) at first i thought ubuntu caused the problem, so i uninstall ubuntu and install windows.. No luck though, windows also doesnt detect my Atheros ar5007eg.. so if u have solution to dis prob, pls share wit me.. thanks in advance



It appears HP is having problems with wireless on some laptops please look here

[http://www.theinquirer.net/inquirer/news/1032183/hp-admits-wireless-laptop](http://www.theinquirer.net/inquirer/news/1032183/hp-admits-wireless-laptop)

---

### Post by keplerspeed on 2009-11-07
Unfortunately my lappy was out of waranty, not worth the money to fix it so I bought a usb wireless adapter. I am not impressed with such a hardware failure, and compaq didnt want to know about it.

---

