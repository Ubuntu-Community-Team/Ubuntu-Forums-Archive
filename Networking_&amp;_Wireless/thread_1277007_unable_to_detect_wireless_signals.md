---
title: "unable to detect wireless signals"
date: 2009-09-27
forum: Networking &amp; Wireless
---

### Post by B_Luv on 2009-09-27
Halp! lol I just installed Ubuntu to my PC and when I went to connect to a wireless signal it said there was none. I use a usb network adapter and it works fine on vista. Do I need to re-install the adapter software to ubuntu? I checked the supported wireless cards and mine seems to be fine. what else could be wrong?

thanks guys!

---

### Post by bkratz on 2009-09-27
> **B_Luv said:**
> Halp! lol I just installed Ubuntu to my PC and when I went to connect to a wireless signal it said there was none. I use a usb network adapter and it works fine on vista. Do I need to re-install the adapter software to ubuntu? I checked the supported wireless cards and mine seems to be fine. what else could be wrong?

thanks guys!



You might want to post the output seen when you execute a lsusb in the terminal so all the people here can see what card you have and make suggestions.

---

### Post by B_Luv on 2009-09-27
How do I do that? haha I am not great with computer lingo =/

---

### Post by bkratz on 2009-09-27
> **B_Luv said:**
> How do I do that? haha I am not great with computer lingo =/


Well actually this will require the use of the terminal commands, which is found under appllications, accessories--termial.  This is really a big subject so I would suggest that you download the Ubutu Pocket Guide at this location

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

The terminal is well described here (much better than I could!).  I will find another link that really describes wireless troubleshooting well that I saw this morning (on another computer) and post it for you as soon as I find it again!

---

### Post by bkratz on 2009-09-27
> **bkratz said:**
> Well actually this will require the use of the terminal commands, which is found under appllications, accessories--termial.  This is really a big subject so I would suggest that you download the Ubutu Pocket Guide at this location

[http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

The terminal is well described here (much better than I could!).  I will find another link that really describes wireless troubleshooting well that I saw this morning (on another computer) and post it for you as soon as I find it again!



Here is a better description of terminal commands ( it is not the one I was looking for though---still looking)

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

---

### Post by cariboo on 2009-09-27
Open an Applications-->Accessories-->Terminal and type:

```
sudo lshw -C network > network.txt
```

The above command will create a text file with all the details of your network devices. Copy network.txt to your Windows partition and paste it into you next post.

---

### Post by B_Luv on 2009-09-27
i couldn't get network.txt =/

but i found this:

*-network DISABLED
description: Ethernet Interface
physical id: 1
logical name: pan0
serial: **:**:**:**:**:**
capabilities: Ethernet physical
configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A
multicast=yes



i have a feeling this helps in no way haha but i'll keep tryin thx for the help =)

---

