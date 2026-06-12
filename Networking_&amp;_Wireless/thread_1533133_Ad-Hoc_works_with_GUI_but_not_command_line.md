---
title: "Ad-Hoc works with GUI but not command line"
date: 2010-07-17
forum: Networking &amp; Wireless
---

### Post by mbilloo on 2010-07-17
I have two Roboards that need to communicate with one another. I have sucessfully installed Ubuntu 9.04 using the 386 kernel based on instructions found online.

I can use the GUI to set up an Ad-Hoc network using one Roboard ("Create New Wireless Network"), call it Manet, and connect to "Manet" using the GUI on the other Roboard and ping/ssh between the boards. 

However, when I try to create the same wireless network using the command line using:

ifconfig wlan2 down
iwconfig wlan2 key off essid 'Manet' channel 5 ap any
ifconfig wlan2 up

I don't see any entry in iwconfig under "Cell". It keeps giving me "Not Associated"

When I try to enter the same information on the other Roboard to try to connect to the network, it doesn't connect and under iwconfig, I don't even see any entry for ESSID. 

Could somebody please tell me why it works when I use the GUI and not the command line. 

Thank you,

---

### Post by ario on 2010-10-17
> **mbilloo said:**
> I have two Roboards that need to communicate with one another. I have sucessfully installed Ubuntu 9.04 using the 386 kernel based on instructions found online.

I can use the GUI to set up an Ad-Hoc network using one Roboard ("Create New Wireless Network"), call it Manet, and connect to "Manet" using the GUI on the other Roboard and ping/ssh between the boards. 

However, when I try to create the same wireless network using the command line using:

ifconfig wlan2 down
iwconfig wlan2 key off essid 'Manet' channel 5 ap any
ifconfig wlan2 up

I don't see any entry in iwconfig under "Cell". It keeps giving me "Not Associated"

When I try to enter the same information on the other Roboard to try to connect to the network, it doesn't connect and under iwconfig, I don't even see any entry for ESSID. 

Could somebody please tell me why it works when I use the GUI and not the command line. 

Thank you,

Me too! I followed the method in Ubuntu community help, but it will just turns off the blinking LED on my device. Nothing happens!

---

