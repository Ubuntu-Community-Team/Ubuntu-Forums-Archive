---
title: "wusb54g and Ubuntu"
date: 2009-08-05
forum: Networking &amp; Wireless
---

### Post by idipous on 2009-08-05
Do even the people preparing the packages for ubuntu test the hardware they include drivers for? 

Sicne Ubuntu 7.10 they include the rt2500usb driver which DOES NOT WORK. We have been saying this in the forums from back then. 

Alhtough it starts with recognising the card as wlan0 and initially, sometimes, connect to the network it seems unbale to keep the connection and disconnects after a while. It keeps doing this over and over again.

The driver they had in 7.04 was working perfectly ( naming the device rausb0). Until 8.04 I could install it after building the rt2570.ko module and then modprobe -r the rt2500usb. Now I am unable to find the rt2570 and the one I had downloaded does not build. Is there anywhere for the rt2570 to be found ready to be builded for Ubuntu 9.04? And please stop using that useless rt2500usb module. IT DOES NOT WORK (at least for the wusb54g v4 wireless linksys card).

 

Excuse my frustration but every time I update to a new version (or even kernel) I face the same issue and now I cannot even solve it the way I used to.

Anyone having a solution to the problem please share it with me.

idipous


I need a way to be able to install the rt2570 driver who is proven to work instead of the rt2500 but when I try to build the driver I get an error with the kill_proc function. I have seen that there is a new rt2570 driver version but I have not been able to find it and donload it. does anyone have it?

---

### Post by n1ym on 2009-11-29
Hi, 

I am sitting here sharing your frustration. Everytime an update comes through I have to completely re-install the drivers for the WUSB54G, and today - after another update - it doesn't work anymore.

Anybody out there who can help? I am about to go and find a dispatched XP computer, get the license number and put Windows onto this thing.

---

### Post by AndrewE on 2009-11-29
Hi guys 
I am new to ubuntu and have the same linksys wusb54g ver4 that doesnt work. It can see the network and tries to connect but no luck, the cable connection is fine but doesnt help us when we both want to use the net we both have 9.10 and only one can use the landline. As I am pretty much computer illiterate when you find the answer could I have my version in language a dummie can understand.

andrew

---

