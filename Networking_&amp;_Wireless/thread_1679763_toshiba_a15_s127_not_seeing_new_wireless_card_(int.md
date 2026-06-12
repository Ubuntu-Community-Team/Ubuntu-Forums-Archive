---
title: "toshiba a15 s127 not seeing new wireless card (internal)"
date: 2011-02-01
forum: Networking &amp; Wireless
---

### Post by luna_tic on 2011-02-01
I am completely new to ubuntu. so please keep responses as simple and direct as possible, please. I have a toshiba a15 s127. it didn't have a wireless card so i ordered one and installed it myself. however, my computer is not seeing the wireless card and i don't know what driver i need because the card itself didn't come to me in a box, so i am not sure what brand it is. All i know is that it is an original part. 

On another note, when i go to network settings and try to config my wireless settings, i do not know what number to put in the BSSID field. (thinking i use the wireless card's MAC address, but ????) and don't know if i use the wireless card's MAC adress or the wireless router's MAC address or the Modem's MAC address in the actual field for the MAC address. 
( i know, i know, i sound totally clueless--well, i am!)
{note: the wired network works fine.}

How do i get my computer to see the wireless card and how do i configure my computer once it does see the card? 

thank you sooooo much if you can help me! i know i will love ubuntu if i can just figure out how to config my computer and get my wireless working.

 :confused:

luna_tic

---

### Post by grahammechanical on 2011-02-01
I am assuming that you are using Ubuntu 10.10. Things will be a little bit different if you are using an older version.

Do you see the network icon? As you are connected by cable to the modem/router, the icon should look like two arrows going in opposite directions. Left click the icon. Do you see any available wireless networks. If you do, then this means that your wireless card or adapter is recognized and is working for it has scanned the neighbourhood and detected some wireless networks.

Is you wireless network in that list? If so, click on it and enter the wireless key when you are asked to authenticate the connection. Network manager will do the rest. You may want to right click the icon and edit the connection to Connect automatically.

What if there are no wireless networks available? May be your wireless card is not switched on. Right click the icon and see if the line Enable wireless has a tick mark against it. If it does not, then select it and click on it.

What if the line Enable Wireless is greyed out and you cannot click on it. This could mean that you needed to activate a driver for your card. Go to System>Administration>Additional Drivers and see if any drivers are on offer.

I am under the impression that the Ubuntu developers are working towards giving us an OS that can be set up by people like us who are a bit clueless and do not have a university degree in computer programming. This is why I like Ubuntu.

Regards.

---

