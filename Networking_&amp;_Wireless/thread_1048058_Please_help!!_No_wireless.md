---
title: "Please help!! No wireless"
date: 2009-01-23
forum: Networking &amp; Wireless
---

### Post by curiousrudy on 2009-01-23
i just installed Ubuntu on my Inspiron 6400, with broadcom wireless 1390 mini card.

the network manager doesn't enable the wireless. 
i have tried EVERYTHING and it is still not working!!!

someone please help, i need to fix this, and i don't want to turn my back on ubuntu, though i am brand new to this game...

if there is one general fix for this, that will definitely help me, i would greatly appreciate the help

---

### Post by ugm6hr on 2009-01-23
Tell us what you've tried (EVERYTHING can me anything).

Which version of Ubuntu are you using?

Do you have a wired connection you can use?

Are you certain it's a 1390 Dell mini-PCI card?

---

### Post by Ayuthia on 2009-01-23
Which version of Ubuntu are you using?  If you are using Intrepid, you should be able to go into System->Administration->Hardware Drivers and activate the Broadcom option.  If you get more than one option, either should work fine.

If you are still having problems, please come back and post the results of lspci -nn and all the options that you have tried.  It will help us determine what needs to be adjusted to make it work right.

---

### Post by jrg_dnn on 2009-01-23
Hi, what you can do is connect your computer to the internet with a cable, restart it, then open System>Administration>Hardware Drivers , and install the driver for your card.

It did not work previously because "Hardware Drivers" needs an active Internet connection to download the proprietary firmware.

Hope this helps.

Jorge Alvarez

---

