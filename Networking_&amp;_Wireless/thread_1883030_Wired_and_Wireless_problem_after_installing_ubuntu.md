---
title: "Wired and Wireless problem after installing ubuntu 11.10"
date: 2011-11-18
forum: Networking &amp; Wireless
---

### Post by Avoo on 2011-11-18
HI ...I'm beginner on forums,so sorry for anything,and sorry for bad english...I have  **[SIZE=3][B]Atheros AR8132**[/SIZE][SIZE=3]  and   wireless BCM4312 [/SIZE][/B]... at first we will go to Terminal (Alt-Ctrl-t)..and type
[SIZE=3]*ifconfig -a*[/SIZE] 
then type 
[SIZE=3]*dhclient eth0*[/SIZE] 
now we have wired network,BUT after restart we will lose it...ok then for wireless access type
 [SIZE=3]*apt-get update*[/SIZE]
[SIZE=3]*apt-get install firmware-b43-lpphy-installer*[/SIZE]
then we remove existing bcmwl kernel source
[SIZE=3]*apt-get remove bcmwl-kernel-source*[/SIZE]
OKKKK...after reboot we will have wireless Internet ...now for wired internet we will edit Network Manager..Type
[SIZE=3]*gedit  /etc/NetworkManager/NetworkManager.conf*[/SIZE]
it will look like this 
[SIZE=3][B][main]
plugins=ifupdown,keyfile

[ifupdown]
managed=true[/B][/SIZE]
save and close the file .
now go to Ubuntu software center and install  Wicd Network Manager . . .lunch the program ...from preferences click on "Always switch to a wired connection when available"...and now u can reboot your Ubuntu...After reboot U WILL HAVE WIRED AND WIRELESS INTERNET !!! GOOD Luck !!

---

### Post by BillyBoa on 2011-11-18
I didn't try your solution but looks good.

In any case mark the thread as UNSOLVED to attract more attention because otherwise no one is going to pay attention.

---

