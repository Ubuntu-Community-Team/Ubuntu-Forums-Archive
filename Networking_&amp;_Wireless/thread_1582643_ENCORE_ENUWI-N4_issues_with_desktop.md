---
title: "ENCORE ENUWI-N4 issues with desktop"
date: 2010-09-26
forum: Networking &amp; Wireless
---

### Post by RedKlover on 2010-09-26
Hello Ubuntu forums,
 
I am new to the Ubuntu world and in need of some assistance. I have been  trying for a week now to get wireless working on my desktop with Ubuntu  on it. I have purchased this wireless adapter([http://www.newegg.com/Product/Produc...82E16833180066]("http://www.newegg.com/Product/Product.aspx?Item=N82E16833180066"))  which I am under the impression that there is no Linux driver for it. I  have been spending a lot of free time attempting every solution online  by using Ralink drivers, also RealTek drivers were suggested but have  not been able to try them out yet. My main issue is how to install the  drivers, because I do know about the Driver Manager, Software Upgrade,  and other options under Administrator. I have also tried using the  terminal and edit .dat files to make it suitable for the Ubuntu machine.  Through all my efforts I have failed to complete the task at hand. I do  have Windows XP Professional also installed on the machine, but I can  not "mount" ,I believe is the right word, the network to the Ubuntu for  some reason. If anyone could give me some assistance it would be very  helpful. thank you for your time.

---

### Post by RedKlover on 2010-09-27
can some one please help me with this or direct somewhere to get help? It is crucial I fix this.

---

### Post by RedKlover on 2010-09-28
bump

---

### Post by RedKlover on 2010-10-01
I'm assuming nobody on this entire website has any clue what could be causing this problem....

---

### Post by RedKlover on 2010-10-04
bump

---

### Post by techdude3177 on 2010-10-04
RedKlover there are a few things you can try. First I would recommend using Ndiswrapper which you can find the documentation for [here]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper") otherwise check out [madwifi.org/]("http://madwifi.org/")

Please post your results, I actually found your thread because I was trying to see if anyone else used this in linux because there was no native driver. Its a neat little usb wifi card that I would like to buy and useless to me if I cannot use it in linux.

Thanks!

**EDIT:** I did some more digging and I found this on the forum. [http://ubuntuforums.org/showthread.php?t=960642]("http://ubuntuforums.org/showthread.php?t=960642").  It may help installing the native linux drivers for ralink rt2870 that is used for the ENUWI-N4. Cheers!

---

### Post by RedKlover on 2010-10-11
Thank you very much for all of your help techdude3177 I have tried Ndiswrapper but when I try lsusb anymore it hangs up and freezes my terminal. I really hope this helps. Thanks again :)

---

### Post by Nougamuck on 2010-12-14
I got the Encore ENUWI-N4 to work in Ubuntu 10.10..  I believe I used the instructions from sbrbot on this post:  [http://ubuntuforums.org/archive/index.php/t-1534918.html](http://ubuntuforums.org/archive/index.php/t-1534918.html)

Now my only issue is that [COLOR=Red]I have to leave the USB adapter un-plugged until I actually start-up Ubuntu[/COLOR].. if I don't wait, it does nothing... not sure why.

If anyone has any tips for my issue above, please advise.. but I can live with it.

---

