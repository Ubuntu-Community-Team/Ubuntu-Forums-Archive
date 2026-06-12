---
title: "Wireless on Compaq Presario CQ40-551TU"
date: 2010-06-07
forum: Networking &amp; Wireless
---

### Post by Christopher Richard Yu on 2010-06-07
Hi,
 
I need help on my wireless regarding that it will not connect to the internet. I tried switching the button for wireless on, but it does not function over in Ubuntu 10.04. It funtions properly in my Windows 7.
 
Next step I did was to go to the terminal and:
 
sudo gedit /etc/NetworkManager/nm-system-settings.conf
 
I managed to edit the Managed from 'false' to 'true'
I used root username to change the file.
 
Still nothing happened.
 
Finally I did iwconfig.
It showed that under wlan0, Power Management=off
In order to turn it on, I tried 
 
ifconfig wlan0 up  <---- this line said that permission denied
 
tried this as well
 
sudo ifconfig wlan0 up  <----- this line nothing happens as well
 
So my plea for help is that, HOW DO I TURN ON MY WIRELESS LAN? because it seems that the driver is installed correctly and that Ubuntu recognizes it because, i forgot the command though, but it says Broadcom Wireless.

---

### Post by rajeev1204 on 2010-06-30
Iam bumping this, considering user has only 1 post and probably went back to windows.

---

