---
title: "Atheros AR5007EG Monitor Mode"
date: 2009-02-07
forum: Networking &amp; Wireless
---

### Post by notnam on 2009-02-07
I have searched the forums and can't find anything that helps with my problem. I followed the instructions here ([http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/](http://www.askstudent.com/hacking/how-to-crack-a-wep-key-using-ubuntu/)) until the driver patching part. I used this ([http://www.aircrack-ng.org/doku.php?id=madwifi-ng](http://www.aircrack-ng.org/doku.php?id=madwifi-ng)) for the drivers.

I can connect to wireless networks with no problem but when I try using ```
sudo airmon start ath0
```
it says> -e 
usage: /usr/sbin/airmon <start|stop> <interface> [channel]

-e Interface	Chipset		Driver

-e -n ath0		Atheros		madwifi
Error for wireless request "Set Mode" (8B06) :
    SET failed on device ath0 ; Invalid argument.
 (monitor mode enabled)

Can anybody link me to a tutorial that will help me with my problem? Did I patch the drivers wrong?

---

### Post by gimpchop on 2009-02-22
I had the same prob with mine. if you do the iwconfig command or ifconfig (not shure which one cos im a novice) it will give you a output of the wireless devices look to see the one that is live ie the one with a ip add if conected to the net.in my case it was wifi0 then do sudo airmon start wifi0 or what ever and it should be ok. Dont take it as 100% right cos ad i say im a novice.

---

