---
title: "Cannot get my ENCORE ENLWI-N to work."
date: 2009-10-25
forum: Networking &amp; Wireless
---

### Post by Treeh on 2009-10-25
Hello,

I decided to test out Ubuntu, but I can't get my wireless card to work. Details about the card can be found here: [http://encore-usa.com/product_item.php?region=us&bid=2&pgid=2&pid=269](http://encore-usa.com/product_item.php?region=us&bid=2&pgid=2&pid=269)

Initially, the card detected the networks, but wouldn't connect to them, repeatedly showing the box to enter my WPA key in over and over.

There are Linux drivers for it, but I have no idea how to install them...and all the threads I could find on the forum recommended installing the drivers on a PC with Windows, and then using the tool "Windows Wireless Drivers" to install it for the Linux machine...which I tried..and failed at. I followed this post: [http://ubuntuforums.org/showpost.php?p=5655589&postcount=4](http://ubuntuforums.org/showpost.php?p=5655589&postcount=4)

When I installed it, the utility said it couldn't find the hardware present. 

Anyway, after I attempted to install the driver and restarted, Ubuntu no longer detected any wireless networks, even after I uninstalled the drivers...so now I'm worse off than before.

I found another thread that attempted to install the card using the official Linux drivers...but it seems much more complex, and if I can, I'd rather do it using the Windows Wireless Driver utility. Here's that thread: [http://ubuntuforums.org/showthread.php?t=1183801](http://ubuntuforums.org/showthread.php?t=1183801)

---

### Post by Treeh on 2009-10-25
Update: Apparently the RT2860 chipset doesn't play nice with WPA, so I just reverted to WEP until 9.1...which I hope will fix it.

---

### Post by carcar1 on 2009-10-28
Why does every one have this problem with the card?  I have this card and its been working fine since 9.04.  Works smashingly in 9.10 rc.  The devs need to get on this card, it is very picky when it wants to work.

---

