---
title: "set tx-power failed"
date: 2012-03-06
forum: Networking &amp; Wireless
---

### Post by warthogdude on 2012-03-06
First off i am using Backtrack 5 (gnome). I have my wireless working thanks to compat-wireless.
I purchased the ALFA wifi 1000mW device (chipset RTL8187) and it works. However a quick run of iwconfig wlan1 for the device results in  Tx-Power=0 dBm.

After some time with the man pages I have tried the following to set the device to anything but 0. The goal being to set the thing to 1000mW and use it at its full potential.

iw dev wlan1 set txpower fixed 30
command failed: Operation not supported (-95)
or
iw dev wlan1 set txpower 30
Invalid parameter: 30

iwconfig wlan1 txpower 30
or
iwconfig wlan1 txpower 30dBm
Error for wireless request "Set Tx Power" (8B26) :
           SET failed on device wlan1 ; Invalid argument.

This fails for every number I input except 0, which it has no problem with.
I have taken down the device and set the register to BO with the following in order th change my region so that it will accept a higher value.

ifconfig wlan1 down
iw reg set BO

Is there any more information that i can provide to help me get this figured out? and the commands would be useful since i am still fairly "green/noob" with ubuntu.

At this point i would like to be able to manipulate the txpower at all then mess with what setting works best for stability in the future.

Thank you for your time.

---

### Post by takka360 on 2012-04-16
Hi what i done just by chance was got a BO proxy from [http://www.hidemyass.com/proxy-list/](http://www.hidemyass.com/proxy-list/)  i then disconnected from wicd then reconnect with the new proxy
put in the command iw reg set BO then wiconfig  wlan1 txpower 30 BINGO.
You can then come off line again fire up mon0 and away you go tx power 30
Each time you log on log on with the BO proxy then you can change back to
your own ip and still have tx pwer 30 until you log off.
Give it a shot.it works

---

### Post by Tesla01 on 2012-04-17
Where exactly did you put in the proxy?
I have the same problem, also tried to change the regulatory.bin an recompile CRDA followed this article [http://hacking-library.com/forum/viewtopic.php?f=36&t=284&start=0&sid=92e29f05abfa08ca43668cb67fc3c0e8](http://hacking-library.com/forum/viewtopic.php?f=36&t=284&start=0&sid=92e29f05abfa08ca43668cb67fc3c0e8) or this [http://deckardt.nl/blog/2011/01/20/regulatory-limitations-in-linux-wireless/](http://deckardt.nl/blog/2011/01/20/regulatory-limitations-in-linux-wireless/)
But without success.
So if the idea with te proxy works, the IP must be in the CRDA Configs somewhere?

---

### Post by takka360 on 2012-04-17
Hi just go to firefox Edit preferences, Advanced. network ,settings manual proxy
and put it in there also the port number

---

