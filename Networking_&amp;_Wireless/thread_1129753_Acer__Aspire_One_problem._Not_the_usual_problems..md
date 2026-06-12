---
title: "Acer  Aspire One problem. Not the usual problems."
date: 2009-04-19
forum: Networking &amp; Wireless
---

### Post by sotvomike on 2009-04-19
Ok, so I had Ubuntu Intrepid running on my Acer Aspire One netbook. I used the madwifi solution to get the wifi going. Been using it like that since January. Now, I updated to the Jaunty beta about 2 weeks ago. Everything was running just fine. THEN, I took my laptop some place that there was no network available. Network Manager kept insisting to connecting to my network until I finally cancelled it. When I got home, it was acting weird. It acted like it couldn't connect to my network (kept asking for the WEP). After several minutes of this, I cancelled out and rebooted.

This is where it really freaks out. When I reboot, there is an X over the signal bars on the top. When I click on it, Wired and Wireless options are greyed out. Network Manager does not even pop up to ask for password to unlock the keyring. I do the whole madwifi routine again, to no avail. I try Firestarter and it says "The device wlan0 is not ready". So I reboot to Windows XP. Same thing. The Windows network manager says "there are no networks in range. Make sure your wireless device is turned on." I slide the switch and the WLAN light lights up, like it's sending and receiving. Still no networks. Reboot back to Ubuntu.

Back in Jaunty, having same problem. Do some research and find this article: [https://bugs.launchpad.net/ubuntu/+s...ux/+bug/319825](https://bugs.launchpad.net/ubuntu/+s...ux/+bug/319825)
I try the "iwlist wlan0 scan" but it says interface does not support scan. I try the "rmmod acer_wmi" solution in the article but nothing happens. Thinking all hope is lost, the computer connects to my network and sees the other surrounding networks without Network Manager popping up and asking for a password, and the Wireless option in the menu is still greyed out. Appears to me there is some sort of conflict, with Network Manager and Windows thinking the network card is turned off or not working but in reality it is and working without their knowledge, if that makes sense.

So, I know it is probably silly to try to get help fixing something that is working, but it is not working as it should. Would like some help on this. please give me some instructions to run in terminal so I can post the output on here.

Thanks again, my friends!

---

### Post by superprash2003 on 2009-04-19
the firestarter error occurs if your interface ( wlan0) doesnt get an ip address. post output of ifconfig from the terminal

---

