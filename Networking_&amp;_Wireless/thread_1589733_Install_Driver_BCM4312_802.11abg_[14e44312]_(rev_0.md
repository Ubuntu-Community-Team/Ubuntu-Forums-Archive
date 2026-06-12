---
title: "Install Driver BCM4312 802.11a/b/g [14e4:4312] (rev 02)"
date: 2010-10-06
forum: Networking &amp; Wireless
---

### Post by maxcomx on 2010-10-06
This is how to install b43 driver on HP Pavilion dv6645ca or any other BCM4312(rev 02) PCI.  With working packet injection.

I'm using Backtrack4 running either ubuntu or kubuntu kernel 2.6.30.9

For any other BCM43xx, b43 and b43legacy [Click here]("http://linuxwireless.org/en/users/Drivers/b43")

broadcom-sta driver do not work becarefull to auto update or even when you update to not install this package. if you have it install remove it.


Make sure of the PCI devices you got.
Command:
> 
lspci -vnn | grep 14e4


In my case 
> Linux bt 2.6.30.9 #1 SMP Tue Dec 1 21:51:08 EST 2009 i686 GNU/Linux
03:00.0 Network controller [0280]: Broadcom Corporation BCM4312 802.11a/b/g [14e4:4312] (rev 02)


so:
[B]Kernel 2.6.30.9
BCM4312 (rev 02)[/B]


In recent versions of Ubuntu and Debian, installing the b43-fwcutter package will handle everything for you: 
> sudo apt-get install b43-fwcutter


You will be asked to automatically fetch and install the firmware into the right location. Answer Yes in that Blue screen.

Done !


If you wanna test packet injection:[http://www.aircrack-ng.org/doku.php?id=injection_test]("http://www.aircrack-ng.org/doku.php?id=injection_test")

---

