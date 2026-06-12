---
title: "Wireless Net Disappears"
date: 2010-03-03
forum: Networking &amp; Wireless
---

### Post by jcobban on 2010-03-03
Out of the blue a dialog popped up requesting that I enter the key for my home wireless network.  This is of course unexpected since the correct key is defined for that network in my network config.  I entered the correct key but it was rejected.

I then clicked on the network manager icon in the task bar.  Contrary to normal behavior this did not show either my home network or any of the other wireless networks from my neighbors.

The only resolution I could find to restore the wireless network was restarting my system.  This seems excessive.

Any thoughts or suggestions?

---

### Post by irisorn on 2010-03-03
Hi, you can use a reconnection script

#!/bin/bash

if eval "ping -c 1 ubuntuforums.org"; then
    exit
else 
/etc/init.d/network-manager restart
fi
    exit

 as shown in article:  
[http://www.thelastthule.com/index.php?option=com_content&view=article&id=19:gonho&catid=6:ubuntu&Itemid=2](http://www.thelastthule.com/index.php?option=com_content&view=article&id=19:gonho&catid=6:ubuntu&Itemid=2)
It can be used when you needed or it can be launched automatically.    

I hope it helps you.    

regards.

---

