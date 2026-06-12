---
title: "DLink wireless not working"
date: 2010-07-10
forum: Networking &amp; Wireless
---

### Post by Johnley on 2010-07-10
hey there forum! i was recently given an old dell dimension 4100, and the previous owner had ordered it with the works... of 2002. so i was wondering if anyone had ever used a DWL-520+ PCI card in Ubuntu 10.04? i had an old 8.04 LTS CD that came with my dell mini, and the wireless worked fine with the live CD. i haven't gone back to 8.04 yet, but if there is no fix, i will probably have to. i'll attach a photo of the card, i'm not sure what all information you guys might need. 

thanks in advance!

[http://lh5.ggpht.com/_rRkOumikFFU/TDgf2-X937I/AAAAAAAAAR8/ya_piHuAxSw/s1024/DSC_0003.JPG](http://lh5.ggpht.com/_rRkOumikFFU/TDgf2-X937I/AAAAAAAAAR8/ya_piHuAxSw/s1024/DSC_0003.JPG)

[http://lh6.ggpht.com/_rRkOumikFFU/TDgf3RTghlI/AAAAAAAAASA/fVsBBUms7c4/s1024/DSC_0002.JPG](http://lh6.ggpht.com/_rRkOumikFFU/TDgf3RTghlI/AAAAAAAAASA/fVsBBUms7c4/s1024/DSC_0002.JPG)

---

### Post by flash63 on 2010-07-10
Hello,
the Module acx111 is since Ubuntu 9.04 no longer included in the system.

More Information about that you can find here [http://www.linuxwireless.org/en/users/Drivers/acx1xx](http://www.linuxwireless.org/en/users/Drivers/acx1xx)

You must use Ndiswrapper. This makes also WPA1 encryption possible.

32bit Driver here [http://forum.ubuntuusers.de/topic/probleme-mit-wlan:-dwl-g650%2B/2/#post-1271405](http://forum.ubuntuusers.de/topic/probleme-mit-wlan:-dwl-g650%2B/2/#post-1271405)

---

### Post by bkratz on 2010-07-10
Just some more supporting info on that driver

[http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx](http://ubuntuforums.org/showthread.php?t=1404097&highlight=acx)

---

### Post by frisket on 2010-08-15
> **flash63 said:**
> Hello,
the Module acx111 is since Ubuntu 9.04 no longer included in the system.

More Information about that you can find here [http://www.linuxwireless.org/en/users/Drivers/acx1xx](http://www.linuxwireless.org/en/users/Drivers/acx1xx)

You must use Ndiswrapper. This makes also WPA1 encryption possible.

32bit Driver here [http://forum.ubuntuusers.de/topic/probleme-mit-wlan:-dwl-g650%2B/2/#post-1271405](http://forum.ubuntuusers.de/topic/probleme-mit-wlan:-dwl-g650%2B/2/#post-1271405)

I downloaded the driver (thanks for the link), and installed ndisgtk to manage the installation. It claims to have installed the driver, but when I reboot, I still don't have any mention of wireless in my network applet.

I have a wired connection working fine, but on any machine with a network card, there is usually an entry "Enable Wireless Network" when you right-click on the Network applet in the top RH panel.

How do I tell my system that NDIS is installed and the driver is installed, and to add wireless networking to the options?

---

