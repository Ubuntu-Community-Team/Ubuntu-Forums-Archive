---
title: "Netgear Wireless Adaptor Problem"
date: 2011-02-02
forum: Networking &amp; Wireless
---

### Post by darku4004 on 2011-02-02
How do I install my Netgear Wireless Adaptor on ubuntu 10.10? it tries to search for it but doesn't find it.

---

### Post by khamil8686 on 2011-02-02
alot of hardware will work by just plugging it into your computer with linux, do you mean when you plug it in you see that it cant connect to your wireless network or when you plug it in it doesnt do anything?

---

### Post by darku4004 on 2011-02-02
I downloaded the software that came with it. the next step was to plug in the adaptor and click next. when I plug it in and click next, it saies it is searching for the adaptor. when it is done, it saies no adaptor is found.

---

### Post by Dans564 on 2011-02-02
what netgear do u have specifically

---

### Post by darku4004 on 2011-02-02
It is Netgear N300 Wireless USB Adapter

---

### Post by khamil8686 on 2011-02-02
what software did you download for this wireless adapter? the only software i can find is windows drivers and alot of linux users seem to have trouble getting this wireless adapter to work so people have used the ndiswrapper program so they can download the windows driver and use it on ubuntu

---

### Post by darku4004 on 2011-02-02
I just used the disc that came with the adapter.

---

### Post by khamil8686 on 2011-02-02
it had linux drivers on the cd? usually stuff included with hardware sold is windows drivers, and their website which should have downloads of all the drivers it distributes only had a windows driver that i saw

---

### Post by darku4004 on 2011-02-02
im not sure, it only came with the disc and no paper work.

---

### Post by khamil8686 on 2011-02-02
try just plugging in the adapter to a usb port and then in the top right corner of your linux desktop there will be a system tray and there should be an icon in there for Network Manager (should be 2 little computers or an icon with some bars on it) open that and then you should be able to search for and configure your wireless network to connect to it

if there is no icon in your system tray that opens up a Network Connections window try pressing alt+f2 and typing in nm-applet and hit enter and see if an icon appears in your system tray

if youre using the software on the disc and its a .exe file im not sure how you got it to run in linux unless you have wine installed or something

---

### Post by darku4004 on 2011-02-02
yes i have wine. when i click the little bars at the top right, i can get to a window that has some catigories, do i just click wireless and add?

---

### Post by khamil8686 on 2011-02-02
yes try clicking wireless and clicking add

---

### Post by darku4004 on 2011-02-03
it takes me here

---

### Post by darku4004 on 2011-02-03
what do i do next?

---

### Post by khamil8686 on 2011-02-03
i forgot the automatic thing you can do :P click on the icon with the red exclamation mark in the top right and see if it lists any wireless networks you can connect to, if you see the one you want to connect to listed then click it and enter any security info it asks you for if theres security and it should automatically connect, if that doesnt work you can try filling in the fields of that editing wireless network connection box you had a screenshot of, fill in the SSID which is the name of the wireless network you want to connect to, and then click the wireless security tab and fill in what kind of security the router uses for its wireless network and the security key if it has one, then hit ok and the connection should automatically connect, if it doesnt you can try double clicking the connection in the network connections box or click the icon on the top right and choose the connection you just created from the drop down box

---

### Post by darku4004 on 2011-02-04
i got it. thanks for all of your help!!:lolflag:

---

### Post by khamil8686 on 2011-02-04
awesome, good to hear you got it working :)

---

