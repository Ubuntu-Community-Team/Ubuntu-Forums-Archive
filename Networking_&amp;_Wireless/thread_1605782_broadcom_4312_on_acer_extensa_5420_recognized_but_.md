---
title: "broadcom 4312 on acer extensa 5420 recognized but not connecting"
date: 2010-10-25
forum: Networking &amp; Wireless
---

### Post by sevenenemy on 2010-10-25
i just got ubuntu yesterday and had to play around with some settings and the fw-cutter tool to get my wireless working and it was...although i upgraded the kernel to 2.6.32-25-generic...and it stopped working. the simple solution is to use the previous kernel version...the wireless works there, but thats just not good enough for me 8) ... it recognizes my card is there it just wont connect. originally i was using b43 driver and now it does not show in the system>hardware drivers list only the sta driver does, although when i try to install and activate it i get the error message "sorry, installation of this driver failed. please have a look at the log file for details: /var/log/jockey.log" please help. oh for the love of god please help! i've been at this for hours and all the solutions are not working. any ideas would be greatly appreciated. thanks. hunter.

---

### Post by sevenenemy on 2010-10-26
[QUOTE=sevenenemy;10026159]i just got ubuntu yesterday and had to play around with some settings and the fw-cutter tool to get my wireless working and it was...although i upgraded the kernel to 2.6.32-25-generic...and it stopped working. the simple solution is to use the previous kernel version...although that version no longer works ... it recognizes my card is there it just wont connect. originally i was using b43 driver and now it does not show in the system>hardware drivers list only the sta driver does, although when i try to install and activate it i get the error message "sorry, installation of this driver failed. please have a look at the log file for details: /var/log/jockey.log" please help. oh for the love of god please help! i've been at this for hours and all the solutions are not working. any ideas would be greatly appreciated. thanks. hunter.

---

### Post by sevenenemy on 2010-10-26
ok so i marked all the broadcom drivers for uninstall and then rebooted and re installed... it worked and the wireless worked for about 5 mins and then would not load pages after that. i rebooted again and it did not work again, after trying the uninstall and reboot method again i re-installed the drivers and this time it didnt work. gah.

---

### Post by TBABill on 2010-10-26
Normally for the Broadcom 4312, same as in a couple of my computers, you should be using the STA driver for best performance. If you uninstall all the drivers you already have loaded, you should be able to plug into the router, click system>>administratin>>hardware and select the STA driver. That one works great with the 4312.

---

### Post by sevenenemy on 2010-10-28
I've tried the to uninstall reboot and reinstall three times and it worked once but it didn't stick after reboot and now continues not to work. Also when I try to activate the sta driver the installation fails and tells me to look at a .log

---

### Post by sevenenemy on 2010-12-24
fixed just upgrade to 10.10

---

