---
title: "Ubuntu home network/server"
date: 2010-07-19
forum: Networking &amp; Wireless
---

### Post by cre8ive65 on 2010-07-19
Hi
Recently i convinced my family to make the big switch from mister gates to the OS of the free. After browsing through all the features ubuntu had to offer and i was quite impressed. One feature i never got to work on windows was "Roaming profiles" which from what i understand is also available on ubuntu. After looking throughout the forums i could not find a guide to fit my unique situation. Here is my Big Ubuntu Dream and pardon my Windows Speak but i was in a windows environment since our first computer 10 years ago. prepare for a mouthful

In my house i have: 
1 Acer travelmate 7530 (Wireless)
1 Dell Dimension 2400 (Wireless) {Yes, i know its quite the dinosaur}
1 D-Link DVA G3810BN wireless gateway with nas usb port (Wireless disabled) (1 enabled 4GB usb drive attached)    (Flashed with TELUS, my IPS' firmware)
1 D-Link DIR-601 (Laptop and Desktop connected here) (connected to gateway via ethernet)
1 HP Photosmart C3180 (Connected to desktop)

Now, i want it so that when you log on to either computer, desktop or laptop, the computer accesses the home folder on the 4 gb usb drive attached to the usb port on the gateway, and also, i want the laptop to be able to access the printer on the desktop

again pardon my windows speak, i am running Lucid Lynx desktop edition on both computers. thanks for your time!:D

---

### Post by Iowan on 2010-07-19
You should see the [Server Guide]("https://help.ubuntu.com/10.04/serverguide/C/index.html"). 
[LDAP]("https://help.ubuntu.com/10.04/serverguide/C/network-authentication.html") is one option, but you might be able to come close with [NFS]("https://help.ubuntu.com/10.04/serverguide/C/network-file-system.html"). 
(Wish I could say I'd done either...)

---

### Post by cre8ive65 on 2010-07-20
Thanks for your answer, but I've seen these guides before. If I'm not mistaken, those terminal commands are suppose to be entered on the server and not the client. this guide wold work fine if i was using the desktop as a server, but I'm not. Today i was looking through the menus and i went to users and groups under administration, and i saw under advanced settings, that you could change the location where the home folder for each account was. the only problem with that was i didn't know what "shell" was and I'm afraid the account won't work if i don't know what to do with files. is shell just like preferences of your theme, or is it something more essential. thank you all for your time and i am enjoying Ubuntu very much. I find it more family friendly than windows.

---

