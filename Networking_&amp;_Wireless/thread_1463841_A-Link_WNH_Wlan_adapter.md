---
title: "A-Link WNH Wlan adapter"
date: 2010-04-27
forum: Networking &amp; Wireless
---

### Post by RedStar81 on 2010-04-27
Hello all

I wanted to take a look what is linux today and installed ubuntu to my desktop. First thing i noticed is that i'm not able to use my WLAN adapter. A-Link is providing drivers but i could not figure it out how to install those. Readme is includet in package and it says i need to build these drivers. I opened terminal and path where i extracted drivers and tryid to run command make

This is what i got. What should i do?
juha@Ubuntu:~$ cd /media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009
juha@Ubuntu:/media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.31-14-generic'
  CC [M]  /media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009/ieee80211/ieee80211_module.o
/media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009/ieee80211/ieee80211_module.c: In function â€˜alloc_ieee80211_rslâ€™:
/media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009/ieee80211/ieee80211_module.c:128: error: â€˜struct net_deviceâ€™ has no member named â€˜hard_start_xmitâ€™
/media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009/ieee80211/ieee80211_module.c: In function â€˜store_debug_levelâ€™:
/media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009/ieee80211/ieee80211_module.c:291: warning: comparison of distinct pointer types lacks a cast
make[2]: *** [/media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009/ieee80211/ieee80211_module.o] Error 1
make[1]: *** [_module_/media/WD500g/Drivers/ubuntu/a-link/rtl8190p_linux_2.6.0010.0525.2009/ieee80211] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.31-14-generic'
make: *** [all] Error 2


and running iwconfig gives me this
lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

This is the card i have:
[http://www.a-link.com/WNH.html?id=8wJ7wEe9](http://www.a-link.com/WNH.html?id=8wJ7wEe9)

Juha

---

### Post by Mayfairy on 2010-05-11
I have the exact same card and I could make it work only with ndiswrapper using Windows XP drivers. 
Check out my answer on this thread: [http://wwww.ubuntuforums.org/showthread.php?p=9024193](http://wwww.ubuntuforums.org/showthread.php?p=9024193)

If you can still return that card and get your money back I really suggest you do. I'm having constant problems with the card, having my internet connection going up and down all the time.

A-Link USB stick WLAN works flawlessly on my other computer. Think I'll go and buy one more of those.

EDIT: Actually now that I spent more time looking for info I stumbled upon this thread: [http://ubuntuforums.org/archive/index.php/t-1321340.html](http://ubuntuforums.org/archive/index.php/t-1321340.html)
This link ([http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz](http://www.dirk-hoeschen.de/temp/rtl819Xe.tar.gz)) has the drivers that supposedly work and are installed by first extracting the files then going into the directory and executing the commands: "sudo su" and "./install.sh" and everything should work. 
I just did the procedure and going to reboot now to see if the card works with those drivers.

---

### Post by RedStar81 on 2010-05-11
I tried that but didn't work. Please reply if you have it working.

---

### Post by Mayfairy on 2010-05-12
Nope, not working.

Guess you have three options here:
1) Return the card and get your money back
2) Use some older (I think older thank Karmic) Ubuntu distro that still works with the card.
3) Use the ndiswrapper drivers.

---

