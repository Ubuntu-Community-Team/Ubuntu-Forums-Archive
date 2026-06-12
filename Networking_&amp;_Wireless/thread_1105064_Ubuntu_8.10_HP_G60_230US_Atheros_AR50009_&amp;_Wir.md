---
title: "Ubuntu 8.10 HP G60 230US Atheros AR50009 &amp; Wirelss connectivity issue"
date: 2009-03-24
forum: Networking &amp; Wireless
---

### Post by shankar_hokie on 2009-03-24
I bought this laptop in january. It is a HP G60 230US running Vista premium. 32 bit. It has the dreaded Atheros AR5009 WLAN card. Had some wireless conenctivity issues and it turned out to be my old mUSR modem. Have no issues wirh a new DLINk D615 under Vista. I recently downloaded and installed Ubuntu 8.10. Immediately after I installed it, I was able to connect to my home wireless network. Since then, I have lost that abilioty. Ubuntu sees the network, and asks for a password, but just keeps cycling and quites in the end. I fl=ollowed some of the instructions on the other threads. I now have 2 version of Ubuntu 8.10. I also added the ath9 string in the /etc/modules file. No success yet.

Can you please point me to the next steps ??

---

### Post by ebug on 2009-05-07
Please try 

[http://ubuntuforums.org/showthread.php?p=7218364](http://ubuntuforums.org/showthread.php?p=7218364)

I upgraded to jaunty. atheros drivers are already included.
I followed madwifi, ndiswrapper thing but they seems not working for me. So when I read from one forum that atheros drivers are included in intrepid, i assumed these drivers are also included in jaunty. Since I did too much madwifi and ndiswrapper installtion, I opted to fresh install and find out if the wifi will work "out-of-the-box".

So, from fresh install, I updated the packages (lan cable connected), make some clean up and install graphics driver etc etc. After that, I removed the lan cable and press the wifi button as I mentioned in [http://ubuntuforums.org/showthread.php?p=7218364](http://ubuntuforums.org/showthread.php?p=7218364)

(try to restart if this doent work the first time)

Waking up the wifi is almost like waking up somebody from slumber using the tip your finger. Push the button about one second then release, then after 2 to 3 seconds, the button turns to blue.

As for now, that is my temporary solution. I hope somebody will have a better one. I would like to know how to make the button light up to blue automatically without intervention after logon. 

Please anyone...

---

