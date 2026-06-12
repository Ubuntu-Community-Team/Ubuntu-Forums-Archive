---
title: "DIsable storage drivers on an aircard."
date: 2010-01-15
forum: Networking &amp; Wireless
---

### Post by wna05 on 2010-01-15
Hello all, 
         I am fairly new to the Linux world, but so far i am loving it. I work for a regional cell phone company, and have recently taken it upon myself to create some documentation that will aid our mobile broadband users with installation of the aircards we carry.I decided to start out with Ubuntu 9.10, and I am using a Novatel mc727. I set it up using the mobile broadband feature that is built in, but I am having a few problems. First I have noticed that once you get the connection created, if you try to edit the settings, an error pops up stating that you are not authorized to do so, before I even get a chance to put in the password. Its not really a big deal, and if it comes down to it you can always delete the connection and start over. However, I have noticed that with the card plugged in, sometimes it can take up to 15 minutes to be recognized as a connection. I got to thinking about it and figured it may have something to do with the fact that this card, and all the cards we carry are seen on windows as a mass storage device. So to test this, i left the card in and rebooted, and of course on reboot, the card was mounted and once i hit eject, it was seen as a modem right away. With that in mind, does anybody know of a simple way do automatically do this? I am trying to document this in such a fashion that our tech support folks who have no knowledge of linux can help out our customers. Thanks for any suggestions or tips..

---

### Post by alexfish on 2010-01-15
hi

First reaction an mc727 means nothing to linux or from where I am sitting

First Step .we need to see how Linux sees the device {the actual device }

step 1. plug in the device . wait for about 10 seconds for the system to settle 

then from the terminal type or copy this code

lsusb

then post the results from the terminal

''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''''

from the internet I have tried to look here to try and get some details of MC727 

**[Ovation *MC727* - NovatelWireless]("http://www.novatelwireless.com/products/ovation/mc727.html")**

? Reply page not found

From the ubuntu device listings nearest match shows as 

 [SIZE=1]Novatel Wireless Ovation MC727 (EVDO Rev-A) 
    USB 
    UNKNOWN[/SIZE]

---

### Post by wna05 on 2010-01-15
Ok, so this is what I get in the terminal

Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 002: ID 1410:5010 Novatel Wireless 
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 047d:102f Kensington Pilot Optical Pro Wireless
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

I should also mention that when going though the mobile broadband setup, it does detect the card as a CDMA modem, which is more than I can say for Win 7.
We also carry the novatel 760 and the franklin 680, which I plan to set up on linux as well. really I am having no trouble at all connecting, it just takes forever for it to be recogized as a modem, just now after pulling it up in the terminal, it took 12 minutes for it to show up in network connections. Maybe I am way off, but I still think it has something to do with the fact that it is showing up as a storage device.
thanks for the help
    Wayne

---

### Post by alexfish on 2010-01-16
hi

Found matching id's  but no  Novatel mc727  nearest match is U727

DefaultVendor=  0x1410
DefaultProduct= 0x5010


Novatel Wireless Ovation MC950D HSUPA
Novatel Wireless Merlin XU950D
Novatel Wireless Ovation 930D
Novatel U727 USB modem (no switching required)

maybe the usb modeswitch could work for you



Could you explain what you were doing when :

1."error pops up stating that you are not authorized to do so"
2."it does detect the card as a CDMA modem"

---

### Post by wna05 on 2010-01-16
The error pops up each time I try to go into network connections and edit the connection details for mobile broadband device. At first I thought i did not have my admin rights set up correctly, but that is not the case. However, I have since discovered that it will not allow me to edit the connection if the aircard is not seen as a modem. In other words, as long as I am connected, or at least have the option to connect, I have no problems.
When I say that the device is recognized as a CDMA modem, when I go in to add or create a new broadband connection, it sees the modem as a novatel broadband modem. Which at least tells me that the necessary drivers are in place.
After further testing, I have confirmed that if the pc is booted with the card already plugged in, I hit eject and within a few seconds i am connected with no problem.
Thanks again

---

