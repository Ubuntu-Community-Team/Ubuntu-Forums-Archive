---
title: "No wireless card after reboots."
date: 2013-04-20
forum: Networking &amp; Wireless
---

### Post by d5115r on 2013-04-20
I have looked high and low through these forums for the last few days and have found many similar threads with the same issue. I have tried all of the solutions contained therein but nothing has worked for me.

After installing and using Ubuntu 12.04 on my EEE PC 1000HE for about three months (and loving every minutes of it), my wireless card seems to have eaten itself after restarting the netbook. I have absolutely no clue what's going on and have given up. Can anyone help? As Ubuntu desktop loads up, I am presented a network notification saying I am "disconnected." As other posts here has suggested, I have thrown "sudo ifconfig wlan0 up" into the terminal and get the response: "wlan0: ERROR while getting interface flags: No such device." I have tried just about everything... The card works just fine in Windows.

---

### Post by marvselby on 2013-04-22
I'm gonna take a quick shot at this.  Is your wireless card a RALink?  If it is, try "sudo ifconfig ra0 up".  Also check to see if the driver module is being loaded by the kernel by using "lsmod".  Again, if it's a RALink, the module will be named something starting with "rt" and ending in "sta".  In my case, it's "rt3562sta".

There's more to this story so come back with the output of "lsmod" and maybe 'lspci" (That will tell what kind of card it is.)

---

