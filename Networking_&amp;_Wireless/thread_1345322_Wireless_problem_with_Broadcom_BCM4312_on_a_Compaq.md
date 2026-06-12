---
title: "Wireless problem with Broadcom BCM4312 on a Compaq Mini running 9.10"
date: 2009-12-03
forum: Networking &amp; Wireless
---

### Post by andrew4540 on 2009-12-03
[FONT=Arial][SIZE=1][COLOR=black]First off, I ap[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]**apologize i**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]f this has been posted before.  I've searched the forums for hours to no avail...  I just bought a Compaq mini (basically an HP mini) preloaded with XP.  I installed NBR as a dual-boot.  The install went fine, I just cant seem to get my wireless to work.  I [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]**don't k**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]now if its lack of knowledge on my part, or else a driver issue.  I'm leaning towards the latter, but at this point I really don't know.

I feel like I've tried all the solutions I can find, but still have nothing. 

First I downloaded a new driver from Broadc[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]**om's websi**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]te

[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)

Attempted to follow a guide to install that driver, was unsuccessful.

I believe that I did manage to uninstall my[/COLOR][/SIZE][/FONT][SIZE=1][COLOR=black] [/COLOR][/SIZE][FONT=Arial][SIZE=1][COLOR=black]**current **[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]driver however..

lshw -c networ[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]**k us**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]ed to list a "driver=*** " something, however, after a few rmmod's and bl[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]**acklist**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]s, of b43, and ssb I believe,[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]** driv**[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=1][COLOR=black]er= no longer shows up.

Any help would be appreciated.  I'd be willing to post whatever diagnostic command here would be helpful, just let me know.  Thanks![/COLOR][/SIZE][/FONT]

---

### Post by andrew4540 on 2009-12-03
The last think I tried was: sudo modprobe ieee80211_crypt_tkip

followed by sudo insmod wl.ko

but I get the error:

insmod: error inserting 'wl.ko': -1 unknown symbol in module

---

### Post by andrew4540 on 2009-12-04
Think I fixed my own problem guys...I needed to do 
modprobe lib80211 

instead of the modprobe command that I was doing...

---

