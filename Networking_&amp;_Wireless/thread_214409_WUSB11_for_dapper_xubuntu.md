---
title: "WUSB11 for dapper xubuntu"
date: 2006-07-12
forum: Networking &amp; Wireless
---

### Post by greenwoodman on 2006-07-12
I am having no luck with connecting to my home wireless network with the WUSB11.  It is recognized by the network manager, but there is no connection.  I tried to make it work using these instructions: https://wiki.ubuntu.com/WifiDocs/Device/LinksysWUSB11?highlight=%28wusb11%29"

after step 13 > Type (always ignore the " "): "sudo apt-get install build-essential linux-headers-`uname -r`". (Note the backticks surrounding uname -r.)This will upgrade some stuff. You will be asked to insert your Ubuntu boot disk, put your password when prompted, and voila. If you have already updated it, a message saying "you have the newest version" will appear: OK so far.:

I got > Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package linux-headers-uname -r


in the terminal.

I get the feeling that because these instructions are for breeze GNOME ubuntu and im using dapper xubuntu that they might be useless.  Please help.

Thank you.

---

### Post by Dr. Nick on 2006-07-12
look on the bottom of your card and tell me which version it is. It should be in a small box in the top left corner after the model number. I have a v3 and have gotten it to work with the built in prism2 drivers and ndiswrapper. If you have a v3 I can surely help you some, though if you have different version it will be different setup instructions. The wusb11 have alot of caritions between versions :(

---

### Post by greenwoodman on 2006-07-12
it is version 2.6, and I got it to work without any setup on breezy ubuntu, only that ubuntu was incredibly slow on my box so it barely worked at all.

---

### Post by Dr. Nick on 2006-07-12
well then I cant be of direct help :(

Though it appears to work as evidenced by a quick wusb11 v2.6 search

[http://ubuntuforums.org/showthread.php?t=211854&highlight=wusb11+v2.6](http://ubuntuforums.org/showthread.php?t=211854&highlight=wusb11+v2.6)
[http://ubuntuforums.org/showthread.php?t=160066&highlight=wusb11+v2.6](http://ubuntuforums.org/showthread.php?t=160066&highlight=wusb11+v2.6)
[http://ubuntuforums.org/showthread.php?t=29554&page=2&highlight=wusb11+v2.6](http://ubuntuforums.org/showthread.php?t=29554&page=2&highlight=wusb11+v2.6)

and probably a few more tutorials. Let me know if you need more help with any of it, I may be able to help, Or someone else probably knows what to do. 

Though It appears its possible to get that rev working just fine

---

