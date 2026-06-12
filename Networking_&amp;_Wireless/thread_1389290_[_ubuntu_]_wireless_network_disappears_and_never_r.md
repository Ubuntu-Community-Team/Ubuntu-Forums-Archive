---
title: "[ ubuntu ] wireless network disappears and never return"
date: 2010-01-24
forum: Networking &amp; Wireless
---

### Post by yaoi1yuri on 2010-01-24
greetings everybody. i am a new ubuntu user. the wireless connection works very well when i start using. but once, after my sister took hold of my computer for a moment. the wireless don't seem to work anymore. i asked her what she did but she says nothing. she may ot may not be lying but that doesn't matters. what matters is i cant reinstall back the wireless network. 
 
when i first formatted my notebook to ubuntu 8.0, i followed an online instruction to enable wifi to work. it works perfectly well. so when the problems occured, i tried using the same instruction but it doesn't work anymore.
 
the wireless network does not appears under connection anymore. anyone can help?
 
thanks in advance.

---

### Post by byStanderone on 2010-01-24
...hi, would assume that you are now in 9.10, and wireless networking have some current issues in that version,...tho have read some threads bout this, would search on it once again, post the loc later for you.

---

### Post by byStanderone on 2010-01-25
...maybe u've read this thread already, all i got at the moment:
[http://ubuntuforums.org/showthread.php?t=1364883](http://ubuntuforums.org/showthread.php?t=1364883)

---

### Post by yaoi1yuri on 2010-02-20
hi, thanks for replying. i gone through the link the posted. i am still using the 8.1 ubunto. the following is an instruction i follow : 
[INDENT]**WLan**


**ath5k Method**


Wireless does not work out of the box but can be brought to life easily. The most simple way is to install ath5k, the new open source driver for Atheros chipsets. It got removed from the stock Intrepid kernel because it was not stable on some systems. I do not have any problems so my recommendation for the Aspire One is to use this driver. To activate ath5k, deactivate the proprietary driver "Atheros wireless card" (System -> Administration -> Hardware Drivers) that Ubuntu tries to use and install the package "linux-backports-modules-intrepid" 
sudo aptitude install linux-backports-modules-intrepidWireless will work after a reboot. 
 
[/INDENT]after typing that into terminals the following appears : 
 
[INDENT][FONT=Times New Roman][SIZE=3]Dpkg was interrupted. You must manually run ‘dpkg –configure –a’ to correct the problem.[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[/INDENT][FONT=Times New Roman][SIZE=3]can anyone tell me what does this mean? [/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]thanks lots[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT] 
[FONT=Times New Roman][SIZE=3][/SIZE][/FONT]

---

### Post by byStanderone on 2010-02-20
...it's ok to run sudo dpkg --configure -a (double dash before configure), the command is use to realigh the package source.

---

