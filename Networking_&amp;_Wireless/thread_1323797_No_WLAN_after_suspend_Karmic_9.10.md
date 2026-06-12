---
title: "No WLAN after suspend Karmic 9.10"
date: 2009-11-12
forum: Networking &amp; Wireless
---

### Post by duxi on 2009-11-12
hey guys

karmic's working fine for me and is running very stable!
BUT I don't get any network after suspend. So if i click on the network manager icon it says (under wireless LAN) "device is not ready" (Gerät nicht betriebsbereit).

I tried to killall NetworkManager and restart it and even ifconfig wlan0 down and up.

when i type wlan0 up, it says SIOCSIFFLAGS: Connection timed out

so i have to restart my laptop...kernel updates didn't make any difference. backports are activated.

i have the daily trunk of NM activated and it works just fine. 

WLAN0 just does not come up after suspend.

do you have any suggestions what to do?

thanks in advance

best regards

christoher

---

### Post by undertakingyou on 2009-11-12
I am having the same issue. I am using wicd to manage wireless however. I find that if I 'sudo rmmod' the appropriate wireless module, 'sudo modprobe' the wireless module and then I stop the wicd daemon, kill the wicd-client, and then start the wicd daemon I can use the wireless again.

Still, even with that workaround it is a pain in the butt.

---

### Post by graden on 2009-11-29
I had the same problem. [http://ubuntuforums.org/showthread.php?t=1017306#4](http://ubuntuforums.org/showthread.php?t=1017306#4) provided a solution which seems to work so far. :-)

---

### Post by Pollox on 2009-12-09
I'm also having this problem. "Undertakingyou"'s workaround worked for me, and will solve the problem for now while I'm waiting for this to get fixed.  If anyone else is attempting this solution, just make a bash script (i.e. a text file called fixwireless.sh, and make it executable) with:
killall nm-applet
gksudo rmmod iwl3945
gksudo modprobe iwl3945
nm-applet

but replace iwl3945 with whatever your wireless module is.  I used hardinfo to find out my wireless module, but I'm sure there's a terminal command to find that info?  Then you can just double click the script and type your password whenever your wireless stops working.

Edit: By the way, thanks "Undertakingyou".  This saves me a lot of hassle compared to restarting my computer and then reopening all the stuff I had open.

---

