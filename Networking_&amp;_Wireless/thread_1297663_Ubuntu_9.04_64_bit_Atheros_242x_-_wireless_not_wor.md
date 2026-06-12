---
title: "Ubuntu 9.04 64 bit Atheros 242x - wireless not working"
date: 2009-10-22
forum: Networking &amp; Wireless
---

### Post by gdbutcher on 2009-10-22
Hi I've re-installed Ubuntu 9.04 64 (after a brief stint on 9.10) my wireless previously worked straight from install but not anymore!? 

I've done a lot of searching but not found a solution can anyone help?

This is what I've tried so far:

1. Activated alternate "madwifi"  Atheros driver from Hardware Drivers

2. De-activated this, then installed linux-backports-jaunty (worked previously for me on 8.10 but not now)

3. Added these to /etc/modprobe.d/blacklist.conf 
blacklist ath_hal
blacklist ath_pci

4. removed network-manager then installed wicd

Is there anything else I can try? Its so frustrating becuase it worked perfectly before without me having to do anything! ](*,)

Any help would be really appreciated, thanks

---

### Post by Cuba71 on 2009-10-22
You should try booting up with the Live CD, it should work out of the box using the ath5k native driver

---

### Post by gdbutcher on 2009-10-22
Thanks for your help, I've not really solved the problem in 9.04, I cheated and upgraded to 9.10 and its now working.:lol:

---

### Post by drpjkurian on 2009-10-25
Hi
Please visit my thread
[http://ubuntuforums.org/showthread.php?t=1240781](http://ubuntuforums.org/showthread.php?t=1240781)
It might help you

With
Regards
Dr Kurian

---

