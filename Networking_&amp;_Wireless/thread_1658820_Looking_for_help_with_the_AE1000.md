---
title: "Looking for help with the AE1000"
date: 2011-01-03
forum: Networking &amp; Wireless
---

### Post by RyanMcD86 on 2011-01-03
i previously posted here

 [http://ubuntuforums.org/showthread.php?t=1654943](http://ubuntuforums.org/showthread.php?t=1654943)

i fixed the problem some how. but i reinstalled my computer and now i went to install the driver again. i followed the steps on this thread posted by "dummptyhummpty" here.. [http://ubuntuforums.org/showthread.php?t=1455649](http://ubuntuforums.org/showthread.php?t=1455649)

i think i originally downloaded the file that is missing. Anyways. this is what the terminal is telling me. 

"ryan@ryan-Unknow:~/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1$ sudo make install
make -C /home/ryan/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux -f Makefile.6 install
mkdir: cannot create directory `/etc/Wireless': File exists
make[1]: Entering directory `/home/ryan/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
rm -rf /etc/Wireless/RT2870STA
mkdir /etc/Wireless/RT2870STA
cp /home/ryan/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/RT2870STA.dat /etc/Wireless/RT2870STA/.
install -d /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install -m 644 -c rt2870sta.ko /lib/modules/2.6.35-24-generic/kernel/drivers/net/wireless/
install: cannot stat `rt2870sta.ko': No such file or directory
make[1]: *** [install] Error 1
make[1]: Leaving directory `/home/ryan/Downloads/2010_0709_RT2870_Linux_STA_v2.4.0.1/os/linux'
make: *** [install] Error 2"

Any clue on how i can locate this file?:confused:

---

### Post by chili555 on 2011-01-03
If rt3572sta is the correct driver for your device as mentioned in your previous post (and I believe it is correct), why are you trying to compile rt2870sta?

---

### Post by RyanMcD86 on 2011-01-03
Well you made a good point. i went back and used the other driver installation file. and sure enough that was the one that had the file for me to download. however. now that I've gone though that process, i can see the network, i connected to it once, but the light on my network adapter is not light like the last time.. I also cant seem to get it working anymore than that one time i connected. any clue on what i'm doing wrong?

---

### Post by chili555 on 2011-01-03
Let's see what the kernel says:```
dmesg | grep -e rt2 -e rt3
lsmod | grep -e rt2 -e rt3
```Thanks.

---

### Post by RyanMcD86 on 2011-01-04
:confused:

"ryan@ryan-Unknow:~$ dmesg | grep -e rt2 -e rt3
[   13.347732] rtusb init rt2870 --->
[   13.386763] usbcore: registered new interface driver rt2870
[   26.288460] <==== rt28xx_init, Status=0
[   38.370030] <==== rt28xx_init, Status=0
[   81.647100] <==== rt28xx_init, Status=0
ryan@ryan-Unknow:~$ lsmod | grep -e rt2 -e rt3
rt3572sta             644556  1 
"

---

### Post by chili555 on 2011-01-04
I have a rt3572sta device and the light doesn't light either, but it connects and operates normally. Your readings look pretty healthy, actually.

Either your driver, Network Manager or wpa_supplicant have problems in two areas. I don't know which. First, it can be troublesome to connect to SSIDs with a space, such as "Chili House." If yours has a space, try changing to something else, such as, "ChiliHouse."

Second, many routers have a mixed WPA and WPA2 mode. The intent, I believe, is to be backwards compatible with older hardware that may not be WPA2 capable. If yours is so configured, you will have better luck with WPA ***or*** WPA2; not both.

Finally, have you double-checked the password? Does it work seamlessly in other computers on the network?

---

### Post by RyanMcD86 on 2011-01-04
Yep. However, it does work. i just have to re-connect a few times before it detects it. What i'm really confused about is what i did to get the light to light up the first time. Maybe it was just randomly working. Although it's working better now that the light isn't lit. Like the connection is stronger. Anyway. thanks for all your help. One last question, not sure how to change the "space". I'm kinda new to all this. Thanks for your help by the way.

---

### Post by chili555 on 2011-01-04
> not sure how to change the "space".Log in to your router's configuration pages and see where it names the ESSID or network name. Change it to something without a space. Here is a slightly obscured sample from my router. Notice also that my router is set to WPA2 only, not mixed WPA and WPA2.

---

### Post by RyanMcD86 on 2011-01-05
well... Everything seems okay. i think i might return this wireless adapter and get one that works better with Ubuntu. Anyways. thanks for all your help. and sorry if it took up too much of your time.

---

