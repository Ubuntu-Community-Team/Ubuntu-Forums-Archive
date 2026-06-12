---
title: "Belkin Bluetooth wireless usb printer adapter on ibex ubuntu"
date: 2009-04-08
forum: Networking &amp; Wireless
---

### Post by pieguy on 2009-04-08
edit: I sent it back.

I'm trying to get ["Belkin Bluetooth wireless usb printer adapter F8T031" ]("http://www.belkin.com/support/product/?lid=en&pid=F8T031&scid=228") working on Intrepid Ibex.  When I try to use the bluez bluetooth applet to add the hardware, it sees it as "BELKIN_PRT_46A193" and fails to automatically connect to it.  When it trys, I notice it brings up the same connection screen that it did for my wireless keyboard where there is a 4-digit number you enter to lock it to that computer but for only a sec before it says it failed.

I would like to know if it will work on ubuntu 8.10 and if it can, how can I set it up?

I tried the instructions [here]("https://help.ubuntu.com/community/BluetoothSetup") and the "hcitool scan" in terminal found it as

Scanning ...
	00:02:72:46:A1:93	BELKIN_PRT_46A193

I tried the "sudo hidd --connect 00:02:72:46:A1:93" and it came back "sudo: hidd: command not found"



edit: I sent it back.

---

