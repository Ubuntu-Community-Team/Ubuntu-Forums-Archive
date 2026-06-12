---
title: "Zonet ZEW1642s wireless PCI adapter"
date: 2011-04-19
forum: Networking &amp; Wireless
---

### Post by andrewholzman on 2011-04-19
hello. i'm a total ubuntu newbie(installed yesterday!), and i cant seem to get my network card to work.
i have an _802.11n Zonet ZEW1642S Wireless PCI Adapter_, and it came with a cd that contained the drivers necessary for installation on windows. i understand that the drivers are not compatible with ubuntu, but is there any method that i can get my wireless card to work? if so could someone explain (in newbie speak, sorry!) how to do it?
Thanks!802.11n Zonet ZEW1642S Wireless PCI Adapter802.11n Zonet ZEW1642S Wireless PCI Adapter

---

### Post by danpaluska on 2011-04-29
i have been having trouble with this one as well.

start here:
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

but i got stuck on not being able to find a windows .inf file. 
zonet has a .exe file on their site. maybe if you have a windows box and you run the .exe you can get the .inf file from the windows box and then transfer thatn to the linux box and run ndisgtk to install that driver.

and if you do that, please post the .inf file for me too. ;)

thanks!
-dan

---

