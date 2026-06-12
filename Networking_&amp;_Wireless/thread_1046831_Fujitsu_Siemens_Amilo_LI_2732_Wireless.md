---
title: "Fujitsu Siemens Amilo LI 2732 Wireless"
date: 2009-01-21
forum: Networking &amp; Wireless
---

### Post by Eriksson_82 on 2009-01-21
Hi!
My first post at this forum.
And to begin with, im sorry for posting this, i know there are a lot of threads about this, and i have tried "them all" 
but i just cant seem to get my wireless adapter to work.
I got it to work earlier(had to send my computer to service, whereafter I got a new harddrive, so i had to reinstall Ubuntu once again, and this time i just cant seem to get it to work.

Last time a friend helped me, but we couldnt get it to work then either, but what did the trick that time was this [http://ubuntuforums.org/archive/index.php/t-928127.html](http://ubuntuforums.org/archive/index.php/t-928127.html)

but when i try that...(and this [http://ubuntuforums.org/showthread.php?t=644899](http://ubuntuforums.org/showthread.php?t=644899))

to begin with... 
These lines doesnt work : wget [http://www.cakey.de/acerhk/archives/acerhk-0.5.35.tgz](http://www.cakey.de/acerhk/archives/acerhk-0.5.35.tgz)
wget [http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz](http://snapshots.madwifi.org/special/madwifi-ng-r2756+ar5007.tar.gz)

(it seems like the files isnt there anymore:( )...

And i get no result whatsoever, when i got it working before the service, my wlan"lamp" on the computer lit up each time i started ubuntu... but now, nothing happens...

Can anyone give me a tutorial from start to finnish?or anyone know what i might be doing wrong?.

:popcorn:
Thanks a lot for your help beforehand!

/Niklas E

---

### Post by mckooiker on 2009-11-13
I just installed ubuntu 9.10, and had a problem with that wireless card as well. Probably due to the fact that I was using a patch (from one of the links you posted).
I think this card is supported now, with the "problem" that the wireless card is not turned on automatically.

The wireless led turned on instantly after giving the command:

[COLOR="Red"]**sudo modprobe acer_wmi**[/COLOR]

in the terminal. Shortly after that the wireless networks came up.

([http://www.vleeuwen.net/2009/06/wireless-fix-on-amilo-running-ubuntu](http://www.vleeuwen.net/2009/06/wireless-fix-on-amilo-running-ubuntu))

---

