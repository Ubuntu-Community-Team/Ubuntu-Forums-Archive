---
title: "Atheros Wireless/Ubuntu 8.10/EEE 1000HA"
date: 2009-01-31
forum: Networking &amp; Wireless
---

### Post by sparks88 on 2009-01-31
I am currently running Ubuntu Intrepid Ibex on a Asus EEE 1000HA. I can't seem to get wireless working.

I've installed ath5k drivers, but still no luck.

$ lspci | grep Atheros
returns:
01:00.0 Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)

$ iwconfig
returns:
lo        no wireless extensions.
eth0      no wireless extensions.

My hardware drivers list shows "Support for 5xxx series of Atheros 802.11 wireless LAN cards."

So as far as I can understand it, the card is recognized, and the drivers are installed, but they still aren't talking to each other.

---

### Post by SqRt7744 on 2009-01-31
have you looked at wiki.eeeuser.com?
or forums.eeuser.com... I believe this is covered there.

but have you tried 
sudo modprobe ath5k ?
what does dmesg|tail tell you?

---

### Post by Reiger on 2009-01-31
It's the same card as the one I used to have, ath5k should work (you have an AR5007EG which requires ndiswrapper in 8.04 but no longer in 8.10).

This solved it for me: [http://ubuntuforums.org/showthread.php?t=958686](http://ubuntuforums.org/showthread.php?t=958686)
EDIT: Or was it compat wireless? [http://linuxwireless.org/en/users/Download](http://linuxwireless.org/en/users/Download)

---

### Post by 5BallJuggler on 2009-01-31
Its not the same net book, but it is using the same wireless controller, have a look at this "how to" for the AspireOne

I know you have the the ath5K installed, but is it being called?

[http://ubuntuforums.org/showthread.php?t=1054629](http://ubuntuforums.org/showthread.php?t=1054629)

---

### Post by sparks88 on 2009-01-31
"sudo modprobe ath5k" fixed it.

Thanks a lot for all the sugguestions, I plan to use them to figure out why that command fixed it. 	:biggrin:

---

### Post by iamkrazee on 2009-01-31
Don't forget to do 'kdesudo kate /etc/modules' ;)

---

