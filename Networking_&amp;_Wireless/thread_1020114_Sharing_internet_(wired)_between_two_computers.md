---
title: "Sharing internet (wired) between two computers"
date: 2008-12-23
forum: Networking &amp; Wireless
---

### Post by JonJ678 on 2008-12-23
Hey. In truth I don't know enough of the terminology to get anything useful from google on this. 

I have one desktop computer with two ethernet ports, eth0 and eth1. 
eth0 is connected to a router, hence to the internet. eth1 is connected by crossover cable to the only ethernet port on a laptop. 

How do I get the laptop online with this set up? 

Using intrepid. Fully updated on the desktop, currently a livecd on the laptop. 

Thank you

---

### Post by jpaulb on 2008-12-23
It would probably be simpler to plug the laptop into the router also, assuming the router has more than one lan port.

---

### Post by JonJ678 on 2008-12-23
Unfortunately the other ports on the router are occupied, otherwise that would very much be a simpler solution :)

edit:
I've now tried this with the laptop running XP. Connects fine, but also no internet. This rules out faulty cable, disabled network adapters etc. Ubuntu still no connection. 

The options in network manager don't mean very much to me unfortunately, but I assume the problem is that both adapters are expecting to connect to a router. What settings do I change to get them to connect to each other directly instead?

---

### Post by jpaulb on 2008-12-23
Last time I did that was years ago with I think SuSE 4.1 which had a setup wizard for multiple cards. I can't remember how I did that.
At the time I was using the computer as a router feeding a switch.

Sorry I can't help.
try this

[http://ubuntuforums.org/showthread.php?t=780024](http://ubuntuforums.org/showthread.php?t=780024)

---

### Post by superprash2003 on 2008-12-24
you could use firestarter ( sudo apt-get install firestarter ) it has an Internet connection sharing(ICS) feature.. if not you could do it this way too [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by JonJ678 on 2009-01-07
That last link was fantastic. Thank you enomously :)

---

