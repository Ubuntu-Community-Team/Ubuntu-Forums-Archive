---
title: "Make laptop a wifi router and share internet from ethernet or a CDMA 3G USB dongle"
date: 2009-01-26
forum: Networking &amp; Wireless
---

### Post by anti_gravity99 on 2009-01-26
Hello: I am using a Dell D620 Latitude running Ubuntu 8.10 and want to be able to share its internet connection. Specifically I would like to share the internet connection that I am getting from my Sprint Sierra Compass USB dongle via wifi directly from my built-in wifi adapter (I don't want to share to my eth and connect a wifi router to my eth). Although, how to share to my Ethernet port will be nice info to have for possible future use or even how to share my eth via built in wifi.

I can easily connect to the internet via the Sprint Sierra Compass USB dongle using the network manager in Ubuntu 8.10. I have tried to do it with Firestarter but couldn't figure it out. I would like to get it to work using Firestarter because it is nice GUI but I can't do it with Firestarter then any help with an alternative would be appreciated.

I am doing this to be able to share my connection from the USB dongle while on the road with other laptop's and wifi devices like an iPod Touch.
(Which by the way let me know when someone can get the ARM port of Ubuntu from Mojo to install on an iPod Touch? I've seen the you tube video's of a Linux shell being installed on one via iBoot but nothing beyond that. Sorry for the side note.)

---

### Post by anti_gravity99 on 2009-01-26
Never mind. I found the answer to my question in this post: [http://ubuntuforums.org/showthread.php?t=1000942&highlight=share+internet+connection](http://ubuntuforums.org/showthread.php?t=1000942&highlight=share+internet+connection)

Extremely easy to do! Although I can't figure out how make access to the shared wifi password protected.

---

### Post by tusharmax on 2009-02-06
yuppie. working like a charm!!! for broadcom corporation 4312 802.11 a/b/g.

thanks mate!

---

### Post by life4himsq on 2009-06-18
I was able to use two wireless cards and share from one to the other. I enabled wep on the network I created and it only showed up after I reboot. I assume I could have sudo /etc/init.d/network restart or something but anyway. I have been using wvdail to get my usb sprint sierra modem to connect since I can't find a way to get Network Manager applet to use it. It seems if the applet is to share a connection it has to make the connection. anti_gravity99 how are you using the NM applet to connect the sprint modem? I don't see any way to use a modem in the applet. Thanks for adding the info you found.

---

### Post by life4himsq on 2009-06-18
Nevermind, I got it. I am using the sierra 598 and it is not recognized by hal as a modem. I found this post that fixes that. [http://ubuntuforums.org/showthread.php?t=1066979](http://ubuntuforums.org/showthread.php?t=1066979) after adding the 0x0025 then unplugging and re-plugging the modem, it came up in the network manager. Al is good... now I am bored. what else can I find to fix.... anti_gravity99 thanks again for posting the answer you found.

---

